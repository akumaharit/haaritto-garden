---
{"dg-publish":true,"permalink":"/2-areas/programming/web/python-dotenv/","created":"2025-10-01T21:51:37.621+07:00","updated":"2025-10-01T21:53:06.747+07:00"}
---


Can be used to setup environment variable.
Use the file `.env`
for flask, you can use `.flaskenv` which will be used when `flask` command is used in the command prompt.

`.env`
```
MY_KEY = 12345
```

`main.py`
```python
from python-dotenv import load_dotenv
import os

api_key = os.getenv("MY_KEY")
 
``