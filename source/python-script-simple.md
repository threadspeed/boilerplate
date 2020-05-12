---
title: python script simple (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simple'

Functions in program: 
* `def main():`
* `def confirm_fail(request):`
* `def confirm_success(request):`
* `def predicate_maker(keyword):`
* `def pre_confirm(request):`
* `def register(request):`
* `def report_renderer_maker(info):`

## python simple

Python example: simple

```python
from pyramid.config import Configurator
from wsgiref.simple_server import make_server
from pyramid.view import view_config
from pyramid.httpexceptions import HTTPFound

from zope.interface import Interface
from zope.interface import implements

class IConfirmContext(Interface):
    pass
class ConfirmSuccess(Exception):
    implements(IConfirmContext)

class ConfirmFail(Exception):
    implements(IConfirmContext)


class Resource(object):
    def __init__(self, request):
        self.request = request
        self._result = None

    def get_random(self): 
        """ random number (cached in same request)
        """
        import random
        if self._result is None:
            self._result =  random.random()
        return self._result

    def choice(self):
        import random
        return random.choice(["report", "json"])

def report_renderer_maker(info):
    def _make_report(value):
        return """\
        <xml>
          <status>%(status)s</status>
          <result>%(n)f</result>
        </xml>
        """ % value
    def _render(value, system):
        request = system.get("request")
        if request is not None:
            return _make_report(value)
    return _render

@view_config(route_name="register")
def register(request):
    _type = request.context.choice()
    return HTTPFound(location=request.route_url("confirm", type=_type))
        
@view_config(route_name="confirm")
def pre_confirm(request):
    n = request.context.get_random()
    if n > 0.5:
        raise ConfirmSuccess()
    else:
        raise ConfirmFail()

def predicate_maker(keyword):
    def _predicate(info, request):
        return keyword == request.matchdict["type"]
    return _predicate
        

@view_config(route_name="confirm", context=ConfirmSuccess,
             renderer="foo.report", custom_predicates=(predicate_maker("report"), ))
@view_config(route_name="confirm", context=ConfirmSuccess,
             renderer="json", custom_predicates=(predicate_maker("json"), ))
def confirm_success(request):
    n = request.context.get_random()
    return dict(status="success", n=n)


@view_config(route_name="confirm", context=ConfirmFail,
             renderer="foo.report", custom_predicates=(predicate_maker("report"), ))
@view_config(route_name="confirm", context=ConfirmFail,
             renderer="json", custom_predicates=(predicate_maker("json"), ))
def confirm_fail(request):
    n = request.context.get_random()
    return dict(status="fail", n=n)

def main():
    """ This function returns a Pyramid WSGI application.
    """
    # configuration settings
    settings = {"mako_directories": "templates"}
    # configuration setup

    config = Configurator(settings=settings)
    config.add_renderer(".report", report_renderer_maker)

    config.add_route("register", "/register", factory=Resource)
    config.add_route("confirm", "/confirm/{type}", factory=Resource)
    config.scan()
    # config.add_static_view('static', '', cache_max_age=3600)
    app = config.make_wsgi_app()
    server = make_server('0.0.0.0', 6543, app)
    server.serve_forever()

if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
