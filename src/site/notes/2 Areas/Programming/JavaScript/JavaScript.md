---
{"dg-publish":true,"permalink":"/2-areas/programming/java-script/java-script/","tags":["javascript"],"created":"2024-07-28T22:01:55.159+07:00","updated":"2026-01-12T22:35:39.073+07:00"}
---

# Introduction (from Mozilla) [^1]
{ #634010}


JavaScript is a cross-platform object-oriented scripting language. Standard library of objects such as `Array` , `Map` and `Math` are core library of the JS. Core JS can be extended further for a variety purposes by supplementing it with additional objects; 
- Client-side JS: For example, to supply objects that allow controlling a browser and its DOM
- Server-side JS: For example, allow communication with a database.
Java is a class-based programming language **which is not the same as JavaScript**. JavaScript is standardized at Ecma International. However, use **JavaScript documentation** not the ECMAScript specification one as JavaScript document is the one that describe the aspect of the programming language for the JS programmer.

Add JS script in HTML via `<script src="script.js" defer></script>`
- `defer` tells the browser to download this script when parsing HTML but execute only after the HTML is fully parsed (to ensures **DOM elements** exist when the script run.)

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
{ #eeea9c}


`var` = declare variable (can be both **function** and **global** depending on execution context) -> global context OR function context if the code is part of a function.
`let` = declare variable, **block** scoped, 
`const` = declare variable, **block**-scoped, **read only** name constant
You can use **destructuring syntax** to declare variables to unpack values such as
```js
const foo = { bar: 'hello world', baz: 10 }; 
const { bar } = foo;
// will result in variable "bar" holding value of "hello world"
```
The syntax for object destructuring flips this pattern for reading: **the curly braces are placed on the left side of the assignment operator to tell the engine that variables should be created based on the property names found inside the object on the right side.**

If you wanted to go deeper,
let and const is actually hoisted but it is just in The Temporal Dead Zone (TDZ) causing the **Reference Error**

**Memorization:** 
var ignores {}
- if declared inside function = it is function-scoped
- it declared outside (global) = it is global-scoped
let and const respect {}
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

console.log(ourTest) //this will return ["Meowsalot", "Barskalot", "Purrsaloud", "Harit"] because this function always return "hello" for each item in the array.
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
#### Scope -> Focus about Variables
The code will always check for the scope inward first before moving outward. (inside code can reach outwards for variable, but outside code cannot reach inside for variable.) The variable in each scope, is independent from the same variable in DIFFERENT scope.
`let` is a local scope (block scope.) **Block scope is introduced 4-5 years ago in JS, and is popular because all other language use this one.**
`var` is a function scope but can be global if defined in the global scope.
Read more about scope at [[#^eeea9c| Declarations]]

#### Context -> Focus about Objects
{ #630f31}

`this` keyword point toward the object that is executing the function.
```js
let john = {
  firstName: "John",
  lastName: "Doe",
  driveCar(){
	function imafunctionnotamethod(){
		console.log(this)
	}
	imafunctionnotamethod() //When you run this one inside the object, the JS understand that it is being run in a global context (because it is not a method of any object!) so the this keyword point to the global root (which is window for webbrowser)
    console.log(this.firstName)
  }
}

john.drivecar() // When you run this, the this keyword understand that it has to point toward "john" object.

function breathe(){
	console.log(this.firstName + " just inhaled and exhaled")
}
breathe.call(john) //this is a method of a function object, which allow you to make the john object, call the function breathe() as its method.
```
This also work with the button in HTML
`<button onclick = "deleteItem(this)">Button</button>` the `this` will refer to this button element.


### Miscellaneous Info

#### Ternary Operator
```js
// The format
condition ? valueIfTrue : valueIfFalse

// Example
nucleotide === "T" ? "U" : nucleotide
// It actually mean
if (nucleotide === "T") {
  return "U"
} else {
  return nucleotide
}

```
#### Anonymous Function
This is how you create annonymous function, because it doesn't have a name.
```js
document.addEventListener("click", function(){
	alert("Thank you for clicking")
})
```
#### Arrow Functions
Remove the word function and keep the (), include arrow between () and {
```js
document.addEventListener("click", () => {
	alert("Thank you for clicking")
})

//You can change it into just one line.
document.addEventListener("click", () => {alert("Thank you for clicking")})
```
The feature of the arrow function is, it will automatically return what is behind  => 
and {} is acutally not required **IF IT IS IN ONE LINE**
And the () is not needed if it is 1 parameters ( the `()` is only needed if it is multiple parameters or 0 parameter)
```js
let myNumbers = [10, 500, 2000]

let doubledNumbers = myNumbers.map(function(x){ 
	return x * 2
})
console.log(doubledNumbers)

//IF you turn it into the arrow function it will be like this
let doubledNumbers = myNumbers.map((x) => { return x * 2})
//IT ACTUALLY EQUIVALENCE TO THIS ONE
let doubledNumbers = myNumbers.map(x =>  x * 2)
```
You can declare a function just like a variable, and it point to the context difference than [[#^630f31|declaring a function in an object and call it.]]
```js
let imAFunctionNotaMethod = () => console.log(this)
imAFunctionNotaMethod()
//when you call this function, the 'this' keyword will point in your current context. IT WILL NOT ALWAYS POINT TO THE GLOBAL
```

#### Function Hoisting
Normally, you have to declare a function first before you call the function (just like a variable.)
But in JavaScript, the function is **hoisted**
```javascript
cool()

function cool(){
	console.log("This is super cool")
}
```
However, if you create a function as a anonymous function it will not hoist.
```js
cool()

let cool = function(){
	console.log("Hey")
}
```

#### Template Literals
```js
let myname = "Brad"
console.log(`Hello, my name is ${myname} and the sky is blue.`)
//Inside {} you could do anything in JS such as ${2+2}
```
This also allow you to write multiple line of code without the need of `\n `

#### Semicolons
As stated earlier in [[#^634010| Introduction Part]], the JavaScript automatically insert semicolons



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
- ![Pasted image 20260112223537.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020260112223537.png)
- You can also use `for(const element of array){}` to loop for the element in array, we use `const` because the variable only exists for a single iteration, not during the entire loop.


[^1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript

[^2]: Mostly were from: https://www.udemy.com/course/learn-javascript-full-stack-from-scratch/
