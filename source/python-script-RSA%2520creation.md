---
title: python script RSA%2520creation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RSA%2520creation'


Modules used in program: 
* `import random`

## python RSA%2520creation

Python example: RSA%2520creation

```python
from Crypto.PublicKey import RSA
from Crypto import Random
import random

class Key:
    
    def __init__(self, key = None):
        
        if key:
            if isinstance(key, RSA._RSAobj):
                self.key = key
            else:
                try: 
                    self.key = self._loadKeyFromFile(key)
                except:
                    try:
                        self.key = RSA.importKey(key)
                    except:
                        raise Exception("key is not a key object, path to a key or key string")

        else:
            self.key = self._createKey()

    def _readFile(self, path, mode = "rb"):
        """
        reads data from a file
        """
        
        handle = open(path, mode)
        data = handle.read()
        handle.close()
        
        return data
    
    def _saveFile(self, string, path, mode = "w"):
        """
        saves data to a file
        """
        
        handle = open(path, mode)
        handle.write(string)
        handle.close()
        
    def _createKey(self):
        """
        creates a key and returns it
        """
        random_generator = Random.new().read
        return RSA.generate(1024, random_generator)
    
        
    def _loadKeyFromFile(self, path):
        """
        loads a key from file
        """
        return RSA.importKey(self._readFile(path))
    
    def encryptString(self, data):
        """
        encrypts a string
        """
        return self.key.encrypt(data, random.randint(1,100))
        
    def encryptFile(self, path, mode = "rb"):
        """
        reads and encrypts a file
        """
        return self.key.encrypt(self._readFile(path, mode), random.randint(1,100))
    
    def decryptString(self, string):
        return self.key.decrypt(string)
    
    def decryptFile(self, string, path, mode = "w"):
        """
        string = string to decrypt
        path = path to save file
        mode = mode to save file
        """
        self._saveFile(self.decryptString(string), path, mode)

    def getPublicKey(self):
        """
        returns a key object from a public key
        Note that public keys can only encrypt data
        """
        return Key(self.key.publickey())
    
    def exportKey(self):
        return self.key.exportKey()
    
    def saveKey(self, path):
        
        self._saveFile(self.key.exportKey(), path, mode = "w")
        
    def getKey(self):
        
        return self.key
        
class KeyPair:
    
    def __init__(self, pubKey = None, privKey = None, createPubKey = False, createPrivKey = False):
        """
        creates a keyPair for encoding and decoding data between 2 sources
        """
        
        self.pubKey = Key(pubKey) if pubKey or createPubKey else None
        self.privKey = Key(privKey) if privKey or createPrivKey else None
        
    def setPrivKey(self, key):
        self.privKey = Key(key)
        
    def setPubKey(self, key):
        self.pubKey = Key(key)
        
    def decryptString(self, string):
        return self.privKey.decryptString(string)
    
    def encryptString(self, string):
        return self.pubKey.encryptString(string)
    
    def decryptFile(self, string, path, mode):
        self.privKey.decryptFile(string, path, mode)
        
    def encryptFile(self, string, path, mode = "rb"):
        self.pubKey.encryptFile(path, mode)
        
if __name__ == "__main__":
    
    key = Key()
    print("key created")
    
    key.saveKey("priv")
    print("key saved")
    
    key = Key("priv")
    "key loaded from file"
    
    key = Key(key.exportKey())
    print("key created from keyString")
    
    pubKey = key.getPublicKey()
    pubKey.saveKey("pubKey")
    print("saving public key")
    
    
    
    
  

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
