---
title: python script as completed with max concurrent (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'as completed with max concurrent'

Functions in program: 
* `def as_completed_with_max_concurrent(futures, max_concurrent, loop=None, timeout=None):`

Modules used in program: 
* `import itertools`
* `import asyncio`

## python as completed with max concurrent

Python mysql example: as completed with max concurrent

```python
import asyncio
import itertools


def as_completed_with_max_concurrent(futures, max_concurrent, loop=None, timeout=None):
    """Tweaked version of `asyncio.as_completed` with the addition of the `max_concurrent` param.

    The main change is to only queue (`_queue_future`) the first `max_concurrent` futures initially.
    The rest will be queued in `_on_completion`.
    """
    if isinstance(futures, asyncio.futures.Future) or asyncio.coroutines.iscoroutine(futures):
        raise TypeError("expect a list of futures, not %s" % type(futures).__name__)
    loop = loop if loop is not None else asyncio.events.get_event_loop()
    todo = set()
    done = asyncio.Queue(loop=loop)
    timeout_handle = None

    def _on_timeout():
        for f in todo:
            f.remove_done_callback(_on_completion)
            done.put_nowait(None)  # Queue a dummy value for _wait_for_one().
        todo.clear()  # Can't do todo.remove(f) in the loop.

    def _on_completion(f):
        if not todo:
            return  # _on_timeout() was here first.
        todo.remove(f)
        try:
            future_to_queue = next(futures_to_queue_iter)
            _queue_future(future_to_queue)
        except StopIteration:
            # Finished adding futures to todo
            pass
        done.put_nowait(f)
        if not todo and timeout_handle is not None:
            timeout_handle.cancel()

    def _queue_future(f):
        wrapped = asyncio.ensure_future(f, loop=loop)
        wrapped.add_done_callback(_on_completion)
        todo.add(wrapped)

    @asyncio.coroutine
    def _wait_for_one():
        f = yield from done.get()
        if f is None:
            # Dummy value from _on_timeout().
            raise asyncio.futures.TimeoutError
        return f.result()  # May raise f.exception().

    # Only queue the first `max_concurrent` futures initially.
    # The rest will be queued in `_on_completion`.
    futures_set = set(futures)
    futures_to_queue_iter = futures_set.__iter__()
    for future in itertools.islice(futures_to_queue_iter, 0, max_concurrent):
        _queue_future(future)

    if todo and timeout is not None:
        timeout_handle = loop.call_later(timeout, _on_timeout)

    for _ in range(len(futures_set)):
        yield _wait_for_one()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
