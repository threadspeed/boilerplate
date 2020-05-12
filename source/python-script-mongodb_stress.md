---
title: python script mongodb stress (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mongodb stress'

Functions in program: 
* `def has_live_threads(threads):`

Modules used in program: 
* `import threading`
* `import datetime`
* `import random`
* `import time`
* `import md5`
* `import pymongo`

## python mongodb stress

Python mysql example: mongodb stress

```python
import pymongo
import md5
import time
import random
import datetime
import threading

host = 'host:port'

ITEM_COUNT = 1000000

# セッタースレッド
class SetterThread(threading.Thread):
    def __init__(self, name, timer=60):
        threading.Thread.__init__(self)
        self.name = name    # スレッド名 
        self.timer = timer  # 負荷をかけたい時間(秒)
        self.kill_received = False  # スレッド停止フラグ
        self.conn = pymongo.Connection([host])
        self.db = self.conn.test
        
    def run(self):
        start = datetime.datetime.now()  # 開始時刻
        while not self.kill_received:
            now = datetime.datetime.now()
            if (now - start) > datetime.timedelta(0, self.timer):
                break
            key = md5.new(str(random.randint(1, ITEM_COUNT-1))).hexdigest()
            val = key * 4
            self.db.mycoll.save({'_id': key, 'val': val}, safe=True)
            time.sleep(0.01)
            
# ゲッタースレッド
class GetterThread(threading.Thread):
    def __init__(self, name, timer=60):
        threading.Thread.__init__(self)
        self.name = name    # スレッド名 
        self.timer = timer  # 負荷をかけたい時間(秒)
        self.kill_received = False  # スレッド停止フラグ
        self.conn = pymongo.Connection([host])
        self.db = self.conn.test
        
    def run(self):
        start = datetime.datetime.now()  # 開始時刻
        while not self.kill_received:
            now = datetime.datetime.now()
            if (now - start) > datetime.timedelta(0, self.timer):
                break
            key = md5.new(str(random.randint(1, ITEM_COUNT-1))).hexdigest()
            self.db.mycoll.find_one(key)
            time.sleep(0.01)
            
def has_live_threads(threads):
    return True in [t.isAlive() for t in threads]

from optparse import OptionParser
if __name__ == "__main__":
    parser = OptionParser()
    parser.add_option("-n", dest="num", type="int",
                      help="number of threads")
    parser.add_option("-t", dest="time", type="int",
                      help="duration time", default="10")
    parser.add_option("-s", dest="setter", action="store_true", default=False)
    (options, args) = parser.parse_args()

    # スレッド生成、開始
    threads = []
    for i in range(0, options.num):
        name = "Thread-" + str(i)
        if options.setter:
            thread = SetterThread(name, options.time)
        else:
            thread = GetterThread(name, options.time)
        print("Starting " + name)
        thread.start()
        threads.append(thread)
        #time.sleep(0.1)
    
    # 生きているスレッドがある間、繰り返し
    while has_live_threads(threads):
        try:
            # timeout 1秒指定でスレッドの終了同期をとる
            [t.join(1) for t in threads
             if t is not None and t.isAlive()]
        except KeyboardInterrupt:
            # Ctrl-C が押されたら、スレッド停止フラグを立てる
            print("Sending kill to threads...")
            for t in threads:
                t.kill_received = True

    print("Exited")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
