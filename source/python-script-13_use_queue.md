---
title: python script 13 use queue (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '13 use queue'

Functions in program: 
* `def downloadEnclosures(i, q):`

Modules used in program: 
* `import time`

## python 13 use queue

Python mysql example: 13 use queue

```python
# -*- coding:utf-8 -*-

# システムモジュール
from Queue import Queue
from threading import Thread
import time

# グローバル変数をセット
num_fetch_threads = 2
enclosure_queue = Queue()

# 実際のアプリではハードコーディングしない...
feed_urls = [ 'http://www.castsampler.com/cast/feed/rss/guest',
             ]


def downloadEnclosures(i, q):
    """This is the worker thread function.
    It processes items in the queue one after
    another.  These daemon threads go into an
    infinite loop, and only exit when
    the main thread ends.
    """
    while True:
        print('%s: Looking for the next enclosure' % i)
        url = q.get()
        print('%s: Downloading:' % i, url)
        # URL から実際にダウンロードせずに sleep で欺く
        time.sleep(i + 2)
        q.task_done()


# エンクロージャを取得してスレッドを設定する
for i in range(num_fetch_threads):
    worker = Thread(target=downloadEnclosures, args=(i, enclosure_queue,))
    worker.setDaemon(True)
    worker.start()


class feedparser:
    @classmethod
    def parse(cls, url, agent=None):
        return {"entries": [{"enclosures": [{"url": url}, {"url": "http://example.com"}]}]}

# フィードをダウンロードしてキューへエンクロージャの URL を追加する
for url in feed_urls:
    response = feedparser.parse(url, agent='fetch_podcasts.py')
    for entry in response['entries']:
        for enclosure in entry.get('enclosures', []):
            print('Queuing:', enclosure['url'])
            enclosure_queue.put(enclosure['url'])

# 全てのダウンロード処理が完了したことを表す、キューが空になるまで待つ
print('*** Main thread waiting')
enclosure_queue.join()
print('*** Done')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
