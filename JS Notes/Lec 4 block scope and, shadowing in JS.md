# Lec 4. block scope and, shadowing in JS

- block ⇒ { }, a.k.a, compound statement
- block scope ⇒ all variables and, function access within the block.
- var/const are also block scoped as it can be accessed within the scope and, the scope popped from Execution stack when it is completed.

```jsx
var a = 100
{
	var a = 10
	console.log(a)//a = 10
}

console.log(a)// a = 10
```

The code example illustrates shadowing which means pointing to the same memory location. 

But, in block scope, take this example.

```jsx
let d = 100
{
	let d = 10
	console.log(b)//b = 10
}

console.log(b)//b = 100
```

This creates two blocks.

### Illegal shadowing

```jsx
let a = 20
{
	var a = 20
}

// Uncaught SyntaxError: has been declared already
```

```jsx
var a =20
{
	let a= 20
}
//because var is a blocked scope variable declaration stuff that is cool. 
```

### const/let is lexical scope which finds the nearest declaration and, follows lexical scope chain pattern.

| js function/variable                    | scope                                           |
| --------------------------------------- | ----------------------------------------------- |
| var/const                               | block scope                                     |
| function declaration                    | function scope                                  |
| function expression (const x = () ⇒ {}) | scope of the declared variable i.e. block scope |
| arrow function                          | lexical scope                                   |