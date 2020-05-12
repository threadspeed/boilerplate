---
title: python script trree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'trree'

Functions in program: 
* `def inorder(root): `
* `def list_search(lst, value):`
* `def list_delete(lst, value): `
* `def list_insert(lst, value): `
* `def delete(root, z):`
* `def transplant(root, u, v):`
* `def Min(root):`
* `def search_data(root, value):`
* `def search(root, value):`
* `def insert(root, node):`

Modules used in program: 
* `import random`
* `import random`

## python trree

Python mysql example: trree

```python
import random

class Node:
    def __init__(self, val):
        self.l_child = None
        self.r_child = None
        self.parent = None
        self.data = val

def insert(root, node):
    """inserts a node into a tree rooted at root, returns the root"""
    if root is None:
        root = node
    else:
        if root.data > node.data:
            if root.l_child is None:
                root.l_child = node
                node.parent = root
            else:
                insert(root.l_child, node)
        else:
            if root.r_child is None:
                root.r_child = node
                node.parent = root
            else:
                insert(root.r_child,node)
    return root


def search(root, value):
    """searches a tree rooted at root for a node with data = value, returns the node if found, None otherwise"""
    if root == None or value == root.data:
        return root
    if value < root.data:
        return search(root.l_child, value)
    else:
        return search(root.r_child, value)


def search_data(root, value):
    v = search(root, value)
    if v != None:
        return v.data


def Min(root):
    while root.l_child != None:
        root = root.l_child
    return root

def transplant(root, u, v):
    if u.parent == None:
        root = v
    elif u == u.parent.l_child:
        u.parent.l_child = v
    else:
        u.parent.r_child = v
    if v != None:
        v.parent = u.parent
        

def delete(root, z):
    """if a node with data = value is present in the tree rooted at root, deletes that node and returns the root"""
    z = search(root, z)
    if z == None:
        return root 
    if z.l_child == None:
        transplant(root, z, z.r_child)
    elif z.r_child == None:
        transplant(root, z, z.l_child)
    else:
        y = Min(z.r_child)
        if y.parent != z:
            transplant(root, y, y.r_child)
            y.r_child = z.r_child
            y.r_child.parent = y
        transplant(root, z, y)
        y.l_child = z.l_child
        y.l_child.parent = y
        
    return root
        


        

def list_insert(lst, value): 
    """inserts value into lst in sorted order"""
    lst.append(value)
    lst.sort()
            
def list_delete(lst, value): 
    """ deletes first instance of value from lst if it present"""
    if value in lst:
        lst.remove(value)
        lst.sort()

def list_search(lst, value):
    """ searches lst for value and returns value if present, None if it is not present"""
    if value in lst:
        return value
    else:
        return None

def inorder(root): 
    """returns a list of all data in the tree rooted at root produced using an in order traversal"""
    if root != None:
        inorder(root.l_child)
        print(root.data)
        inorder(root.r_child)
    
    
###
### Testing Code
###

import random
bst = None
lst = []

for x in [Node(random.randint(0,100)) for _ in range(50)]: 
    if not bst: 
        bst = x
    else: 
        insert(bst, x)
    list_insert(lst, x.data)
    
for x in [random.randint(0,100) for _ in range(50)]: 
    bst = delete(bst, x)
    list_delete(lst,x)

for x in [random.randint(0,100) for _ in range(50)]: 
    print(x, search_data(bst, x), list_search(lst, x))
    
#print(inorder(bst))
print(lst)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
