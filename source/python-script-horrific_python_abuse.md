---
title: python script horrific python abuse (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'horrific python abuse'

Functions in program: 
* `def horrific_abuse_of_python(the_expr, **kwargs):`

## python horrific python abuse

Python mysql example: horrific python abuse

```python
#!/bin/env python

# a joke exercise in Slack the other day where a simple python question became a 
# round of joke code where we riffed on 'enterprise quality' but very bad code.
# my submission included a TODO to fix a horrible security hole along with a fake Jira ticket #

def horrific_abuse_of_python(the_expr, **kwargs):
    """Return the result of evaluating expression with supplied arguments.

    Args:
        the_expr (str): The expression
        **kwargs: Arbitrary keyword arguments

    Returns:
        The result of the expression

    >>> horrific_abuse_of_python("a + b + c", a = 1, b = 2, c = 3)
    6
    >>> # kwargs can be supplied in a dict:
    >>> horrific_abuse_of_python("a + b + c", **{'a': 1, 'b': 2, 'c': 3})
    6
    >>> # change the expression, you get different result
    >>> horrific_abuse_of_python("a + b ** c", a = 1, b = 2, c = 3)
    9
    >>> # lists can be concatenated too
    >>> horrific_abuse_of_python("a + b + c", a = ['a'], b = ['b1','b2'], c = ['c1', 'c2', 'c3'])
    ['a', 'b1', 'b2', 'c1', 'c2', 'c3']

    >>> # anything that's an expression works, so do some trickery to import
    >>> # importing random in next expr, set seed for doctests
    >>> import random
    >>> random.seed(1)
    >>> horrific_abuse_of_python("[__import__('random').randrange(b) for i in range(a)]", **{'a': 3, 'b': 100})
    [17, 72, 97]

    # TODO: Jira ticket FML-204 prevent horrific abuse ala "__import__('os').system('RM -RF /I_HOPE_THIS_DIRECTORY_DOESNT_EXIST')"
    """
    return eval(the_expr, kwargs)


if __name__ == "__main__":
    import doctest
    doctest.testmod()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
