---
title: python script retry decorator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'retry decorator'

Functions in program: 
* `def test_multiple_exceptions():`
* `def test_random(text):`
* `def test_success(text):`
* `def test_fail(text):`
* `def retry(ExceptionToCheck, tries=4, delay=3, backoff=2, logger=None):`

Modules used in program: 
* `import unittest`
* `import logging`
* `import random`
* `import random`
* `import time`

## python retry decorator

Python mysql example: retry decorator

```python
import time
from functools import wraps


def retry(ExceptionToCheck, tries=4, delay=3, backoff=2, logger=None):
    """Retry calling the decorated function using an exponential backoff.

    http://www.saltycrane.com/blog/2009/11/trying-out-retry-decorator-python/
    original from: http://wiki.python.org/moin/PythonDecoratorLibrary#Retry

    :param ExceptionToCheck: the exception to check. may be a tuple of
        exceptions to check
    :type ExceptionToCheck: Exception or tuple
    :param tries: number of times to try (not retry) before giving up
    :type tries: int
    :param delay: initial delay between retries in seconds
    :type delay: int
    :param backoff: backoff multiplier e.g. value of 2 will double the delay
        each retry
    :type backoff: int
    :param logger: logger to use. If None, print
    :type logger: logging.Logger instance
    """
    def deco_retry(f):

        @wraps(f)
        def f_retry(*args, **kwargs):
            mtries, mdelay = tries, delay
            while mtries > 1:
                try:
                    return f(*args, **kwargs)
                except ExceptionToCheck, e:
                    msg = "%s, Retrying in %d seconds..." % (str(e), mdelay)
                    if logger:
                        logger.warning(msg)
                    else:
                        print(msg)
                    time.sleep(mdelay)
                    mtries -= 1
                    mdelay *= backoff
            return f(*args, **kwargs)

        return f_retry  # true decorator

    return deco_retry

# USE CASES

# 1 ALWAYS FAIL CASE
@retry(Exception, tries=4)
def test_fail(text):
    raise Exception("Fail")

test_fail("it works!")


# 2 ALWAYS SUCCESS CASE
@retry(Exception, tries=4)
def test_success(text):
    print("Success: ", text)

test_success("it works!")

# 3 RANDOM FAIL CASE
import random

@retry(Exception, tries=4)
def test_random(text):
    x = random.random()
    if x < 0.5:
        raise Exception("Fail")
    else:
        print("Success: ", text)

test_random("it works!")

# 4 MULTPIPLE EXCEPTIONS CASE
import random

@retry((NameError, IOError), tries=20, delay=1, backoff=1)
def test_multiple_exceptions():
    x = random.random()
    if x < 0.40:
        raise NameError("NameError")
    elif x < 0.80:
        raise IOError("IOError")
    else:
        raise KeyError("KeyError")

test_multiple_exceptions()

####################
# UNIT TESTS

import logging
import unittest

from decorators import retry


class RetryableError(Exception):
    pass


class AnotherRetryableError(Exception):
    pass


class UnexpectedError(Exception):
    pass


class RetryTestCase(unittest.TestCase):

    def test_no_retry_required(self):
        self.counter = 0

        @retry(RetryableError, tries=4, delay=0.1)
        def succeeds():
            self.counter += 1
            return 'success'

        r = succeeds()

        self.assertEqual(r, 'success')
        self.assertEqual(self.counter, 1)

    def test_retries_once(self):
        self.counter = 0

        @retry(RetryableError, tries=4, delay=0.1)
        def fails_once():
            self.counter += 1
            if self.counter < 2:
                raise RetryableError('failed')
            else:
                return 'success'

        r = fails_once()
        self.assertEqual(r, 'success')
        self.assertEqual(self.counter, 2)

    def test_limit_is_reached(self):
        self.counter = 0

        @retry(RetryableError, tries=4, delay=0.1)
        def always_fails():
            self.counter += 1
            raise RetryableError('failed')

        with self.assertRaises(RetryableError):
            always_fails()
        self.assertEqual(self.counter, 4)

    def test_multiple_exception_types(self):
        self.counter = 0

        @retry((RetryableError, AnotherRetryableError), tries=4, delay=0.1)
        def raise_multiple_exceptions():
            self.counter += 1
            if self.counter == 1:
                raise RetryableError('a retryable error')
            elif self.counter == 2:
                raise AnotherRetryableError('another retryable error')
            else:
                return 'success'

        r = raise_multiple_exceptions()
        self.assertEqual(r, 'success')
        self.assertEqual(self.counter, 3)

    def test_unexpected_exception_does_not_retry(self):

        @retry(RetryableError, tries=4, delay=0.1)
        def raise_unexpected_error():
            raise UnexpectedError('unexpected error')

        with self.assertRaises(UnexpectedError):
            raise_unexpected_error()

    def test_using_a_logger(self):
        self.counter = 0

        sh = logging.StreamHandler()
        logger = logging.getLogger(__name__)
        logger.addHandler(sh)

        @retry(RetryableError, tries=4, delay=0.1, logger=logger)
        def fails_once():
            self.counter += 1
            if self.counter < 2:
                raise RetryableError('failed')
            else:
                return 'success'

        fails_once()


if __name__ == '__main__':
    unittest.main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
