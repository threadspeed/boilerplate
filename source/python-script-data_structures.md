---
title: python script data structures (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'data structures'

Functions in program: 
* `def detect_cycle2(lst):`
* `def detect_cycle1(lst):`

Modules used in program: 
* `import random`

## python data structures

Python mysql example: data structures

```python
import random
class TreeNode:
    def __init__(self, key, value, left=None, right=None):
        self.key = key
        self.value = value
        self.left = left
        self.right = right

class BinarySearchTree:
    def __init__(self):
        self.root = None

    def lookup(self, key):
        def __lookup(node, key):
            if node == None:
                return None
            if key == node.key:
                return node.value
            if key < node.key:
                return __lookup(node.left, key)
            return __lookup(node.right, key)
        return __lookup(self.root, key)

    def insert(self, key, value=None):
        def __insert(node, key, value):
            if node == None:
                return TreeNode(key, value)
            if key == node.key:
                node.value = value
            elif key < node.key:
                node.left = __insert(node.left, key, value)
            else:
                node.right = __insert(node.right, key, value)
            return node
        self.root = __insert(self.root, key, value)

    def size(self):
        def __size(node):
            if node == None:
                return 0
            return 1 + __size(node.left) + __size(node.right)
        return __size(self.root)

    def depth(self):
        def __depth(node):
            if node == None:
                return -1
            return 1 + max(__depth(node.left), __depth(node.right))
        return __depth(self.root)

    def min(self):
        if self.root == None:
            return None
        node = self.root
        while node.left != None:
            node = node.left
        return node.key

    def traverse(self):
        def __traverse(node):
            if node.left != None:
                for elem in __traverse(node.left):
                    yield elem
            yield node.key, node.value
            if node.right != None:
                for elem in __traverse(node.right):
                    yield elem
        return __traverse(self.root)

# ---------------------- #
class Node():
    def __init__(self, val):
        self.value = val
        self.next = None

class LinkedList():
    def __init__(self):
        self.value = "dummy"
        self.next = None

    def add_at_start(self, val):
        p = self
        tmp = p.next
        p.next = Node(val)
        p.next.next = tmp
    
    def add_at_end(self, val):
        p = self
        while p.next != None:
            p = p.next
        p.next = Node(val)      

    def insert(self, val, loc):
        p = self
        for i in range(loc):
            p = p.next
        tmp = p.next
        p.next = Node(val)
        p.next.next = tmp

    def delete(self, loc):
        p = self
        for i in range(loc):
            p = p.next
        if p != None and p.next != None:
            p.next = p.next.next
            
    def get_item(self, loc):
        p = self.next
        for i in range(loc):
            p = p.next
        return p
            
    def find(self, item):
        p = self.next
        loc = 0
        while p != None:
            if p.value == item:
                return p, loc
            else:
                p = p.next
                loc = loc + 1
        return None     

# Detecting cycles in linked lists.    
def detect_cycle1(lst):
    p = lst.next
    d = {}
    while True:
        if p == None:
            return False
        elif id(p) in d:
            return True
        d[id(p)] = 1
        p = p.next
        
def detect_cycle2(lst):
   slow = fast = lst
   while True:
       if slow == None or fast == None or fast.next == None:
           return False
       slow = slow.next
       fast = fast.next.next
       if slow is fast:
           return True

class HashTable():
    def __init__(self, m):
        # initial hash table, m empty entries
        self._table = [[] for i in range(m)]
    
    def hash_mod(self, key, mod, func=hash):
        return func(key) % mod
    
    def contained(self, key, list_of_items):
        """ checks if key is in list_of_items
            returns location in list (if found), or None"""
        for k in range(len(list_of_items)):
            if key == list_of_items[k][0]:
                return k  # return index of candidate in list 
        return None

    def __getitem__(self, key):
        """ finds an item in a hash table and returns it.
            If the item is not found, returns None"""
        mod = len(self._table)
        i = self.hash_mod(key, mod)    
        list_of_items = self._table[i]
        k = self.contained(key, list_of_items)
        if k != None:  # key exists in table
            return list_of_items[k][1]
        return None
            
    def __setitem__(self, key, value):
        """ inserts an item into a hash table. If key already
            exists, the value is updated. Always returns None"""
        mod = len(self._table)
        i = self.hash_mod(key, mod)
        list_of_items = self._table[i]
        k = self.contained(key, list_of_items)
        if k != None:  # key exists in table
            list_of_items[k] = (key, value)
        else:
            list_of_items.append((key, value))
        return None

    def delete(self, key, func=hash):
        """ deletes an item from a hash table. """
        mod = len(self._table)
        i = self.hash_mod(key, mod, func)
        list_of_items = self._table[i]
        k = self.contained(key, list_of_items)
        if k != None:  # key exists in table
            list_of_items.pop(k)
            return True
        return False

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
