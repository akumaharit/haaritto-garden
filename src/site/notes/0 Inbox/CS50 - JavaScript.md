---
{"dg-publish":true,"permalink":"/0-inbox/cs-50-java-script/","tags":["cs50web","javascript"],"created":"2025-10-27T21:42:56.775+07:00","updated":"2025-10-27T22:17:16.628+07:00"}
---

DOM = Document Object Model that represent the webpage that the user is looking at.
JavaScript allow you to manipulate DOM
`<script> </script>` tell that inside = javascript code.
JavaScript biggest pro in web dev: **event driven programming**
Anything that user does, can be though as an event, and js can handle/event listener to that event and then do something.

## Defining function and calling function via `<button>`
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Hello</title>
        <script>
            function hello(){
                alert("Hello, World!");
            }
        </script>
    </head>
    <body>
        <h1>Hello!</h1>
        <button onclick="hello()">CLick Here</button>
    </body>
</html>
```
## Declaring variable 
`let counter = 0;` -> declare a variable
`const heading = document.querySelector('h1');` -> the value will never be changed and will error if we try to change it

## Various way of counter
```js
counter = counter + 1;
// counter += 1;  these all produce same result!
// counter++;
```

## Manipulating something in the page
`document.querySelector('h1')` go through the face, and return the first h1 element that found.
`document.querySelector('h1').innerHTML = 'goodbye';` to manipulate the content inside that element
`the == and ===` is different in js. `the triple ===` will check for the same variable type and the value to make sure it is the same.

The if else format is
```js

function hello(){
	let heading = document.querySelector('h1')
	if (heading.innerHTML === 'Hello!'){
		heading.innerHTML = 'goodbye';
	} else {
		heading.innerHTML = 'Hello!';
	}
}
```

To plug variable into the string, use ``alert(`Congrats! count is now ${counter}`);``
Take note if the backtick, bracket and the dollar sign!