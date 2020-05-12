---
title: python script django code (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'django code'


## python django code

Python mysql example: django code

```python
from rest_framework.renderers import JSONRenderer
from rest_framework.response import Response
from rest_framework.views import APIView

class RandNumView(APIView):
   """ 
    A view that returns the count of active users in JSON.
    """
    renderer_classes = (JSONRenderer, )

    def get(self, request, format=None):
        # from random import random
        import random
        rand = random.randint(0, 100)
        content = {'random_num': rand}
        return Response(content)

   # def put(self, request, format=None):

----------------------urls.py   
   
from django.conf.urls import url 
from rest_framework.urlpatterns import format_suffix_patterns
from django.contrib import admin
from tutorial import views

urlpatterns = [ 
    url(r'^admin/', admin.site.urls),
    url(r'^rand/$', views.RandNumView.as_view()),
    url(r'^myapp/', include('myapp.urls')),
]
urlpatterns = format_suffix_patterns(urlpatterns)


------------------- myapp/urls.py
from django.conf.urls import url 
from . import views

urlpatterns = patterns('',
    url(r'^form$',
        views.post_form_upload),

)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
