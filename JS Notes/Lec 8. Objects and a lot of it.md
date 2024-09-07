# Objects and a lot of it

Level: Moderate
ID: ACJ-24
Last edited time: August 9, 2023 10:37 AM
Status: Not started

## ToF

- Objects
- Objects Method
- Prototypes
- Classes
- Class Notation
- Overriding derived properties
- Maps
- Polymorphism
- Symbols
- The iterator interface
- Getter, setters and statics
- Inheritance
- Objects in React ⇒ Implementation

Questions

- [**Write an object constructor and instantiate the object.**](https://www.theodinproject.com/lessons/node-path-javascript-objects-and-object-constructors#object-constructors)
- [**Describe what a prototype is and how it can be used.**](https://www.theodinproject.com/lessons/node-path-javascript-objects-and-object-constructors#the-prototype)
- [**Explain prototypal inheritance.**](https://javascript.info/prototype-inheritance)
- [**Understand the basic do’s and don’t’s of prototypical inheritance.**](https://www.theodinproject.com/lessons/node-path-javascript-objects-and-object-constructors#recommended-method-for-prototypal-inheritance)
- [**Explain what `Object.create` does.**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
- [**How does `this` behave in different situations?**](https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/)

### Objects

> Objects are not nested, basically.
> 

```jsx
function Player(name, marker) {
  this.name = name
  this.marker = marker
  this.sayName = function() {
    console.log(name)
  }
}

const player1 = new Player('steve', 'X')
const player2 = new Player('also steve', 'O')
player1.sayName() // logs 'steve'
player2.sayName() // logs 'also steve
```

### Objects Method

```jsx

```

### Object Properties

⇒ Two types of properties

1. Data Properties
2. Accessor Properties, i.e. getters and setter

### Objects implementation in react

```jsx
// a. state and object
// ==> treat state as read-only

// b. mutation
// c. using immer

```

### Classes