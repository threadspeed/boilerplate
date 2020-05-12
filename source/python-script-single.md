---
title: python script single (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'single'


Modules used in program: 
* `import random`

## python single

Python mysql example: single

```python
# coding: utf-8

# Authorized by: Jiaan Fang <fduodev@gmail.com>
# Blog:          https://fangs.work

# 本gist为文章 https://fangs.work/sqlalchemy-mapper-inheritance/ 的示例代码
# pip install Flask Flask-SQLAlchemy

from flask_sqlalchemy import SQLAlchemy
from flask import Flask
import random

app = Flask(__name__)
db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    user_type = db.Column(db.String(10))

    __mapper_args__ = {
        'polymorphic_identity': 'normal',
        'polymorphic_on': user_type
    }

    def has_permission(self, permission):
        return some_permission_check_logic()

    @classmethod
    def init_for(cls, user_type, **kwargs):
        """根据user_type初始化不同子类的实例"""
        children_classes = {
            x.polymorphic_identity: x.class_
            for x in cls.__mapper__.self_and_descendants
            }
        return children_classes[user_type](**kwargs)



class AdminUser(User):
    __mapper_args__ = {
        'polymorphic_identity': 'admin',
    }

    def has_permission(self, permission):
        return True

if __name__ == '__main__':
    with app.app_context():
        db.create_all()
        users = [User() for i in range(5)]
        print(users)

        admins = [AdminUser() for i in range(5)]
        print(admins)

        random_users = [User(user_type=random.choice(['normal', 'admin'])) for i in range(10)]
        print(random_users)

        for user in random_users:
            db.session.add(user)
        db.session.commit()

        id_list = [o.id for o in random_users]
        del random_users

        random_users_from_db = User.query.filter(User.id.in_(id_list)).all()
        print(random_users_from_db)




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
