---
{"dg-publish":true,"permalink":"/2-areas/programming/web/name-variable-in-python/","created":"2025-10-01T21:14:03.853+07:00","updated":"2025-10-05T15:06:59.849+07:00"}
---

`__name__` is a special variable that will be created when the python is being run.
It will store the name of the module which it is currently used.

If the source file is executed as the main program, the interpreter sets the __name__ variable to have a value "__main__". If this file is being imported from another module, __name__ will be set to the module's name. `__name__` **is a built-in variable which evaluates to the name of the current module.**