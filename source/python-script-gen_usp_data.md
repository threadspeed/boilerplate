---
title: python script gen usp data (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gen usp data'

Functions in program: 
* `def main():`
* `def delete_old_files(dir_to_be_deleted):`
* `def write_usp_to_file(usps):`
* `def make_filename():`
* `def make_USPs():`

Modules used in program: 
* `import thread`
* `import os`
* `import time`
* `import random`
* `import sys`

## python gen usp data

Python example: gen usp data

```python
# -*- coding: utf-8 -*-

import sys
import random
from datetime import datetime
import time
import os
import thread
# from random import random

out_dir = 'sp_in/'

class USPTester(object):
	def __init__(self, arg):
		super(USPTester, self).__init__()
		self.arg = arg
		self.id = self.arg

		self.lat = round(random.uniform(2100, 4210), 4)
		self.long = round(random.uniform(6400, 9999), 4)
		

	def simulate(self):
		self.wind_direction = round(random.uniform(100,300), 1)
		self.wind_speed = round(random.uniform(10, 90), 1)
		self.no2 = random.randint(151, 360)
		self.lpg = random.randint(151, 360)

	def tostring(self):
		self.simulate()
		return '{0},{1},{2},{3},{4},{5}\r\n'.format(
								self.id, 
								self.wind_direction, 
								str(self.wind_speed).zfill(5),
								self.lpg,
								self.lat,
								self.long
								)


def make_USPs():
	usps = []
	# 센서 데이터 600 개 정도 생성, (~다른 업체에서 보내는 id 랑 중복안되게 100 부터 시작.~)
	usps.append(USPTester("sp-02"))
	for i in range(1, 600):
		usps.append(USPTester("usp-" + str(i).zfill(3)))
	return usps

def make_filename():
	dt = datetime.now()
	# sp_20141021010100.log
	return out_dir + dt.strftime("sp_%Y%m%d%H%M%S.log")

def write_usp_to_file(usps):
	filename = make_filename()
	with open(filename, 'wb') as f:
		# csv 에 헤더 정보 넣기 
		f.write("(u)sp_id,wind_direction,wind_speed,no2,lpg,lat,long\r\n")
		for u in usps:
			f.write(u.tostring())

# 1시간 마다 돌면서, 2일 이전 데이터 지움
def delete_old_files(dir_to_be_deleted):
	while True:
		print('{} delete old files.'.format(datetime.now()))
		now = time.time()
		path = os.path.abspath(dir_to_be_deleted)
		for f in os.listdir(path):
			f = os.path.join(path, f)
			if os.stat(f).st_mtime < now - 2 * 86400:	# 2일 이전꺼
				if os.path.isfile(f):
					os.remove(f)
		# break
		time.sleep(60*60)	# 1시간


def main():
	try:
		os.mkdir(out_dir)	
	except Exception, e:
		pass

	thread.start_new_thread(delete_old_files, (out_dir,))		
	
	# 가상 usp 장비들 생성
	usps = make_USPs();

	while 1:
		# out_dir 에 장비들 정보를 write 하기
		write_usp_to_file(usps)
		time.sleep(1)
		sys.stdout.write('.')
		# break

if __name__ == '__main__':
	main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
