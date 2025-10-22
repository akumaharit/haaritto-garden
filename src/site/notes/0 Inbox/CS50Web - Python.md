---
{"dg-publish":true,"permalink":"/0-inbox/cs-50-web-python/","tags":["python","cs50web"],"created":"2025-10-14T22:10:23.331+07:00","updated":"2025-10-18T15:31:12.561+07:00"}
---

### Basic Overview
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
	def __init__(self, input1, input2): #this is called constructor, It automatically runs whenever you create (instantiate) an object from a class. #self is like, to reference to itself
		self.x = input1 #the value will be stored inside the "point" itself, with the properties called "x", and this will be an attribute for the created object from class Point(): 
		self.y = input2
		
p = Point(2,3)
print(p.x)
print(p.y)
```

```python

class Flight():
	def __init__(self, capacity):
		self.capacity = capacity
		self.passengers = []
		
	def add_passenger(self, name):
		if not self.open_seats(): #this is how to express if self.open_seats() == 0 in a more pythonic way
			return False #to indicate that there is some sort of error
		self.passengers.append(name) #this is how to reference to attribute of the self
		return True #to return that everything is successfully
		
	def open_seats(self):
		return self.capacity - len(self.passengers)
		
flight = Flight(3)
people = ["Harry","Ron","Hermione","Ginny"]
for person in people:
	success = flight.add_passenger(person) #call method but also receive the "return" value to the "success" variable
	if success: #check if it success (TRUE) #actually you can just if flight.add_passenger(person)
		print(f"Added {person} to flight successfully.")
	else:
		print(f"No avaliable seats for {person}")
```

### Functional Programming
Decorator is a function that takes a function of input and returns a modified version of the function as output.
In python, function is just another value that can be passed to another function (which in other programming language may cannot) -> This is called functional programming paradigm.
``` python
def announce(f): #this is called DECORATOR, it receives function "f" that modified or add something to the existing function
	def wrapper(): #this is WRAPPER function, it wrap around the actual function
		print("about to run the function...")
		f()
		print("done with the function)
	return wrapper #so it return the new modified function.

@announce #this will add announce decorator to the function
def hello():
	print("Hello, world!")
	
hello() #this will be interpreted like  hello = announce(hello)
```
For example, you can create an authentication checker decorator to check before running a certain function.

### Lambda
``` python
people = [ #one strongest ability of the python is ability to wrap thing just like this one, a list of dictionary
	{"name":"Harry", "house","Grffindor"},
	{"name":"Cho", "house","Ravenclaw"},
	{"name":"Draco", "house","Slytherin"}
]

def f(person):
	return person["name"] #return "name" in the dictionary
people.sort(key=f) #The key parameter tell the python to: Before comparing each item in the list, **apply this function** to extract the value to compare by.”

#You can just write it into one line via Lambda
people.sort(key = lambda person: person["name"])
```


### Catching error
```python
import sys #module to exit the program
try:
	result = 10 / 0
except ZeroDivisionError: #when zerodivisionerror happen
	print("Error: cannot divided by 0.") 
	sys.exit(1) #exit the program with status 1 (1 = something went wrong)
```
To be able to handle error gracefully, use the error exception.