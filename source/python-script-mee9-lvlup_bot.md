---
title: python script mee9-lvlup bot (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mee9-lvlup bot'

Functions in program: 
* `def random_phrase(length):`

Modules used in program: 
* `import asyncio`
* `import string`
* `import random`
* `import discord`

## python mee9-lvlup bot

Python example: mee9-lvlup bot

```python
import discord
import random
import string
import asyncio

client = discord.Client()


def random_phrase(length):
    return ''.join(random.choice(string.ascii_uppercase) for i in range(length))

rndOut = random_phrase(5) + "-" + random_phrase(5) + "-" + random_phrase(5) + "-" + random_phrase(5)


# inEmail = input("email: ")
# inPassword = input("password: ")


@client.event
async def on_ready():
    print("Find out how much messages you need to send to reach wanted lvl on mee6calc.xyz")
    msg_to_send = int(input("How how much messages you need to send: "))
    while msg_to_send > 0:
        msg_to_send -= 1
        await client.send_message(client.get_channel('274597252880662528'), rndOut)
        await asyncio.sleep(50)
    return

client.run('lox1337@binka.me', 'qwerty1337')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
