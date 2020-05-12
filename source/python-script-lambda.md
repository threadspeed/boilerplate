---
title: python script lambda (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lambda'

Functions in program: 
* `def index():`
* `def myFunc(a, b):`
* `def randomPasswordGenerator(length):`
* `def pow(x, power):`

Modules used in program: 
* `import random, string`

## python lambda

Python example: lambda

```python
########################################################
# How to NOT use Lambdas. An inneficient and yet educa-#
# tonal guide to the proper misuse of the lambda const-#
# ruct in Python 2.x.  DO NOT USE ANY OF THIS EVER     #
#                                   by: e000 (13/6/11) #                 
########################################################

## Part 1. Basic LAMBDA Introduction ##
# Well, it's worth diving straight into what lambdas are.
# Lambdas are pretty much annymous "one line" functions
# that are able to be constructed at runtime. Typical usage
# would be to plug it into `filter()` or `map()`, but that's
# boring. Let's start with the most basic of basic examples.

def pow(x, power):
    return x**power

# Bam, a function that raises `x` to the `power` power.
# Now let's do that in a one lined lambda.
# >>> pow(1, 3)
# 1
# >>> pow(2, 3)
# 8

pow = lambda x, power: x**power

# Fine, that's all cool. Basic and easy or what not.

## Part 2: Scoping within Lambdas -or- A really bad way ##
##         to define variables within lambdas.          ##
# Let's try something a bit more complicated. A random
# string or password generator? Sure.

import random, string
characters = string.digits + string.letters

def randomPasswordGenerator(length):
    return ''.join(random.choice(characters) for i in xrange(length))
    
# >>> randomPasswordGenerator(8)
# 'bDpHVxiO'

# Haah! That was cake! Now in this terrible tutorial, we're going to
# prohibit the use of defining ANYTHING outside of the lambda function,
# including any kind of variable, or import. So, how are we going to get
# `random` and `string`. Well the answer is obvious, we're going to make
# a lambda inside of a lambda inside of a lambda. We're also going to use
# a bit of `__import__` trickery.

randomPasswordGenerator = \
(lambda random, string: # level 1
    (lambda characters: # level 2
        lambda length: ''.join(random.choice(characters) for i in xrange(length)) # level 3
    )(string.digits + string.letters) # level 2 args
)(
    __import__('random'), # level 1 args
    __import__('string')
)

# Haha, wait... WHAT? That's totally unpythonic. That's disgusting. That's
# a literal abomination. Why would anyone ever want to do that EVER?
#   - That's actually a good question? But then again, this tutorial is about
#     how to NOT use lambdas.

## Part 3. How to give lambdas function names. ##
# In a world where absurdity peaks, and somehow we NEED a
# function name, for what ever reason. Here's how to do it.
#           THIS IS NOT FOR THE WEAK HEARTED.

# First, let's start with some regular code.

def myFunc(a, b):
    return a + b

# >>> myFunc
# <function myFunc at 0x...>

myLambda = lambda a, b: a + b

# >>> myLambda
# <function <lambda> at 0x...>
# Uh'oh! How are we going to give this function a name?
# Some hackery with the `new` module shall work.

myFunc = (lambda(new):
    new.function(
        (lambda a, b: a + b).func_code, {}, 'myFunc'
    )
)(__import__('new'))

# >>> myFunc
# <function myFunc at 0x...>
# LOL! It works! Isn't that disgusting? 

## Part 4. A class? With lambdas? You've got to be kidding me! ##
# If you haven't raged and exited out of this tutorial yet,
# you'll probably want to take a deep breath. Let's start with a
# simple class that we'll call `Foo`

class Foo:
    classVariable = 'ImAClassVariable'
    def __init__(self, a, b, c):
        self._a = a
        self._b = b
        self._c = c
        
    def getA(self):
        return self._a
    
    @classmethod
    def aClassMethod(cls):
        return cls.classVariable
    
    @staticmethod
    def aStaticMethod(a, b):
        return a + b
    
    def __repr__(self):
        return '<%s: %r>' % (
            self.__class__.__name__,
            vars(self)
        )
        
# Alright, that's easy enough...
# >>> p = Foo(1, 2, 3)
# >>> p
# <Foo: {'_c': 3, '_b': 2, '_a': 1}>
# >>> p.getA()
# 1
# >>> Foo.aStaticMethod(1, 1)
# 2
# >>> Foo.aClassMethod()
# 'ImAClassVariable'
        
# **INHALE**
# Here's it using lambdas.
        
Foo = (lambda(new): # level 1, we define our new variable.
        new.classobj('Foo', (), dict( # return a class object.
            classVariable = 'ImAClassVariable',
            __init__ = (lambda self, a, b, c:
                self.__dict__.update(dict(
                    _a = a,
                    _b = b,
                    _c = c
                ))
            ),
            getA = lambda self: self._a,
            aClassMethod = classmethod(
                lambda cls: cls.classVariable
            ),
            aStaticMethod = staticmethod(
                lambda a, b: a + b
            ),
            __repr__ = (lambda self:
                '<%s: %r>' % (
                    self.__class__.__name__,
                    vars(self)
                )   
            )
        ))
    )(__import__('new')) # level 1 args

# That's all kinds of fucked up. Isn't it?

## Part 5. Flask + Lambda??? OH GOD NO STOP!!! ##
# No comment.

from flask import Flask

app = Flask('__name__')

@app.route('/')
def index():
    return 'Hello World!'

app.run()

# ...

(lambda flask:
    (lambda app:
        (app,
         app.route('/')(
            lambda: 'Hello World!'
         )
        )[0]
    )(flask.Flask('__name__')).run()
)(__import__('flask'))

# And that's all folks.

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
