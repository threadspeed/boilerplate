---
title: python script deploy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'deploy'


## python deploy

Python example: deploy

```python
{% set URL = 'https://drive.google.com/drive/u/0/notareallink' %}
{% from random import random %}
{% set URL1 = 'https://alien-labs.slack.com/archives/development/p1460591822000489#{}'.format(random()) %}
{% set URL2 = 'https://alien-labs.slack.com/archives/sandbox/p1460675353000161#{}'.format(random()) %}

{% if message_number == 0 %}

{% elif message_number == 1 %}

	:bulb: I have two answers to this question. To edit them <{{URL}}|go to your dashboard.>

{% elif message_number == 2 %}
	<{{URL1}}| >
  	
{% elif message_number == 3 %}
	<{{URL2}}| >

{% else %}

  {{ reset() }}
  {% include base %}

{% end %}

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
