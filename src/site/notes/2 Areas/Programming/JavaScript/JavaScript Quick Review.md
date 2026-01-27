---
{"dg-publish":true,"permalink":"/2-areas/programming/java-script/java-script-quick-review/","tags":["javascript"],"created":"2025-12-29T14:20:22.639+07:00","updated":"2025-12-29T14:51:26.032+07:00"}
---

- `var` hoists and becomes `undefined` early.
- `let/const` hoist but TDZ blocks access (ReferenceError).
- `function name(){}` is fully hoisted (callable before).
- `var f = function(){}` is **not callable** before assignment.
- `const say = user.sayName.bind(user)` → **fixes `this` forever**, copying the function data and fix the `this` to `user` value
- `array.forEach()` → **never returns a value**
- Functions are **values**. They can be passed as arguments, returned, and stored in variables `fn(x)` means “call the function stored in `fn` with value `x`”
- **Higher-order functions** A function that **accepts a function** or **returns a function**
- `.forEach()` → runs code, **returns `undefined`**
- `.map()` → transforms data, **returns a new array**
- **Array's Mutation** `.push()` mutates the array and returns the new length. Mutation changes original data and can cause hidden bugs. Prefer creating new arrays when transforming data
- Variables are just labels
- Functions don’t “own” variables
- JavaScript executes left → right, value → value
- Most JS bugs come from **scope**, **`this`**, or **mutation**, not syntax