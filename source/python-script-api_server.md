---
title: python script api server (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'api server'

Functions in program: 
* `def set_Info(info):`

Modules used in program: 
* `import random`
* `import pprint`
* `import time`
* `import traceback`
* `import datetime`
* `import os`

## python api server

Python mysql example: api server

```python
##########################################################################################
import os
import datetime
import traceback
import time
import pprint
import random
from flask import Flask, request
from flask.ext.restful import reqparse, abort, Api, Resource

##########################################################################################
def set_Info(info):
	print('type(info)=<%s>' % str(type(info)))
	print('info=%s' % pprint.pformat(info))
	return True
	
##########################################################################################
class Upload(Resource):
	#=====================================================================================
	@staticmethod
	def allowed_file(filename):
		return '.' in filename and \
	           filename.rsplit('.', 1)[1] in ('tgz','tar.gz')
	#=====================================================================================
	def post(self):
		try:
			file = request.files['file']
			if file and self.allowed_file(file.filename):
				filename = os.path.basename(file.filename)
				file.save(os.path.join(app.config['UPLOAD_FOLDER'], filename))
			info = eval(request.form['info'].encode('utf-8'))
			rd = {
				'result':set_Info(info)
			}
			return rd
		except Exception, e:
			rd = {
				'result':False
			}
			return rd

##########################################################################################
if __name__ == '__main__':
	host = '127.0.0.1'
	port = 5001
	g_config.logger.info("Start RestAPI : listen %s:%s" % (host, port))

	app = Flask(__name__)
	# for upload setting
	UPLOAD_FOLDER = '/tmp/upload'
	if not os.path.isdir(UPLOAD_FOLDER):
		os.mkdir(UPLOAD_FOLDER)
	app.config['UPLOAD_FOLDER'] = UPLOAD_FOLDER

	api = Api(app)
	## Actually setup the Api resource routing here
	api.add_resource(UploadVaccine, '/api/Upload')

	from OpenSSL import SSL
	context = SSL.Context(SSL.SSLv3_METHOD)## SSL.Context(SSL.SSLv23_METHOD)
	cert = '/opt/my.crt'
	pkey = '/opt/my.key'
	context.use_privatekey_file(pkey)
	context.use_certificate_file(cert)
	app.run(host=host, port=port, ssl_context=(cert, pkey), threaded=True, debug=True)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
