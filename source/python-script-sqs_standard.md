---
title: python script sqs standard (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sqs standard'


Modules used in program: 
* `import random`
* `import boto3`

## python sqs standard

Python mysql example: sqs standard

```python
import boto3
import random

# This is for demo purpose, do not store your credentials in the code
AWS_ACCESS_KEY = 'yourAccessKey'
AWS_SECRET_ACCESS_KEY = 'yourSecretAccessKey'
sqs_client = boto3.resource(
    'sqs',
    aws_access_key_id=AWS_ACCESS_KEY,
    aws_secret_access_key=AWS_SECRET_ACCESS_KEY,
    region_name='us-east-1' # use any regions
)

queue_name = 'demo_queue'

response = sqs_client.create_queue(
    QueueName=queue_name
)

queue = sqs_client.get_queue_by_name(QueueName=queue_name)

# generate some sample numbers
samples = random.sample(range(1, 999999), 500)

# send the numbers to the queue
for i in samples:
    queue.send_message(
        MessageBody=str(i),
        MessageGroupId='my_message_group_id'
    )

received_messages = []

# consume the numbers
messages = queue.receive_messages()
while len(messages)>0:
    for message in messages:
        received_messages.append(int(message.body))
        message.delete()
    messages = queue.receive_messages()

# Check that the sent and consumed numbers are the same (also same order!)
print(samples == fetched) # This will print(False (the messages are not returned in the same order))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
