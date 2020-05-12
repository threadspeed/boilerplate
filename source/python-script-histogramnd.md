---
title: python script histogramnd (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'histogramnd'

Functions in program: 
* `def test4():`
* `def test3():`
* `def test2 ():`
* `def test1a ():`
* `def test0 (clip_fnc=clip_fnc_clip):`
* `def test1 ():`
* `def clip_fnc_raise (x, min, max):`
* `def clip_fnc_clip (x, min, max):`
* `def nint (x):`

Modules used in program: 
* `import numpy as np`

## python histogramnd

Python mysql example: histogramnd

```python
import numpy as np

def nint (x):
    if x >= 0:
        return int (x + 0.5)
    else:
        return int (x - 0.5)
    
def clip_fnc_clip (x, min, max):
    if x > max:
        return max
    elif x < min:
        return min
    else:
        return x

def clip_fnc_raise (x, min, max):
    if x > max:
        raise RuntimeError
    elif x < min:
        raise RuntimeError
    else:
        return x

class histogram (object):
    def __init__ (self, mins, maxs, deltas, clip_fnc=clip_fnc_clip):
        self.mins = mins
        self.maxs = maxs
        self.deltas = deltas
        self.clip_fnc = clip_fnc
        self.n_bucketss = [int ((max - min)/delta + 1) for (max, min, delta) in zip (maxs, mins, deltas)]
        self.buckets = np.zeros ((self.n_bucketss), dtype=int)
        self.count = 0
        
    def __call__ (self, xs, w=1):
        assert len(xs) == self.buckets.ndim
        if hasattr (xs[0], '__len__'):
            if not hasattr (w, '__len__'):
                w = np.broadcast_to (w, len(xs[0]))
            for *a,c in zip(*xs, w):
                self.__call__ (a, c)
            return self
        else:
            indexes = tuple([nint ((self.clip_fnc (x, min, max) - min) / delta) for (x, min, max, delta) in zip (xs, self.mins, self.maxs, self.deltas)])
            self.buckets[indexes] += w
            self.count += 1
            return self

    # def __iadd__ (self, z):
    #     return self (z.real, z.imag)

    @property
    def axes (self):
        return [np.arange (min, max+delta, delta) for (min, max, delta) in zip (self.mins, self.maxs, self.deltas)]

def test1 ():
    h = histogram ((-5, -5), (5, 5), (0.1, 0.1))
    from numpy.random import RandomState
    rs = RandomState(0)
    from normal_c import normal_c
    u = normal_c (rs, 0, 1)
    z = u(1)
    print((z))
    h ((z.real, z.imag))
    return h

def test0 (clip_fnc=clip_fnc_clip):
    h = histogram ((-5,), (5,), (0.1,), clip_fnc)
    h ((np.ones(10),))
    return h

def test1a ():
    h = histogram2d (-5, 5, -5, 5, 0.1, 0.1)
    from numpy.random import RandomState
    rs = RandomState(0)
    from normal_c import normal_c
    u = normal_c (rs, 0, 1)
    z = u(10000)
    h (z.real, z.imag, 2)
    return h

def test2 ():
    h = histogram2d (-5, 5, -5, 5, 0.01, 0.01)
    from numpy.random import RandomState
    rs = RandomState(0)
    from uniform_real import uniform_real
    u = uniform_real (rs, -10, 10)
    z = u (10000) + 1j * u(10000)
    h += (z.real, z.imag)
    return h

def test3():
    h = test1()
    import matplotlib.pyplot as plt
    xaxis, yaxis = h.get_axes()
    a, b = np.meshgrid (xaxis, yaxis)
    plt.pcolor (a, b, h.buckets, cmap='Blues')
    plt.colorbar()
    plt.show()

def test4():
    c = np.zeros ((4,4), dtype=int)
    c[2,2] = 100
    xaxis = yaxis = np.arange (4, dtype=float)
    a, b = np.meshgrid (xaxis, yaxis)
    plt.hexbin (a.flatten(), b.flatten(), c.flatten())
    
if __name__ == '__main__':
    h = test1()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
