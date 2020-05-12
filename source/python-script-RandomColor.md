---
title: python script RandomColor (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RandomColor'


Modules used in program: 
* `import random`

## python RandomColor

Python mysql example: RandomColor

```python
import random
from colored import fg, bg, attr

class RandomColorDict(dict):
    """Color storage class.

    Stores ANSI coloring specifications as formatted strings and converts
    to ANSI sequences on access.

    The value format is 'key1:value1+key2:value2'. Only 'fg', 'bg', and 'attr' are
    recognized keynames.  Recognized values are colornames (for fg/bg) or
    attribute names (for attr) as defined in the colored library.  Multiple 'fg'
    and 'bg' keys are overwritten -- only the last found is used.  Multiple 'attr'
    keys can coexist but duplicate values are not checked.

    The value 'random' causes obj[key] to return a random ANSI foreground coloring.
    For nonexistent keys, obj[notakey] will also return a random ANSI foreground
    instead of throwing a KeyError.  Use obj.get(key) if you need the real value
    (nonexistent keys will return None).

    Each instance of the class stores its own PRNG.
    """
    def __init__(self, choices, *args, **kwargs):
        """choices: a list of ints to randomly choose from"""
        super(RandomColorDict, self).__init__(*args, **kwargs)
        self.random = random.Random()
        self.random.seed()
        self.choices = choices

    def __getitem__(self, key):
        """Overload to return a random fg(color) if the value is 'random'
        or the key does not exist."""
        val = None
        try:
            val = super(RandomColorDict, self).__getitem__(key)
        except:
            # catch nonexistent keys and return a random value
            val = 'random'

        if val == 'random':
            return fg(self.random.choice(self.choices))
            # could add other attributes or bg colors here but might be too much
        return RandomColorDict._ansiconvert(val)

    @staticmethod
    def _ansiconvert(val):
        # fg:color+bg:color+attr:attrname+attr:attrname
        fore = ""
        back = ""
        attribs = ""

        chunks = val.split('+')
        for chunk in chunks:
            (t, name) = chunk.split(':')

            if t == 'fg':
                # only one foreground color allowed so overwrite
                fore = fg(name)
            elif t == 'bg':
                # only one background color allowed so overwrite
                back = bg(name)
            elif t == 'attr':
                # multiple attribs can be combined so append
                attribs += attr(name)

        return fore+back+attribs

### end RandomColorDict


# sample use
from colored import stylize
from RandomColor import RandomColorDict
colors = list(range(19,231))
#
## define the theme
mytheme = RandomColorDict( colors, {
    'ui_info':            'fg:blue',                 # UI (info msg)
    'ui_error':           'fg:red+attr:bold',        # UI (error msg)
    'user_display':       'random',                  # user detail
    'spoiler':            'fg:red',                  # spoiler text
    'timestamp':          'attr:dim',                # timestamps (general use)
    'toot_name':          'random',                  # timeline (name line)
    'toot_content':       'fg:grey_82',              # timeline (content, summary)
    'toot_reply':         'fg:black+bg:yellow',      # timeline (reply header)
    'mention':            'fg:magenta_2b',           # notifications
    'favourite':          'fg:sea_green_2',          # notifications
    'reblog':             'fg:yellow_2',             # notifications
    'follow':             'fg:red_1',                # notifications
    # ... etc ...
    })
#
## now print(the pieces)
## first line -- random name color, dimmed timestamp
print( stylize(display_name, mytheme['toot_name']) + stylize(timestamp, mytheme['timestamp']) )
#
## second line -- red, black-on-yellow
print( stylize(spoiler, mytheme['spoiler']) + stylize(replytext, mytheme['toot_reply']) )



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
