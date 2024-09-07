# Fundamentals (data types/loops/conditinals/operators)

Level: Easy
ID: ACJ-3
Last edited time: September 3, 2023 11:23 AM
Status: Not started

## Values, Types, and, operators
1. Values
2. Numbers
	1. Arithmetic (1 + 2 ⇒ 3)
	2. Special Number (1.23)\
3. Strings (”aiudsaiugia”, ‘what is wrong with you’)
4. Unary Operators ()
5. Boolean Values
6. Comparison (<, >, ==, ===)
7. Logical Operators(&&, ||), Ternary Operators (console.log(true ? 1 : 2))
8. Empty Values (null, undefined)
9. Automatic Type Conversion
```
(console.log(8 * null)) ⇒ 0
(console.log(null == 0)) => false
```
10. Short-circuiting of Logical Operators 
```(console.log(”Agnes” || “user”)) ⇒ Agnes```

## Program Structure

Expression and statements (Expression are the basics of program ⇒ 1; is an expression as well)

Bindings (let myNum = 2; let binds the myNum keyword to value 2  that means binding have been define), const and var is also use to create bindings

Binding Names(catch22 is a valid binding names, any variable declaration works as this is the same thing, Lol)

The Environment 

Functions

The console.log function (is an expression that retrieves the log property)

Return values 

Control Flow (The flow of program is usually Top to bottom)

Conditional Execution (Ups and, down like a road in hills, this is where the conditional are introduced) ⇒ (if, else)

```jsx
let num = Number(prompt("Pick a number"));

if (num < 10) {
  console.log("Small");
} else if (num < 100) {
  console.log("Medium");
} else {
  console.log("Large");
}
```

While and Do Loops

```jsx
let number = 0;
while (number <= 12) {
  console.log(number);
  number = number + 2;
}
// → 0
// → 2
//   … etcetera
```

Indenting code

For Loops

```jsx
v=for (let number = 0; number <= 12; number = number + 2) {
  console.log(number);
}
// → 0
// → 2
//   … etcetera
```

Breaking out of loops

```jsx
for (let current = 20; ; current = current + 1) {
  if (current % 7 == 0) {
    console.log(current);
    break;
  }
}
// → 21
```

Updating Binding Succinctly: Using shortcuts like this  `(counter += 1;)` 

Dispatching on a value with switch

Capitalization

Comments

> from Eloquent JS
> 

Data Types, differences and explanation

- numbers
- string
- boolean
- arrays
- objects

conditional

- if/else
- switch

loops

- for
- do/while