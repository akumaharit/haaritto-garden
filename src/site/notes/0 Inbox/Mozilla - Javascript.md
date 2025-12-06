---
{"dg-publish":true,"permalink":"/0-inbox/mozilla-javascript/","tags":["javascript"],"created":"2025-11-16T21:41:01.286+07:00","updated":"2025-12-05T12:29:50.818+07:00"}
---

Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript

# Introduction (from Mozilla)
JavaScript is a cross-platform object-oriented scripting language. Standard library of objects such as `Array` , `Map` and `Math` are core library of the JS. Core JS can be extended further for a variety purposes by supplementing it with additional objects; 
- Client-side JS: For example, to supply objects that allow controlling a browser and its DOM
- Server-side JS: For example, allow communication with a database.
Java is a class-based programming language **which is not the same as JavaScript**. JavaScript is standardized at Ecma International. However, use **JavaScript documentation** not the ECMAScript specification one as JavaScript document is the one that describe the aspect of the programming language for the JS programmer.

# Basic Syntax
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