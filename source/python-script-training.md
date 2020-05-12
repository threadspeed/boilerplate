---
title: python script training (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'training'

Functions in program: 
* `def main():`
* `def grange(num):`
* `def flatten(nested_list):`
* `def partition(function, sequence):`
* `def iseven(n):`
* `def myfilter(function, sequence):`
* `def mapconcat(function, sequence, separator):`
* `def parallel_read(file1, file2):`
* `def generate_randlist2(num, lower=1, upper=10):`
* `def generate_randlist1(num):`

## python training

Python mysql example: training

```python

def generate_randlist1(num):
    """ランダムなリストを生成
    :param num: 要素数
    """
    import random
    return [random.randint(1, 10) for _ in range(num)]


def generate_randlist2(num, lower=1, upper=10):
    """ランダムなリストを生成(範囲指定)
    :param num: 要素数
    :param lower: 下限の値
    :param upper: 上限の値
    """
    import random
    return [random.randint(lower, upper) for _ in range(num)]


def parallel_read(file1, file2):
    """引数に指定したファイルを並列に読み込んで表示する
    :param file1: ファイル1
    :param file2: ファイル2
    """
    import os
    from itertools import zip_longest
    # 両方のファイルが存在しない場合にはNoneを返す
    if not os.path.exists(file1) or not os.path.exists(file2):
        return None
    with open(file1, 'r')as f1, open(file2, 'r') as f2:
        for l1, l2 in zip_longest(f1, f2):
            # Noneの場合は空文字に変換する
            l1 = '' if l1 is None else l1
            l2 = '' if l2 is None else l2
            l1 = l1.rstrip('\n')
            l2 = l2.rstrip('\n')
            print(l1.ljust(20), '|', l2.ljust(20))


def mapconcat(function, sequence, separator):
    """sequenceの各要素にfunctionを適用して結果を繋げる
    :param function: 適用する関数
    :param sequence: 対象シーケンス
    :param separator: セパレータ
    """
    sequence = map(function, sequence)
    return separator.join(sequence)


def myfilter(function, sequence):
    """sequenceの要素にfunctionの内容にてフィルタリングを実施する
    :param function: 適用する関数
    :param sequence: 対象シーケンス
    """
    return filter(function, sequence)


def iseven(n):
    """偶数かどうかを判定する
    :param n: 対象の数値
    """
    return n % 2 == 0


def partition(function, sequence):
    """sequenceの要素に対応する要素,対応しない要素をタプルにて返却する
    :param function: パーティション判定用関数
    :param sequence: 対象シーケンス
    """
    conform = list(filter(function, sequence))
    return conform, [s for s in sequence if s not in conform]


def flatten(nested_list):
    """入れ子になったリストを平らにする関数
    :param nested_list: 入れ子になったリスト
    """
    import collections
    for elem in nested_list:
        if isinstance(elem, collections.Iterable):
            # Iterableである場合には再起処理
            yield from flatten(elem)
        else:
            yield elem


def grange(num):
    """数値の個数の数列を生み出すジェネレータを定義する
    :param num:数列の個数
    """
    return range(num)


def main():
    for num in generate_randlist1(10):
        print(num)
    for num in generate_randlist2(10, 1, 2):
        print(num)
    parallel_read('add10.py', 'bytecode.txt')
    parallel_read('bytecode.txt', 'add10.py')
    print(mapconcat(str, ["foo", "bar", "baz"], "-"))
    print(mapconcat(str, [1, 2, 3], " "))
    print(mapconcat(lambda c: c*3, "abc", ""))
    print(mapconcat(lambda s: s.rjust(10), ["foo", "bar", "baz"], ""))
    print(list(myfilter(iseven, range(10))))
    print(list(myfilter(lambda x: x < 5, range(-10, 10, 2))))
    print(partition(iseven, range(10)))
    print(partition(lambda x: x < 10, [1, 5, -3, 120, 99, 7, 89]))
    students = [("Beth", 43), ("Kathy", 80), ("Mark", 56),
                ("Mary", 70), ("Susie", 68)]
    print(partition(lambda s: s[1] >= 60, students))
    print(list(flatten([1, 2, [3, 4]])))
    print(list(flatten([1, [2, 3], [4, [5]]])))
    for i in grange(5):
        print(i)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
