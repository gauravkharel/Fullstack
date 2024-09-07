wIncludes: Classes, object, inheritance, abstraction, encapsulation, polymorphic
OOP is a computer programming model that organizes objects represents data and, operations. 
In OOP, software design around data and object rather than functions and logic.

**Class**: A class is a blueprint of an object. A class is a template definition of the methods and variables in a particular kind of object. It is a data type that the user specifies. 
**Object**: Objects are basically instances of a class. They can access variables or, methods declared inside the class. 
**Method**: A method is a programmed procedure that is defined as a part of class and is available to any object instantiated from that class.

## OOP Principles: 
**Encapsulations**: Information contained in an object exposed only elected information.
**Inheritance**: Child classes inherit data and behavior from parents class
**Polymorphism**: Many methods can do the same task.
**Abstraction**: Only exposing high level public method for accessing object.

#### Inheritance:
![](Screenshot%20from%202024-06-22%2016-09-14.png)


#### Encapsulation:
- Packaging of data and functions in classes.
- Which means we will group data and methods that operate on that data into separate bundles into objects.
- We can also restrict access to that data from outside the bundle using closure, private fields and so on.
Function of encapsulation:
- hides the logic and implementation within a class and disguise from inner objects
- encapsulation requires certain fields to be defined in public and private
- **private/internal interface**: properties and methods, available from the other methods same class
- **public/external interface**: properties and methods are taken from outside the class

### Abstraction
hides the code but, allow necessary access to info/access these data are contained inside the definition of objects
- all python data types are objects
- a list is a class constructed within methods for performing functions
Function of abstraction:
- using simple things to represent complexity
- hide complex details from user
- benefits:
	- simple, high level user interface
	- complex code is hidden
	- security
	- easier software maintenance
	- code updates rarely change abstraction
	- reduce the impact of change


#### Polymorphism
Works similarly to methods/method works differently for various class
- objects of different types can be passed through same interface
- **method overriding**: a child class can implement another method than its class by overriding it
- **method overloading**: the polymorphism compile time employs overloading approach
even with same name for methods, distinct parameter been given to the call method

#### Some interview questions:
a. What is OOPs and why it's important?
-> OOPs rely on object rather than just functions and procedure
-> all objects are grouped into classes in OOP
-> OOPs integrates real-world concepts into programming.

b. Why we need OOP?
-> OOPs provides ability to bind both data and code together
-> allows in keeping sensitive data confidential
-> improves code readability
-> polymorphis gives flexibility to the program by allowing the entities to have multiple forms
