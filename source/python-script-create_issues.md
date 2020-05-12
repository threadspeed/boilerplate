---
title: python script create issues (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'create issues'


Modules used in program: 
* `import random`

## python create issues

Python mysql example: create issues

```python
import random

from github import Github

from main import BootcampSpot

ACCESS_TOKEN = os.environ.get("ACCESS_TOKEN")

g = Github(ACCESS_TOKEN)
bootcamp_spot = BootcampSpot()

repo = g.get_repo("DustinAlandzes/Full-Stack-Web-Development-Anki-Deck")

open_issues = list(repo.get_issues(state='open'))
closed_issues = list(repo.get_issues(state='closed'))
issues = [issue.title for issue in open_issues]
issues.extend([issue.title for issue in closed_issues])

assignments = bootcamp_spot.get_assignments()
for assignment in assignments:
    note_txt = f"{assignment.get('studentName')} - {assignment.get('assignmentTitle')}"

    not_added_already = note_txt not in issues
    is_submitted = assignment.get('submitted')
    not_graded = not assignment.get('grade')
    not_a_milestone = not 'Milestone' in assignment.get('assignmentTitle')

    if all([not_added_already, is_submitted, not_graded, not_a_milestone]):
        # choose randomly between Dustin and David
        assign_to = random.choice(['DustinAlandzes', None])
        if assign_to:
            repo.create_issue(title=note_txt, assignee=assign_to)
        else:
            repo.create_issue(title=note_txt)
        issues.append(note_txt)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
