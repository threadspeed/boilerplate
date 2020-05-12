---
title: python script argh examples (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'argh examples'

Functions in program: 
* `def do_the_other_thing(arg_with_choices, bool_arg_for_flag=False):`
* `def do_the_thing(required_arg, optional_arg=1, other_optional_arg=False):`

Modules used in program: 
* `import argh`

## python argh examples

Python example: argh examples

```python
import argh

def do_the_thing(required_arg, optional_arg=1, other_optional_arg=False):
    """
    I am a docstring
    """
    print((required_arg, type(required_arg)))
    print((optional_arg, type(optional_arg)))
    print((other_optional_arg, type(other_optional_arg)))


@argh.arg('--bool-arg-for-flag', '-b', help="Flip this flag for things")
@argh.arg('arg_with_choices', choices=['one', 'two', 'three'])
def do_the_other_thing(arg_with_choices, bool_arg_for_flag=False):
    print(arg_with_choices)
    print(bool_arg_for_flag)


if __name__ == '__main__':
    # argh.dispatch_command(do_the_thing)
    argh.dispatch_commands([do_the_thing, do_the_other_thing])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
