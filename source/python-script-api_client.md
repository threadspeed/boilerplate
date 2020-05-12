---
title: python script api client (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'api client'

Functions in program: 
* `def uploadFile(filename, info, host='localhost', port=5001):`
* `def get_info():`
* `def encode_for_upload (file_path, fields=[]):`

Modules used in program: 
* `import string`
* `import random`
* `import datetime`
* `import urllib`
* `import httplib`
* `import pprint`
* `import unittest`
* `import json`
* `import sys`
* `import os`

## python api client

Python example: api client

```python
##########################################################################################
import os
import sys
import json
import unittest
import pprint
import httplib
import urllib
import datetime
import random
import string

##########################################################################################
def encode_for_upload (file_path, fields=[]):
	BOUNDARY = '----------boundary----------'
	CRLF = '\r\n'
	body = []
	# Add the metadata about the upload first
	for key, value in fields:
		body.extend(
		  ['--' + BOUNDARY,
		   'Content-Disposition: form-data; name="%s"' % key,
		   '',
		   value,
		   ])
	# Now add the file itself
	file_name = os.path.basename(file_path)
	f = open(file_path, 'rb')
	file_content = f.read()
	f.close()
	body.extend(
	  ['--' + BOUNDARY,
	   'Content-Disposition: form-data; name="file"; filename="%s"'
	   % file_name,
	   # The upload server determines the mime-type, no need to set it.
	   'Content-Type: application/octet-stream',
	   '',
	   file_content,
	   ])
	# Finalize the form body
	body.extend(['--' + BOUNDARY + '--', ''])
	return 'multipart/form-data; boundary=%s' % BOUNDARY, CRLF.join(body)

##########################################################################################
def get_info():
	info = {
		'version' : '7.59425',
		'desc': '20150210 설명 정보',
		'filename' : '/tmp/v20150226.tgz',
	}
	return info
##########################################################################################
def uploadFile(filename, info, host='localhost', port=5001):
	#=====================================================================================
	if not os.path.exists(filename):
		raise IOError('Cannot open for file <%s>' % filename)
	fields = (('info', str(info)),)
	content_type, body = encode_for_upload(filename, fields=fields)
	headers = { 'Content-Type': content_type }
	conn = httplib.HTTPSConnection(host=host, port=port)
	conn.request('POST', '/api/Upload', body, headers)
	response = conn.getresponse()
	# print(response.status, response.reason)
	data = response.read()
	conn.close()
	rdict = json.loads(data)
	return rdict

##########################################################################################
if __name__ == '__main__':
	s_ts = datetime.datetime.now()
	filename = '/tmp/v20150226.tgz'
	info = get_info()
	r = uploadVaccine(filename, vaccine_info, TU.host, TU.port)
	_r = r['result']
	e_ts = datetime.datetime.now()
	print('result of upload=<%s> takes [%s]' % (_r, e_ts-s_ts))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
