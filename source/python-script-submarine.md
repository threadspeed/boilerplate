---
title: python script submarine (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'submarine'

Functions in program: 
* `def main():`
* `def login(user, password):`
* `def validate_credentials(user, password):`
* `def validate_token(ciphertext):`

## python submarine

Python example: submarine

```python
#!/usr/bin/python
from aes_cbc_cipher import AES_CBC_Cipher
from Crypto import Random

secret_key = "abcdefghijklmnop" # not the real one =)

def validate_token(ciphertext):
    cipher = AES_CBC_Cipher(secret_key)
    return cipher.decrypt(ciphertext)

def validate_credentials(user, password):
    if user == "qwerty" and password == "asdf":
        return True
    else:
        return False

def login(user, password):

    if not validate_credentials(user, password):
        return False

    cipher = AES_CBC_Cipher(secret_key)
    
    IV = Random.new().read(16)
    return cipher.encrypt(IV, user)

def main():

    token = raw_input("Do you have a token? (y/n)\n")

    if token == "y":
        ciphertext = raw_input("token?\n")

        cipher = AES_CBC_Cipher(secret_key)
        user = cipher.decrypt(ciphertext)

        print("You are logged in as", validate_token(ciphertext))
    else:    
        user = raw_input("user?\n")
        password = raw_input("password?\n")

        token = login(user, password)

        if not token:
            print("Wrong credentials\n")
        else:
            print("Success. here's your token:")
            print(token)

if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
