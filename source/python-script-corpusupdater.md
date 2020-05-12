---
title: python script corpusupdater (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'corpusupdater'

Functions in program: 
* `def update_corpus(sc, channel):`
* `def format_message(original):`
* `def build_text_model():`
* `def _add_messages(message_db, new_messages):`
* `def _query_messages(client, page=1):`
* `def _store_db(obj):`
* `def _load_db():`
* `def check_n_update(msg):`

Modules used in program: 
* `import random`
* `import os`
* `import numpy as np`
* `import yaml`
* `import random`
* `import datetime`
* `import time`
* `import re`
* `import json`

## python corpusupdater

Python mysql example: corpusupdater

```python
# -*- coding: utf-8 -*-
from chatterbot import ChatBot
import json
import re
import time

import datetime
#from apscheduler.schedulers.blocking import BlockingScheduler

from slackclient import SlackClient

import random
import yaml
import numpy as np
from yahoo_finance import Share

from flask import Flask
from flask import request
from flask import jsonify
from flask import render_template
import os
import random


from slackclient import SlackClient
BOT_TOKEN = "xoxb-115838670327-KU1njeFWz4ivi65mzWZn9rtF"
GROUP_TOKEN = "xoxp-73866548933-114910066931-115825496294-e2291c4f5133dad8b2d89089a71e45ea"
MESSAGE_PAGE_SIZE = 100
DEBUG = True
MESSAGE_QUERY = "after:yesterday"

def check_n_update(msg):
    try:
        msg = msg.strip()
        if msg[-1] not in ('.','?','!'):
            msg += '. \n'
        else :
            msg += ' \n'
    except :
        pass
    return msg


def _load_db():
    """
    Reads 'database' from a JSON file on disk.
    Returns a dictionary keyed by unique message permalinks.
    """

    try:
        with open('message_db.json', 'r') as json_file:
            messages = json.loads(json_file.read())
    except IOError:
        with open('message_db.json', 'w') as json_file:
            json_file.write('{}')
        messages = {}

    return messages

def _store_db(obj):
    """
    Takes a dictionary keyed by unique message permalinks and writes it to the JSON 'database' on
    disk.
    """

    with open('message_db.json', 'w') as json_file:
        json_file.write(json.dumps(obj))
    print(obj)
    new_obj = {}
    for key,items in obj.iteritems():
        new_obj[items] = key

    with open('old_db.json', 'w') as json_file:
        json_file.write(json.dumps(new_obj))
    print("DONE")
    return True

def _query_messages(client, page=1):
    """
    Convenience method for querying messages from Slack API.
    """
    if DEBUG:
        print("requesting page {}".format(page))

    return client.api_call('search.messages', query=MESSAGE_QUERY, count=MESSAGE_PAGE_SIZE, page=page)

def _add_messages(message_db, new_messages):
    """
    Search through an API response and add all messages to the 'database' dictionary.
    Returns updated dictionary.
    """
    for match in new_messages['messages']['matches']:
        trimmed_msg = check_n_update(match['text'])
        message_db[match['permalink']] = trimmed_msg

    return message_db


# get all messages, build a giant text corpus
def build_text_model():
    """
    Read the latest 'database' off disk and build a new markov chain generator model.
    Returns TextModel.
    """
    if DEBUG:
        print("Building new model...")

    messages = _load_db()
    return markovify.Text(" ".join(messages.values()), state_size=2)


def format_message(original):
    """
    Do any formatting necessary to markon chains before relaying to Slack.
    """
    if original is None:
        return

    # Clear <> from urls
    cleaned_message = re.sub(r'<(htt.*)>', '\1', original)

    return cleaned_message


def update_corpus(sc, channel):
    """
    Queries for new messages and adds them to the 'database' object if new ones are found.
    Reports back to the channel where the update was requested on status.
    """

    sc.rtm_send_message(channel, "Leveling up...")

    # Messages will get queried by a different auth token
    # So we'll temporarily instantiate a new client with that token
    group_sc = SlackClient(GROUP_TOKEN)

    # Load the current database
    messages_db = {} #_load_db()
    starting_count = len(messages_db.keys())

    # Get first page of messages
    new_messages = _query_messages(group_sc)
    total_pages = new_messages['messages']['paging']['pages']

    # store new messages
    messages_db = _add_messages(messages_db, new_messages)

    # If any subsequent pages are present, get those too
    if total_pages > 1:
        for page in range(2, total_pages + 1):
            new_messages = _query_messages(group_sc, page=page)
            messages_db = _add_messages(messages_db, new_messages)

    # See if any new keys were added
    final_count = len(messages_db.keys())
    new_message_count = final_count - starting_count

    # If the count went up, save the new 'database' to disk, report the stats.
    if final_count > starting_count:
        # Write to disk since there is new data.
        _store_db(messages_db)
        sc.rtm_send_message(channel, "I have been imbued with the power of {} new messages!".format(
            new_message_count
        ))
    else:
        sc.rtm_send_message(channel, "No new messages found :(")

    if DEBUG:
        print("Start: {}".format(starting_count), "Final: {}".format(final_count),
              "New: {}".format(new_message_count))

    # Make sure we close any sockets to the other group.
    del group_sc

    return new_message_count


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
