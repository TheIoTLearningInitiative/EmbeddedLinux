# Python

- [Five trivial things every python programmer should work with](https://impythonist.wordpress.com/2015/10/11/five-trivial-things-every-python-programmer-should-work-with/)

## Flask

> Flask is a microframework for Python based on Werkzeug, Jinja 2 and good intentions.

- [Flask Homepage](http://flask.pocoo.org/)

```sh
    root@edison:~# apt-get install python-flask
    root@edison:~# pip install Flask
    root@edison:~# nano myflask.py 
```

```Python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000, debug=True, threaded=True)
```

```sh
    root@edison:~# python myflask.py
    * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
    * Restarting with stat
    192.168.1.73 - - [18/Oct/2015 16:34:56] "GET / HTTP/1.1" 200 -
    192.168.1.73 - - [18/Oct/2015 16:34:56] "GET /favicon.ico HTTP/1.1" 404 -
    192.168.1.73 - - [18/Oct/2015 16:34:56] "GET /favicon.ico HTTP/1.1" 404 -
```

