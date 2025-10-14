---
{"dg-publish":true,"permalink":"/0-inbox/cs-50-web-python/","tags":["python","cs50web"],"created":"2025-10-14T22:10:23.331+07:00","updated":"2025-10-14T22:51:28.347+07:00"}
---


### Key Takeaway
- No need to declare variable type when declaring variable, which is a main difference from other programming language.
- Variable Types: int, float, str, bool, NoneType
	- None is used to represent for LACK of something or ABSENT of something.
- Tuple is very useful when you want to create something that is ACTUALLY one instead unit, such as a coordinate of X and Y `coordinate = (10.0, 20.0)`, this will allow you to represent as just one variable.
- Data Structures:
	- list: sequence of mutable values
	- tuple: sequence of immutable values -> You cannot add another element to the existing tuple, you have to create a new one!
	- set: collection of **unique** values -> appear exactly once! anddd no sequence so it is called "collection"
	- dict: collection of key-value pairs
- List: (these are in-place method) `.append` `.sort`
- Set:  `s = set()` to create empty set, use `s.add(___)` to add value into the set, use `.remove(___)` to remove value from the set
- `from functions import square` will import function "square" from functions.py, 
  you can also just `import functions` (import entire module) but you need to call the function via `functions.square(i)`
  however it can also be used to import "entire file" from folder "functions", read more [[2 Areas/Programming/Web/Python Package\|Python Package]]

### Object Oriented Programming
Classes is like a template for an object.
All function that will going to operate on themselves (called **methods**) will have to take the first argument called self (which represent the object). 
Refer to [[2 Areas/Programming/Python/Object Oriented Programming (OOP)\|Object Oriented Programming (OOP)]]  for details
```python
class Point():
	def __init__(self, input1, input2):
		self.x = input1 #the value will be stored inside the "point" itself, with the properties called "x", and this will be an attribute for the created object from class Point(): 
		self.y = input2
```

45:39