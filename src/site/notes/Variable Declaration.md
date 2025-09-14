---
{"dg-publish":true,"permalink":"/variable-declaration/","created":"2025-09-14T21:39:04.069+07:00","updated":"2025-09-14T21:41:13.757+07:00"}
---

### Variable Declaration
- Use `DATA <name> TYPE <type> VALUE <val>` to define the variable
	- add VALUE if you wanted to assign the value to that variable when declaring it.
	- In case if the number is decimal, you have to put quotes (' ') so it don't interpret the period ( . ) as a termination.
- `DATA d2 LIKE d1`, will make D2 with the same data type as d1 **WARNING, this does not assign the variable's value, use "MOVE" for the assign.**
	- you can also declare variable with the same data type of the field in the table `DATA d2 LIKE <tablename>-<fieldname>`
- `MOVE d2 TO d1`, this will assign d2 value to the d1. (d1 = d2)
- **in SAP the variable is also called "FIELD' if it is from table**

- There are three types of the variable, **static variable**, **references variable** and **system variables** #tolearn

**Literals** are unnamed data objects that you create within the source code of a program.

**Constants** are named data objects created statically by using declarative statements. The value assigned to constants cant be changed during the execution of the program.
- DATA is almost the same as CONSTANTS (same syntax too!) except that, you cannot change the value of the CONSTANTS //it is a **must** to use also include `VALUE` during the constant declaration.
- You cannot define constant for, XSTRING, References, Internal table, structure containing internal tables