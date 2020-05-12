---
title: python script server ping (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'server ping'


Modules used in program: 
* `import random `

## python server ping

Python example: server ping

```python
# UDPPingerServer.py 
# We will need the following module to generate randomized lost packets import random 
from socket import * 
# Create a UDP socket 
# Notice the use of SOCK_DGRAM for UDP packets 
import random 

serverSocket = socket(AF_INET, SOCK_DGRAM) # Assign IP address and port number to socket 
serverSocket.bind(('', 12000)) 
  
while True: 
  # Generate random number in the range of 0 to 10 
  rand = random.randint(0, 10) 
  # Receive the client packet along with the address it is coming from 
  message, address = serverSocket.recvfrom(1024) 
  # Capitalize the message from the client 
  message = message.upper()
  # If rand is less is than 4, we consider the packet lost and do not respond 
  if rand < 4: 
    continue 
    # Otherwise, the server responds 
  serverSocket.sendto(message, address) 


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
