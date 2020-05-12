---
title: python script 00update check (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '00update check'

Functions in program: 
* `def main():`

Modules used in program: 
* `import logging`
* `import random`
* `import asyncio`
* `import typing as t`
* `import sys`

## python 00update check

Python mysql example: 00update check

```python
import sys
import typing as t
import asyncio
import random
import logging
from handofcats import as_command

logger = logging.getLogger(__name__)


async def update_check() -> t.Awaitable[t.Optional[str]]:
    logger.info("-> update_check ...")
    await asyncio.sleep(0.5)
    logger.info("<- ... update_check")

    if random.random() < 0.2:
        # update is not found
        return None

    # update is found
    return "0.8.8"


@as_command
def main():
    async def run():
        fut = asyncio.ensure_future(update_check())

        logger.info("do something (main)")
        for i in range(6):
            logger.info(".")
            sys.stdout.flush()
            await asyncio.sleep(0.1)
        logger.info("ok")

        update_version = await fut
        if update_version is not None:
            logger.info(f"A new release of gh is available: xxx → {update_version}")

    asyncio.run(run())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
