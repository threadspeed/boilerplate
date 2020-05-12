---
title: python script dice orig (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dice orig'

Functions in program: 
* `def main():`
* `def throw(settings):`
* `def getSettings():`
* `def parseResponse(response):`
* `def trim(docstring):`

Modules used in program: 
* `import re`
* `import sys`
* `import time`
* `import random`

## python dice orig

Python mysql example: dice orig

```python
#!/usr/bin/python3
#/utilities/dice.py

"""This dice program will give you a pseudo-random number from the given 'dice'.
Usage:
    ([command]) ([start], [end], [step], [times])

    command (Optional, defaults to nothing):
        Help:
            Show this help.
        Default:
            Define the default dice: [start], [end], [step], [times].

    Start (Optional, defaults to 1):
        The lowest number on the dice. Negative numbers are not supported and
        are converted into positive ones.

    End (Optional, defaults to 6):
        The highest number on the dice. Negative numbers are not supported and
        are converted into positive ones.

    Step (Optional, defaults to 1):
        The amount of numbers between the numbers on the sides of the dice.

    Times (Optional, defaults to 1):
        The amount of throws to be done with the given settings, without
        re-defining the default dice.
"""

import random
import time
import sys
import re

d4 = {"Start": 1, "End":   4, "Step":  1, "Times": 1}
d6 = {"Start": 1, "End":   6, "Step":  1, "Times": 1}
d8 = {"Start": 1, "End":   8, "Step":  1, "Times": 1}
d10 = {"Start": 1, "End":  10, "Step":  1, "Times": 1}
d100 = {"Start": 1, "End": 100, "Step":  1, "Times": 1}
d12 = {"Start": 1, "End":  12, "Step":  1, "Times": 1}
d20 = {"Start": 1, "End":  20, "Step":  1, "Times": 1}

defaultSettings = {"Start": 1, 
                   "End":   6,
                   "Step":  1,
                   "Times": 1}

random.seed(time.clock())

def trim(docstring):
    if not docstring:
        return ""

    # Convert tabs to spaces (following the normal Python rules)
    # and split into a list of lines:
    lines = docstring.expandtabs().splitlines()

    # Determine minimum indentation (first line doesn't count):
    indent = sys.maxint
    for line in lines[1:]:
        stripped = line.lstrip()
        if stripped:
            indent = min(indent, len(line) - len(stripped))

    # Remove indentation (first line is special):
    trimmed = [lines[0].strip()]

    if indent < sys.maxint:
        for line in lines[1:]:
            trimmed.append(line[indent:].rstrip())

    # Strip off trailing and leading blank lines:
    while trimmed and not trimmed[-1]:
        trimmed.pop()

    while trimmed and not trimmed[0]:
        trimmed.pop(0)

    # Return a single string:
    return '\n'.join(trimmed)

def parseResponse(response):
    global defaultSettings # Needed to modify global copy of defaultSettings.

    if "help" in response.lower():
        print(__doc__)

    if response.lower() == "exit" or response.lower() == "quit":
        sys.exit(0)

    elif "default" in response.lower():
        arguments = re.findall(r"[\d']+", response)

        length = len(arguments)
        if length < 4:
            x = 4 - (4 - length)
            for i in range(0, 4 - length):
                x = x + 1
                if x == 1:
                    arguments.append(defaultSettings["Start"])
                elif x == 2:
                    arguments.append(defaultSettings["End"])
                elif x == 3:
                    arguments.append(defaultSettings["Step"])
                elif x == 4:
                    arguments.append(defaultSettings["Times"])

        temp = []
        for item in arguments:
            temp.append(int(item))

        defaultSettings = {"Start": temp[0], 
                           "End":   temp[1],
                           "Step":  temp[2],
                           "Times": temp[3]}

    else:
        arguments = re.findall(r"[\d']+", response)

        length = len(arguments)
        if length < 4:
            x = 4 - (4 - length)
            for i in range(0, 4 - length):
                x = x + 1
                if x == 1:
                    arguments.append(defaultSettings["Start"])
                elif x == 2:
                    arguments.append(defaultSettings["End"])
                elif x == 3:
                    arguments.append(defaultSettings["Step"])
                elif x == 4:
                    arguments.append(defaultSettings["Times"])

            temp = []
            for item in arguments:
                temp.append(int(item))

            arguments = temp

    return arguments

def getSettings():
    response = input(">> ")
    if not response:
        settings = defaultSettings
    else:
        arguments = parseResponse(response)

        validArguments = True

        for item in arguments:
            if int(item) < 0:
                validArguments = False
                break

        if validArguments:
            settings = {"Start": arguments[0], 
                        "End":   arguments[1],
                        "Step":  arguments[2],
                        "Times": arguments[3]}
        else:
            print("There was at least one negative value.")

    return settings

def throw(settings):
    start = settings["Start"]
    end =   settings["End"]
    step =  settings["Step"]
    times = settings["Times"]

    if int(start) > int(end):
        temp = start
        start = end
        end = temp
    elif int(start) == int(end):
        print("Given dice is impossible: decreasing start by one.")
        start -= 1

    score = []
    for throw in range(0, int(times)):
        score.append(random.randrange(int(start), int(end), int(step)))

    return score

def main():
    try:
        while True:
            throwSettings = getSettings()
            score = throw(throwSettings)

            n = 0
            for i in score:
                print("You threw: " + str(score[n]))
                n = n + 1

    except SystemExit as e:
        sys.exit(0)
        print(str(e))
    except Exception as e:
        print("Exception: %s.\nPlease try again." % str(e))
        main()
    except:
        print("There was an unexpected exception.")

main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
