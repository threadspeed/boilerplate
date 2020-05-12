---
title: python script concrete (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'concrete'


Modules used in program: 
* `import random`

## python concrete

Python mysql example: concrete

```python
# coding: utf-8

# Authorized by: Jiaan Fang <fduodev@gmail.com>
# Blog:          https://fangs.work

# 本gist为文章 https://fangs.work/sqlalchemy-mapper-inheritance/ 的示例代码
# pip install Flask Flask-SQLAlchemy

from sqlalchemy.ext.declarative import ConcreteBase
from flask_sqlalchemy import SQLAlchemy
from flask import Flask
import random

app = Flask(__name__)
#app.config['SQLALCHEMY_ECHO'] = True
db = SQLAlchemy(app)

class User(ConcreteBase, db.Model):
    __tablename__ = 'user'
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(50))

    __mapper_args__ = {
        'polymorphic_identity': 'normal',
    }

class WechatUser(User):
    __tablename__ = 'user_wechat'

    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(50))  # 注意: 子类必须重新定义字段
    open_id = db.Column(db.String(40))

    __mapper_args__ = {
        'polymorphic_identity': 'wechat',
        'concrete': True
    }

if __name__ == '__main__':
    with app.app_context():
        db.create_all()
        print(User.query)
        print(WechatUser.query)

        user = WechatUser(open_id=1)

        db.session.add(WechatUser())
        db.session.add(User())
        db.session.commit()

        print(User.query.all())
        print(WechatUser.query.all())

        user = User.query.first()




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
