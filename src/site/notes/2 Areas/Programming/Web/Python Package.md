---
{"dg-publish":true,"permalink":"/2-areas/programming/web/python-package/","created":"2025-10-01T21:09:31.960+07:00","updated":"2025-10-01T21:11:10.313+07:00"}
---

In python, **package** is a way to organize and group related modules.
Module = single .py file
Package is a folder that contain one or more module and usually `__init__.py` which tell the python that this folder should be treated as apackage.

When you import using `from math_tools import algebra, geometry` it is telling the python to import from folder `math_tools` and the file `algebra.py` and `geometry.py`. The `__init__.py` will also be executed.