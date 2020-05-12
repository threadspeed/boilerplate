---
title: python script link (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'link'


## python link

Python example: link

```python
{% set URL = 'https://drive.google.com/drive/u/0/notareallink' %}
{% set URL3 = 'https://alien-labs.slack.com/archives/development/p1458083054000134' %}
{% from random import random %}
{% set URL4 = 'https://alien-labs.slack.com/archives/development/p1458083054000134#{}'.format(random()) %}

{% if message_number == 0 %}

{% elif message_number == 1 %}

  :eyes: I've seen this question before <{{URL3}}|here>. To add an answer <{{URL}}|go to your dashboard.>

{% elif message_number == 2 %}

  <{{URL4}}| >

{% end %}

{{ reset()  }}

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
