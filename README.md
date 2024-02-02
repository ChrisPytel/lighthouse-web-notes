# Chris's Lighthouse Dev Notes
## Summary 
This repository contains all of my notes taken by [Chris](https://github.com/ChrisPytel) that I've compiled for the Lighthouse Labs Web Development Bootcamp.

https://www.markdownguide.org/basic-syntax/

# Table of Contents

  * [Variables and Datatype Properties](#variables)
  * [Strings]()
  * [Numbers and Operators]
  * [IF... and ELSE IF... statements]
  * [For and While Loops]
  * [Arrays]
  * [Functions]
  * Comparisons and Booleans
  * Objects
  * Replit and IDE 
  * Dev environment
  * Terminal and Command Line
    * Common Terminal Commands
    * Directory + file manipulation commands
  * Git Github and source control
    1. Initial setup
    2. Info related commands
    3. Staging to the INDEX and committing to the HEAD
    4. Push and pull and connecting to remotes
    5. Branches and merging
    * Note during LHL Git and GitHub Account Setup

* Module 1
  * [Week 1](/Week_1)
    * Gists
    * Refactoring
    * ESlint
    * Markdown
  * Week 2
    * Datatypes
    * ...
    * ...
    * ...

* Lecture notes
  * Week1 L1
  * Week1 L2
  * Week2 L1
  * Week2 L2
  * Week3 L1
  * Week3 L2




## Variables


There are 3 main types of variables that can hold a datatype

`var` is a variable that can be assigned a datatype to represent and it can have its value changed after being assigned. 

Its is the original way of declaring variables in Javascript, 
Since 2015 with ES6 Update, the new standard of declaring variables has shifted towards using `let` and `const`

`let`   is a variable that can have its value changed after being assigned.

`const`  is a read only variable that once its value is assigned, it cant be overwritten. (If a datatype such as array or object within an const object are excepted)


#### Declaration
You can delcare a variable, then assign its value later:


```javascript
var numberOfDogs;
numberOfDogs = 3;
```

Alternatively, you can also initialize a variable and declare its datatype value immediately


```javascript
var numberOfCats = 5; 
```

## Datatypes are
`number`      a datatype representing a number value 

`string`      a datatype representing a sequence of text

`boolean`     a datatype representing a true or false value, they are mutually exclusive

`undefined`   when no value is assigned yet.

`null`        similar to undefined, its value is made intentionally empty


`object`      a datatype representing a collection of key value pairs 

`symbol`      a datatype representing a object property keys (ignore for now)

`bigint`      a datatype representing an overly large integer value (ignore for now)


## Primitive vs objects


In JavaScript, primitive data types are immutable, meaning they cannot be altered once they are created. 
They are also compared by value, not by reference. Primitive datatypes are values are fixed.
Primitive data types in JavaScript are:

`String:` Represents textual data, enclosed within single or double quotes.
`Number:` Represents numeric data, this includes integers (whole numbers) and floating-point numbers (decimal numbers).
`Boolean:` Represents a logical value, either true or false.
`Undefined:` Represents a variable that has been declared but has not been assigned a value.
`Null:` Represents the intentional absence of any value.
`Symbol:` Represents a unique identifier, introduced in ECMAScript 6.

## Objects
The main mutable data type is objects. Mutable values are datatypes whos value can be changed, such as array, and objects. 
However, there are other data types and structures that are considered mutable because they allow for changes to their values or contents. 
Mutable data types and structures in JavaScript are

  `Objects:` Objects in JavaScript are mutable collections of key-value pairs where the values can be changed or updated.
`  Arrays:` Arrays are ordered collections of elements and are mutable. They can be modified by adding, removing, or updating elements.
  `Functions:` Functions in JavaScript are mutable. You can modify a function's behavior by adding or changing its properties, or by reassigning it to different variables.


An array is considered an object because it is mutable. 
I thought that an array was its own datatype, it falls under the datatype of object `(If you do a console.log(typeof myArray); it outputs as object and not array;)`

## Literals vs non literals

The difference between declaring something as a literal vs non literal is determined by how you initialize the variable. 

Example of an object literal: 

Here we create a const `person` and define it as an object with some key/values assigned to it.

```javascript
const person = {
    name: 'John',
    age: 30
};
```
Example of an object created using a constructor

Here we create a const `person` and define it as a `new` object, it is essentially empty at this point. We later "construct" the object by defining some values within the object.
```javascript
const person = new Object();
person.name = 'John';
person.age = 30;
```

## Lexical Scoping for variables within Javascript

Javascript performs variable scope check following lexical scoping. 
Meaning that the scope of a variable is determined by its location within the code as a whole, rather than what the runtime arrives at.
Its useful reminder to think that local scope is defined by curlybraces.

When JS encounters a variable reference, it follows this sequence to determine what its scope is:
  1. Local Scope AKA Innermost Scope

  Javasript frist checks if the variable is stored within the current function or block. 
  If the variable is declared locally, JS uses that variable.

  2. Enclosing Scope aka Outer Scope

  If the variable isnt located in local scope, JS searches in its enclosing scope, aka a level above.
  This process continues outward until either the variable is found or the global scope is reached.

  3. Global Scope aka Outermost Scope

  If the variable isnt found in any enclosing scopes, JS finally checks the global scope. 
  Variables declared outside of any function or curly block are a part of the global scope (within the file it is running in). 
  If the variable is found in the global scope, JavaScript uses that variable. If it isnt found, then it will likely be undefined.



```javascript
    let userName = "James";

    const testFunction = function(){ //one level deep in defined by curlybrackets
      let userName = "Jeff";
      console.log(userName); // will log jeff, as it cannot check any levels deeper than it currently resides
      const testFunction2 = function(){ //2 levels deep in scope defined by curlybrackets
        let userName = "Jony";
        console.log(userName);
      }
      testFunction2();      
    }    
    testFunction();    
    console.log(userName); // will log James, as it cannot check any levels deeper than it currently resides, its closest reference 
```



























### this is an H3 for subsections
content content content content content content 
#### H4 sections
content content content content content content 
##### H5 sections
content content content content content content 
###### This is an H6 header (smallest)
content content content content content content 






