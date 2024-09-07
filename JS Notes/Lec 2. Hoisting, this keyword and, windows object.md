# Lec 2. Hoisting, this keyword and, windows object

During memory execution, all the declaration are moved to the top of their scope which is before code execution. This process is called hoisting.

- In memory creation,
    - variable declaration are scanned and, are made undefined
    - function declaration are acanned and, made available.

Hoisting basically means allocating memory.
- a normal function store in memory as
    - getName: fn getName()
- an arrow function is stored as a variable
    - getName: undefined
![[JS Notes/Lec 2 Hoisting, this keyword and, windows object 21209da1c72f4408ae8b908d3dd8b8d1/Untitled.png]]
Every EC has its own memory and, environment running separately independent from each other