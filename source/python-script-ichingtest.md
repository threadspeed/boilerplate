---
title: python script ichingtest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ichingtest'

Functions in program: 
* `def malicious_test(rounds = 30000, WIDTH=20):`
* `def honest_test():`
* `def validate_corechain(C):`
* `def fake_verify(pk, m, sig):`
* `def fake_sign(pk, m):`
* `def random_bytes(n):`
* `def hash_to_unit(h):`
* `def unhex(x): return unhexlify(x)`
* `def hex(x): return hexlify(x)`
* `def hash(x):`

Modules used in program: 
* `import random`
* `import random`

## python ichingtest

Python example: ichingtest

```python
from Crypto.Hash import SHA256
from binascii import hexlify, unhexlify
import random

### Basic utilities

def hash(x):
    assert type(x) is str
    return SHA256.new(x).digest()

def hex(x): return hexlify(x)
def unhex(x): return unhexlify(x)

def hash_to_unit(h):
    assert type(h) is str and len(h) == 32
    return int(hex(h),16) / (2.**256)

def random_bytes(n):
    return ''.join(chr(random.randint(0,255)) for _ in range(n))


### Signature utilities

def fake_sign(pk, m):
    # Not a real signature scheme, we can generate the signature
    # just given the public key
    assert type(pk) is str and len(pk) == 32
    return hash(pk + m)

def fake_verify(pk, m, sig):
    assert fake_sign(pk, m) == sig
    return True

### PoS experiment

import random
random.seed(10)

genesis = '\x00'*32

"""
 Default parameters:
  67 honest parties
  33 attacker parties
  Each party gets to make 1 query per round

  The goal is that on average, it takes 300 rounds to find a solution
  The difficulty is therefore 1 / (100 * 300)
"""
T = 1. / (100 * 300)
NUM_HONEST = 67
NUM_BAD = 33
    
def validate_corechain(C):
    prev = genesis
    prevround = -1
    for block in C:
        ( prev_, rnd, pk, sig ) = block

        # Check prev hash
        assert prev_ == prev

        # Check the signature
        assert fake_verify(pk, prev, sig)

        # Check the round
        assert type(rnd) is str and len(rnd) == 32
        round = int(rnd)
        assert round > prevround
        prevround = round

        # Check the hash and difficulty
        h = hash(''.join(block))
        assert hash_to_unit(h) <= T
        prev = h
        
    return True

def honest_test():
    honest_keys = [random_bytes(32) for _ in range(NUM_HONEST)]
    bestchain = []
    bestprevhash = genesis
    for round in range(30000):
        for i, pk in enumerate(honest_keys):
            # Compute the signature on the prev block
            sig = fake_sign(pk, bestprevhash)

            # Compute the (potential) next block
            block = ( bestprevhash, str(round).rjust(32), pk, sig )

            # Check if the block wins
            h = hash(''.join(block))
            if hash_to_unit(h) <= T:
                print('Party %d found a block in round %d' % (i, round))
                bestchain.append(block)
                bestprevhash = h
                assert validate_corechain(bestchain)

    global besthonestchain
    besthonestchain = bestchain
    print('Length of honest chain: ', len(bestchain))
    assert validate_corechain(bestchain)
    print('Validation OK')

def malicious_test(rounds = 30000, WIDTH=20):
    # The idea behind this attack is that the attacker keeps
    # track of *multiple* possible corechains to extend, not
    # just the *single best* chain.
    #    
    # In other words, instead of keeping track of "bestchain",
    # this attack keeps track of the top `WIDTH` chains, in a list
    # called `top_blocks`. Instead of just trying to extend the
    # single top block, in each round we try to extend all of the
    # blocks in `top_blocks`. After finding a new block, we 
    # replace the smallest block in `top_blocks` with it.
    #
    # In principle this attack would work with an arbitrary number
    # of `top_blocks`, but fixing it to a maximum `WIDTH` makes it
    # computationally tractable.
    
    print('Expected best (honest mining):', T * rounds * NUM_BAD)
    bad_keys = [random_bytes(32) for _ in range(NUM_BAD)]
    
    block_dict = {}    # mapping from hash => block
    top_blocks = [(0,genesis)] # List of (len, h)

    for round in range(rounds):
        for i, pk, in enumerate(bad_keys):
            # Try extending the top_blocks
            for l, prev in top_blocks:
                sig = fake_sign(pk, prev)
                block = ( prev, str(round).rjust(32), pk, sig )
                h = hash(''.join(block))
                if hash_to_unit(h) <= T:
                    print('Party %d found a block in round %d, length %d (expected: %.2f)' % (i, round, l+1, float(T * round * NUM_BAD)))
                    block_dict[h] = (l+1, block)
                    top_blocks.append( (l+1, h) )
                    top_blocks = sorted(top_blocks)
                    top_blocks = top_blocks[-WIDTH:] # Only keep the largest
                    print([l for (l,_) in top_blocks])

    bestlen, prev = top_blocks[-1]
    C = []
    while prev != genesis:
        block = block_dict[prev]
        C = [block] + C
        (prev, _, _, _) = block
    print('Best:', len(C))
    validate_corechain(C)
    print('Validation OK')
    return C

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
