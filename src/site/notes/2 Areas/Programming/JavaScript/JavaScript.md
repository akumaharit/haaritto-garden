---
{"dg-publish":true,"permalink":"/2-areas/programming/java-script/java-script/","tags":["javascript"],"created":"2024-07-28T22:01:55.159+07:00","updated":"2025-12-05T12:32:06.618+07:00"}
---

# Introduction (from Mozilla) [^1]
JavaScript is a cross-platform object-oriented scripting language. Standard library of objects such as `Array` , `Map` and `Math` are core library of the JS. Core JS can be extended further for a variety purposes by supplementing it with additional objects; 
- Client-side JS: For example, to supply objects that allow controlling a browser and its DOM
- Server-side JS: For example, allow communication with a database.
Java is a class-based programming language **which is not the same as JavaScript**. JavaScript is standardized at Ecma International. However, use **JavaScript documentation** not the ECMAScript specification one as JavaScript document is the one that describe the aspect of the programming language for the JS programmer.

## Basic Syntax
JavaScript is **case-sensitive** and use **Unicode** character set.
Instructions are called **statements** and are separated by semicolons (;)
## Comment
```js
// a one line comment

/* this is a longer,
 * multi-line comment
 */
```
Use backslash \ to prevent a comment from being break `*/` ---> `*\/` 
Some file may has comment such as `#!/USER/BIN/ENV NODE` -> these are **hashbang comment** syntax
## Declarations
`var` = declare variable (can be both **local** and **global** depending on execution context) -> global context OR function context if the code is part of a function.
`let` = declare variable, **block** scoped, 
`const` = declare variable, **block**-scoped, **read only** name constant
You can use **destructuring syntax** to declare variables to unpack values such as
```js
const foo = { bar: 'hello world', baz: 10 }; 
const { bar } = foo;
// will result in variable "bar" holding value of "hello world"
```
The syntax for object destructuring flips this pattern for reading: **the curly braces are placed on the left side of the assignment operator to tell the engine that variables should be created based on the property names found inside the object on the right side.**
### Declaration vs Initialization
`let x = 42` the `let x` = declaration and 42 is initialization (which is optional for `var` and `let` BUT REQUIRED FOR `const`)
if variables were declared without initializer, the assign value is `undefined`

### Scope
A variable may belong to one of the following scopes:
- Global scope: The default scope for all code running in script mode.
- Module scope: The scope for code running in module mode.
- Function scope: The scope created with a function.
In addition, variables declared with `let` or `const` can belong to an additional scope:
- Block scope: The scope created with a pair of curly braces (a block)

### `var` is **hoisted**
`var` will always be **declared** and **initialized** with `undefined` even if it is inside function or local scope. The variable can be accessed anywhere BEFORE its value assignment (but will always be `undefined` if you access it before the assignment.)
Because of hoisting, `var` should be placed near the top of the function or the scope to increase clarity of the code.

# JavaScript Basic [^2]
The syntax is actually the "structure" not the "word". It is the `(), ;` of the coding language.
The word in the programming language is an "environmental" jargon.

JavaScript use ASI (Automatic Semicolon Insertion) to automatically insert `;` when the parser thinks you meant to end a statement. However, this sometimes can break your code if it misinterpret! So it is always a good practice to add `;` by the end of your statement.

The **Web Browser** is just one of JavaScript environment. **NodeJS** and **MongoDB** is also the JavaScript environment.
`document.title` / `document.body.style.backgroundColor` these are example of the jargon used in web browser environment.
### JavaScript Function
``` javascript
function greet(parameter){
// this is the function body.
	alert("Hello, my name is." + parameter);	
};

greet('Harit');
// The 'Harit' is an argument for the greet() function.

```
### JavaScript Object
Advantage of using the object is it is easier to access, to communicate to other devs.
When you create a function inside the object, you don't have to begin the statement with `function`
The `{}` can be interpret as "inside this object" or "inside the body of this function." Its depend on the context being used.
You can also nest object inside the object.
```javascript
let cat = { // this is "object" datatype, and it can store the property inside it.
	name: "Fluffy", // these are "property"
	age: 4,
	meow() {
		alert("Meooooow") //this is how to create a function inside the object. (we refer to it as a method since it live inside the object.)
	}
}

cat.name // to access the property inside the object.
cat.meow()
```
The **Web Browser** environment has a pre-built objects included e.g. `document` which represent a webpage as a whole.
```javascript
document.addEventListener("click",myAmazingFunction) // click, scroll, keydown | method or function to run when event happens.
//No need to add the () behind the function because we are just passing the REFERENCE of what function, not to make it run!
```
Note: some data type has its own abilities or methods that are provided by the JavaScript language itself and you don't have to create it. (such as Array, String.)

### JavaScript Array
Array is a "A Collection of items" 
```js
let myFavoriteNumbers = [9, 2, 8, 3, 7, 4]
let myWords = ["red", "orange", "blue"]
let myPets = [{name: "Meow", species: "cat"}, {name: "Meow2", species: "cat2"}] // this is an array of object.

myWords.push("green") //add value into the array and return new legnth of the array.
console.log(myWords)

myWords.splice() //Array in JS is zero-indexed, to remove "orange" in this one you can use (1,1)
//Starting from index 1 and remove 1 item.
console.log(myWords)

console.log(myFavoriteNumbers[2]) //will return 8
console.log(myPets[1].species) //will return the second object, and the property value of species
```
`.push()` and return the length of the array
`.pop()` and then return the removed variable
`.length`

`.foreach()` will run a function for each items inside the array. This is a [[#JavaScript Higher-Order Functions|higher-order function]] because it accept the function as a argument.
```js
let myColors = ['red','orange','yellow']
myColors.forEach(sayColors)
function sayColors(x){
  document.write("Hello, this is the color " + x);
}
```

`.map()` it does not mutate the array, but return a new value (brand new array)
```js
let pets = [
  {name: "Meowsalot", species: "cat", age: 2},
  {name: "Barskalot", species: "dog", age: 3},
  {name: "Purrsaloud", species: "cat", age: 9}
]

console.log(pets.push({name: "Harit", species: "human", age: 25}))
let ourTest = pets.map(nameOnly)

function nameOnly(){
  return "hello"
}

console.log(ourTest) //this will return ["hello", "hello", "hello", "hello"] because this function always return "hello" for each item in the array.
```
```js
let pets = [
  {name: "Meowsalot", species: "cat", age: 2},
  {name: "Barskalot", species: "dog", age: 3},
  {name: "Purrsaloud", species: "cat", age: 9}
]

console.log(pets.push({name: "Harit", species: "human", age: 25}))
let ourTest = pets.map(nameOnly)

function nameOnly(x){ //the name is actually not matter, but it will be the variable that receive each object inside pets.
  return x.name //to return the name property of each object inside pets
}

console.log(ourTest) //this will return ["hello", "hello", "hello", "hello"] because this function always return "hello" for each item in the array.
```

`.filter()` it does not mutate the array, but return a new value (brand new array) (based on the return boolean, if true that items will be returned, if false, that items will not be returned)
Quick note: you can use `.filter().filter()` (same for other methods!) to use method for the returned object from the first method's return.
``` js
let pets = [
  {name: "Meowsalot", species: "cat", age: 2},
  {name: "Barskalot", species: "dog", age: 3},
  {name: "Purrsaloud", species: "cat" , age: 9}
]

function onlyDogs(x){
  return x.species == "dog"
} 

let dogs = pets.filter(onlyDogs)


console.log(dogs)
```

### JavaScript Decisions (if-else-loop)
```js
let strawberrycount = 20;

if (strawberrycount){ // <<< anything higher than 0 will be interpreted as "true" However, 0 will be false
  document.write("Congrats") 
}
else
{
  document.write("Sorry we don't accept less than 9 strawberries")
}
```

```js
let strawberrycount = 0;

while (strawberrycount <= 1000){
  document.write("There are currently " + strawberrycount + " strawberries")
  strawberrycount = strawberrycount + 1 // you can also increment using ++
}
```

### JavaScript Higher-Order Functions
This can be separated into two types, **function that accept function as argument** and **function that return a function**
```js
document.addEventListener("click", ourAmazingFunction) //this is higher-order function that receive the function as an argument, and this is what make JS special because not all language allow accepting function as an argument.


function doubleMe(x){ //this is not a higher-order function.
	return x * 2
}

function createMultiplier(multiplier){ //this is a higher-order function because it return a function. this is also special in JS because other language may not allow doing such a thing like this one.
	return function(x){
		return x * multiplier
	}
}
let doubleMe = createMultiplier(3);
```

### JavaScript Returning vs Mutating
Some function mutate and return the value `.pop()`
Some function does not mutate and return the value (`.map()`)
```js
let pets = [
  {name: "Meowsalot", species: "cat", age: 2},
  {name: "Barskalot", species: "dog", age: 3},
  {name: "Purrsaloud", species: "cat", age: 9}
]

console.log(pets.push({name: "Harit", species: "human", age: 25})) //this returned 4
console.log(pets) //this also returned the array with the new object inside.

```

### JavaScript Scope & Context





# ของเก่าจากไหนไม่รู้
---
String is **immutable**, but you can reassign the variable to new value.

If you declare variable without providing the value = it is *uninitialized*
**const** variable cannot be reassigned, and cannot be uninitialized

Primitive data = such as string and number,  it is complex and **can only hold one value** at a time
Non-primitive data, can hold a series of values

Array is **mutable**, you can change the value at an index directly

Error that occured because of ... in a language with zero-index position is called *off-by-one* error


### String
- .repeat() to repeat the string value for a certain time
### Loop
- `for ("iterator"; "condition"; "iteration") {}`
- You can also use `for(const element of array){}` to loop for the element in array, we use `const` because the variable only exists for a single iteration, not during the entire loop.


[^1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript

[^2]: Mostly were from: https://www.udemy.com/course/learn-javascript-full-stack-from-scratch/
