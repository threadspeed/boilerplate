---
title: python script password generator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'password generator'

Functions in program: 
* `def main():`
* `def password(pattern, length=0):`
* `def charset(expansion, exclude=''):`

Modules used in program: 
* `import argparse`

## python password generator

Python example: password generator

```python
import argparse
try:
    from Crypto.Random import random
except ImportError:
    try:
        import secrets as random
    except ImportError:
        import random

"""
Patterned Password Generator

Command examples:
$ python password_generator.py -n 5 'qiita-%d%X%x%x%A%C%c%c%B%V%v%D%Q%q%Y%Z%z%W%L%l'
$ python password_generator.py -n 5 'qiita-%3d'
$ python password_generator.py -n 5 'qiita-%{dXxxACccBVvDQqYZzWLl}'
$ python password_generator.py -n 5 '%8[01]'
$ python password_generator.py -n 5 '%8[S-Z]'
$ python password_generator.py -n 5 '%8[S\-Z]'
$ python password_generator.py -n 10 'qiita%4{-c3d}'
$ python password_generator.py -n 10 'qiita%4{-Qvqd}'
$ python password_generator.py -n 10 'qiita%2{-C3{2c[13579]}}'

BNF of password pattern:
<pattern> ::= ( <item> )+
<item> ::= "%" <percent> | <char>
<percent> ::= [<repeat>] <expander>
<repeat> ::= ("0"|"1"|"2"|"3"|"4"|"5"|"6"|"7"|"8"|"9")+
<expander> ::= "[" <blacket> "]" | "{" <brace> "}" | <special> | <char>
<blacket> ::= <charset>
<brace> ::= ( <percent> )+
<special> ::= "b"|"o"|"d"|"X"|"x"|"A"|"C"|"c"|"B"|"V"|"v"|"D"|"Q"|"q"|"Y"|"Z"|"z"|"W"|"L"|"l"
<charset> ::= <expansion>
<expansion> ::= ( <start> "-" <end> | <char> )+
<start> ::= <char>
<end> ::= <char>
<char> ::= <escape> character | character
<escape> ::= "\\"
"""


class Iterator:

    def __init__(self, pattern, escape='\\'):
        self.pattern = pattern
        self.escape = escape
        self.index = 0

    def __iter__(self):
        return self

    def __next__(self):
        c = self.fetch()
        if c is None:
            raise StopIteration()
        self.index += 1
        return c

    def fetch(self):
        if self.index >= len(self.pattern):
            return None
        return self.pattern[self.index]

    def unescape(self):
        if self.index == 0:
            return None
        last = self.pattern[self.index - 1]
        return last == self.escape and self.fetch() and next(self) or last


def charset(expansion, exclude=''):
    """
    >>> charset('123')
    '123'
    >>> charset('0-9')
    '0123456789'
    >>> charset('0\\-9')
    '0-9'
    >>> charset('-0-9-')
    '-0123456789-'
    >>> charset('A-F-1-')
    'ABCDEF-1-'
    >>> charset('A-F-1-6')
    'ABCDEF-123456'
    >>> charset('A-F1-6xyz')
    'ABCDEF123456xyz'
    >>> charset('xA-Fy1-6z')
    'xABCDEFy123456z'
    """
    def expand():
        start = None
        e = Iterator(expansion)
        for c in e:
            if c == '-' and start and e.fetch():
                next(e)  # skip '-'
                end = e.unescape()
                yield from map(chr, range(ord(start) + 1, ord(end) + 1))
                start = None
            else:
                c = e.unescape()
                yield c
                start = c
    return ''.join(c for c in expand() if c not in exclude)


class Blacket:

    def __init__(self, parser):
        expansion = ''
        escape = False
        for c in parser:
            if not escape and c == ']':
                break
            expansion += c
            escape = not escape and c == '\\'
        self.selection = charset(expansion)

    def __iter__(self):
        yield self.selection


class Brace:

    def __init__(self, parser):
        self.percents = []
        while parser.fetch():
            if parser.fetch() == '}':
                next(parser)  # skip '}'
                break
            self.percents.append(Percent(parser))

    def __iter__(self):
        for percent in self.percents:
            yield from percent


class Percent:
    EXPANDER = {
        '[': Blacket,
        '{': Brace,
    }
    SPECIAL = {
        'b': '01',
        'o': charset('0-7'),
        'd': charset('0-9'),
        'X': charset('0-9A-F'),
        'x': charset('0-9a-f'),
        'A': charset('A-Za-z'),
        'C': charset('A-Z'),
        'c': charset('a-z'),
        'B': 'AEIOUaeiou',
        'V': 'AEIOU',
        'v': 'aeiou',
        'D': charset('A-Za-z', 'AEIUOaeiou'),
        'Q': charset('A-Z', 'AEIOU'),
        'q': charset('a-z', 'aeiou'),
        'Y': charset('0-9A-Za-z'),
        'Z': charset('0-9A-Z'),
        'z': charset('0-9a-z'),
        'W': charset('0-9A-Za-z_'),
        'L': charset('0-9A-Z_'),
        'l': charset('0-9A-Z_'),
    }

    def __init__(self, parser):
        self.repeat = 0
        c = next(parser)
        while c.isdigit():
            self.repeat = self.repeat * 10 + int(c)
            c = next(parser)
        if c in self.EXPANDER:
            self.expander = self.EXPANDER[c](parser)
        elif c in self.SPECIAL:
            self.expander = (self.SPECIAL[c],)
        else:
            self.expander = (parser.unescape(),)

    def __iter__(self):
        for _ in range(self.repeat or 1):
            yield from self.expander


class Parser(Iterator):

    def parse(self):
        for c in self:
            if c == '%':
                yield from Percent(self)
            else:
                yield self.unescape()


class PasswordGenerator:
    """
    >>> from random import Random
    >>> generate = PasswordGenerator(choice=Random(0).choice).generate
    >>> generate('qiita-%d%X%x%x%A%C%c%c%B%V%v%D%Q%q%Y%Z%z%W%L%l')
    'qiita-4Fb6gEjeEUirYgJ64vLU'
    >>> generate('qiita-%3d')
    'qiita-784'
    >>> generate('qiita-%{dXxxACccBVvDQqYZzWLl}')
    'qiita-57a2MShhIUoHDnuWv6JZ'
    >>> generate('%8[01]')
    '10101101'
    >>> generate('%8[S-Z]')
    'XVWUVUSW'
    >>> generate('%8[S\\-Z]')
    '-SSZSSSS'
    >>> generate('qiita%4{-c3d}')
    'qiita-o751-t179-g304-w352'
    >>> generate('qiita%4{-Qvqd}')
    'qiita-Cuz8-Baz3-Qap1-Yaj2'
    >>> generate('qiita%2{-C3{2c[13579]}}')
    'qiita-Tdi1hc5ln3-Qob9dw7gi5'
    """

    def __init__(self, choice=None):
        self.choice = choice or random.choice

    def generate(self, pattern):
        parser = Parser(pattern)
        return ''.join(self.choice(selection) for selection in parser.parse())


def password(pattern, length=0):
    generator = PasswordGenerator()
    password = generator.generate(pattern)
    if length == 0:
        return password
    while len(password) < length:
        password += generator.generate(pattern)
    return password[:length]


def main():
    parser = argparse.ArgumentParser()
    parser.add_argument('-n', '--count', type=int, default=0)
    parser.add_argument('-l', '--length', type=int, default=0)
    parser.add_argument('-U', '--upper', action='store_true', default=False)
    parser.add_argument('-L', '--lower', action='store_true', default=False)
    parser.add_argument('pattern', type=str, default='%l')
    args = parser.parse_args()
    width = len(str(args.count))
    convert = args.upper and str.upper or args.lower and str.lower or str
    for count in range(1, args.count + 1):
        print(f"{count:{width}}:", convert(password(args.pattern, args.length)))

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
