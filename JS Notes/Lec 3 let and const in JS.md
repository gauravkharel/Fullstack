# Lec 3. let and const in JS

### temporal dead zone:

this is the time between a variable is hoisted and, when the variable have some values. Meaning, a variable after memory creating and, code execution sequence. Whenever you try to access value in temporal dead zone you’ll get Reference Error. 

### let and, const

- basically, let/const are not stored in windows(global) object but, are hoisted.
- let can’t be redeclared which throws SyntaxError but, can be declared and, assigned value later

e.g. const b; // throws SyntaxError: Missing Initializer in const declaration.

- recommended: const to use whenever we can as it’s more strict. and, use let if you need to after const.
- TypeError: {const a = 10; a = 20} throws the error cause y’know constant can’t be re-declared.