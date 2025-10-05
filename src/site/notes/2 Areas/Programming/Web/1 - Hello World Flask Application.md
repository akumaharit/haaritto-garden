---
{"dg-publish":true,"permalink":"/2-areas/programming/web/1-hello-world-flask-application/","created":"2025-10-01T21:19:31.244+07:00","updated":"2025-10-05T15:06:43.314+07:00"}
---


`app/__init__.py`
```python
from flask import Flask
app = Flask(__name__)
from app import routes
```
1. Import Flask Class from flask packages
2. create "app" as a instance for Flask class. The first argument is the name of the application's module or package (and mostly we use [[2 Areas/Programming/Web/name variable in Python\|name variable in Python]])
3. import `route.py` module (import at the bottom to avoid mutual references between two files) -> to make sure that the routes module is loaded
`app/route.py`
```python
from app import app

@app.route('/')
@app.route('/index')
def index():
    return "Hello, World!"
```
1. from app import app -> so it gets access to flask app instance, so you can define route to it. 
2. `@app.route` --> @ tell the python that this is the decorator.
3. The `@app.route('/path')` is a decorator provided by flask. It tell that when someone visits this URL path, run the function that comes after this decorator.
4. Why use `app` ? Because app is the flask instance created from `__init.py__` and it has method `.route()` to register URLs -> function
`main.py`
```python
from app import app
```
1. tell the python to from `app` packages, import app (app variable which is instantiated from running `__init__` when using from)

Running your program.
`set FLASK_APP=main.py` -> tell the flask how to import it. (in WSL use `export` instead of `set`)
`flask run` 
*Why you can use flask run in CLI? --> Because pip does not install only the package, but also the command-line tools to declare an entry points. This does not only happen with flask but also jupyter and django.*

Setting port to run
`flask run --port xxxx`

Setting environment variables across terminal (as it aren't remembered across terminal)
`pip install python-dotenv`
Create a file named `.flaskenv` in the top-level directory and add `FLASK_APP=main.py` into it. Then the flask command will automatically look for the `.flaskenv` first and import all variable defined it in.
PS. actually, the [[2 Areas/Programming/Web/python-dotenv\|python-dotenv]] can be used to load the file `.env` extension, but it is also load the `_.flaskenv_` which is a special file for Flask application.