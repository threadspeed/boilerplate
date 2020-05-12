---
title: python script score submissions (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'score submissions'

Functions in program: 
* `def generate_leader_board(evaluation, get_user_profile):`
* `def score_open_submissions(evaluation):`
* `def getParticipants(evaluation):`
* `def getSubmissionStatusBundles(evaluation, status=None, limit=1000, offset=0):`
* `def _getBlockOfSubmissionStatusBundles(evaluation, status=None, limit=20, offset=0):`

Modules used in program: 
* `import synapseclient`
* `import sys`
* `import re`
* `import random`
* `import json`

## python score submissions

Python mysql example: score submissions

```python
##
## Poll for new submissions and score them according to a
## scoring function
######################################################################s
import json
import random
import re
import sys
import synapseclient
from collections import OrderedDict
from synapseclient import Activity, Evaluation, File, Folder, Project
from synapseclient.utils import id_of
from synapseclient.evaluation import SubmissionStatus



def _getBlockOfSubmissionStatusBundles(evaluation, status=None, limit=20, offset=0):
    params = OrderedDict()
    if status:
        params['status'] = status
    params['limit'] = limit
    params['offset'] = offset

    uri = '/evaluation/%s/submission/bundle/all'

    query_string = '&'.join(['%s=%s' % (key,str(value),) for key,value in params.items()])
    if query_string:
        uri += '?' + query_string

    return syn.restGET(uri % id_of(evaluation))


def getSubmissionStatusBundles(evaluation, status=None, limit=1000, offset=0):
    total_number_of_results = sys.maxint
    while (offset < total_number_of_results):
        results = _getBlockOfSubmissionStatusBundles(evaluation, status=status, limit=limit, offset=offset)
        total_number_of_results = results['totalNumberOfResults']
        for submission in results['results']:
            yield submission
        offset += len(results['results'])


def getParticipants(evaluation):
    return syn.restGET('/evaluation/%s/participant?limit=999' % id_of(evaluation))


def score_open_submissions(evaluation):
    i = 0
    for bundle in getSubmissionStatusBundles(evaluation, status='OPEN'):
        submission = bundle['submission']
        status = bundle['submissionStatus']
        entity_bundle = json.loads(submission['entityBundleJSON'])
        entity = entity_bundle['entity']

        print('scoring', entity['id'], entity['name'])

        file_info = syn._downloadFileEntity(entity)

        # if file_info['path'].endswith('.txt'):
        #     with open(file_info['path'], 'r') as f:
        #         guess = [int(x) for x in re.split(r'(?:\s+|[,;:]\s*)', f.read().strip())]

        #     score = nmse(guess, correct_answer)

        #     print(guess, score)

        # else:
        score = 1/(random.lognormvariate(0.0, 1.0) + 1.0)

        status['status'] = 'SCORED'
        status['score'] = score

        status = SubmissionStatus(**status)

        status = syn.store(status)
        print(status)
        i += 1

    return i


class GetUserProfile(object):
    """
    Retrieve and cache user profiles
    """
    def __init__(self, synapse):
        self.profiles = {}
        self.syn = synapse

    def __call__(self, userId):
        if userId in self.profiles:
            return self.profiles[userId]

        profile = self.syn.getUserProfile(userId)
        self.profiles[userId] = profile
        return profile


def generate_leader_board(evaluation, get_user_profile):
    
    bundles = []

    for bundle in getSubmissionStatusBundles(evaluation, status='SCORED'):
        bundles.append(bundle)

    bundles.sort(key=lambda b: b['submissionStatus']['score'])

    lines = ['User Name|Date Submitted|Synapse ID|Name|Score']

    for bundle in bundles:
        submission = bundle['submission']
        status = bundle['submissionStatus']
        entity_bundle = json.loads(submission['entityBundleJSON'])
        entity = entity_bundle['entity']
        profile = get_user_profile(bundle['submission']['userId'])

        lines.append(
            '|'.join([
                '[%s](/#!Profile:%s)' % (profile['displayName'],profile['ownerId'],),
                submission['createdOn'],
                entity['id'],
                entity['name'],
                str(status['score'])]))

    return '\n'.join(lines)



syn = synapseclient.Synapse()
syn.login()


evaluation_id = 1901877
content_host_id = 'syn1901865'
leader_board_wiki_id = '56664'
correct_answer = [7, 12, 23, 44, 52]


evaluation = syn.getEvaluation(evaluation_id)

count = score_open_submissions(evaluation)
print('scored %d submissions!' % count)

if count > 0:
    md = generate_leader_board(evaluation, GetUserProfile(syn))

    print(md)

    wiki_page = syn.getWiki(owner=content_host_id, subpageId=leader_board_wiki_id)
    wiki_page.markdown = md
    wiki_page = syn.store(wiki_page)

    syn.onweb(content_host_id)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
