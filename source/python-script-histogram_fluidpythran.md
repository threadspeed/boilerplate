---
title: python script histogram fluidpythran (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'histogram fluidpythran'

Functions in program: 
* `def test4():`
* `def test3():`
* `def test2():`
* `def test1a():`
* `def test0(clip_method="clip"):`
* `def test1():`
* `def clip_fnc_raise(x: float, min: float, max: float):`
* `def clip_fnc_clip(x: float, min: float, max: float):`
* `def nint(x: float):`

Modules used in program: 
* `import numpy as np`

## python histogram fluidpythran

Python mysql example: histogram fluidpythran

```python

import numpy as np

from fluidpythran import boost, Array, NDim


@boost
def nint(x: float):
    if x >= 0:
        return int(x + 0.5)
    else:
        return int(x - 0.5)


@boost
def clip_fnc_clip(x: float, min: float, max: float):
    if x > max:
        return max
    elif x < min:
        return min
    else:
        return x


@boost
def clip_fnc_raise(x: float, min: float, max: float):
    if x > max:
        raise RuntimeError
    elif x < min:
        raise RuntimeError
    else:
        return x


A = "float[]"


@boost
class Histogram:

    buckets: Array[int, NDim(1, 2, 3)]
    mins: A
    maxs: A
    deltas: A
    clip_method: str

    def __init__(self, mins, maxs, deltas, clip_method="clip"):
        self.mins = np.array(mins, float)
        self.maxs = np.array(maxs, float)
        self.deltas = np.array(deltas, float)
        self.clip_method = clip_method
        self.n_bucketss = [
            int((max - min) / delta + 1)
            for (max, min, delta) in zip(maxs, mins, deltas)
        ]
        self.buckets = np.zeros((self.n_bucketss), dtype=int)

    @boost
    def compute(self, xs: "float list", w: "int or int[]"):

        if self.clip_method == "clip":
            clip_fnc = clip_fnc_clip
        elif self.clip_method == "raise":
            clip_fnc = clip_fnc_raise
        else:
            print(self.clip_method)
            raise ValueError
        indexes = [
            nint((clip_fnc(x, min, max) - min) / delta)
            for (x, min, max, delta) in zip(
                xs, self.mins, self.maxs, self.deltas
            )
        ]
        self.buckets[indexes] += w

    def __call__(self, xs, w=1):
        print("__call__", xs, type(xs))
        assert len(xs) == self.buckets.ndim
        if hasattr(xs[0], "__len__"):
            if not hasattr(w, "__len__"):
                w = np.broadcast_to(w, len(xs[0]))
            for *a, c in zip(*xs, w):
                self.__call__(a, c)
            return self
        else:
            self.compute(xs, w)
            return self

    # def __iadd__ (self, z):
    #     return self (z.real, z.imag)

    @property
    def axes(self):
        return [
            np.arange(min, max + delta, delta)
            for (min, max, delta) in zip(self.mins, self.maxs, self.deltas)
        ]


def test1():
    h = Histogram((-5, -5), (5, 5), (0.1, 0.1))
    # from numpy.random import RandomState

    # rs = RandomState(0)
    # from normal_c import normal_c

    # u = normal_c(rs, 0, 1)
    # z = u(10000)
    # h((z.real, z.imag))h.buckets.shape
    return h


def test0(clip_method="clip"):
    h = Histogram((-5,), (5,), (0.1,), clip_method)
    h((np.ones(10),))
    return h


def test1a():
    h = histogram2d(-5, 5, -5, 5, 0.1, 0.1)
    from numpy.random import RandomState

    rs = RandomState(0)
    from normal_c import normal_c

    u = normal_c(rs, 0, 1)
    z = u(10000)
    h(z.real, z.imag, 2)
    return h


def test2():
    h = histogram2d(-5, 5, -5, 5, 0.01, 0.01)
    from numpy.random import RandomState

    rs = RandomState(0)
    from uniform_real import uniform_real

    u = uniform_real(rs, -10, 10)
    z = u(10000) + 1j * u(10000)
    h += (z.real, z.imag)
    return h


def test3():
    h = test1()
    import matplotlib.pyplot as plt

    xaxis, yaxis = h.get_axes()
    a, b = np.meshgrid(xaxis, yaxis)
    plt.pcolor(a, b, h.buckets, cmap="Blues")
    plt.colorbar()
    plt.show()


def test4():
    c = np.zeros((4, 4), dtype=int)
    c[2, 2] = 100
    xaxis = yaxis = np.arange(4, dtype=float)
    a, b = np.meshgrid(xaxis, yaxis)
    plt.hexbin(a.flatten(), b.flatten(), c.flatten())


if __name__ == "__main__":
    h = test0()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
