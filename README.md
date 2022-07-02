# savplatform-python

$ cd <your directory>
$ python3.9 -m venv venv
$ source venv/bin/activate

(venv)$ touch server.py

import json
from webob import Request, Response

def server(environ, start_response):
resp = Response()
response_data = {"message": "Hello from Python"}
resp.body = json.dumps(response_data).encode()
resp.content_type = "application/json"
return resp(environ, start_response)

(venv)$ pip install gunicorn
(venv)$ gunicorn server:server
