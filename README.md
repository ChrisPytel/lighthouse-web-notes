# Chris's Lighthouse Dev Notes

<i>"LHL Notes Doc V3 - Fleshed out notes on Week 2 and 3 content"</i>

### Summary 
This repository contains all of my notes taken by [Chris](https://github.com/ChrisPytel) that I've compiled for the Lighthouse Labs Web Development Bootcamp. 
https://www.markdownguide.org/basic-syntax/

# Table of Contents for Module 1 - Javascript

  * [Variables and Datatype Properties](#variables)
  * [Strings](#strings)
  * [Numbers and Operators](#numbers-and-operators)
  * [IF... and ELSE IF... statements](#if-statements-and-else-if-statements)
  * [For and While Loops](#for-and-while-loops)
  * [Arrays](#arrays)
  * [Functions](#functions)
  * [Comparisons and Booleans](#comparisons-and-booleans)
  * [Objects](#objects)


    * [Week 1](#week-1)
      * Gists
      * Refactoring
      * ESlint
      * Markdown
    * [Week 2](#week-2)
      * Datatypes
      * Object Iteration
      * Anon functions
      * Arrow functions
      * Callbacks
    * [Week 3](#week-3)
      * Object Methods
      * Recursion
      * Testing with Mocha and Chai
      * Object Oriented JS
    * [Week 4](#week-4)
      * ...
      * ...
      * ...
      * ...



# Variables
There are 3 main types of variables that can hold a datatype <br>

`var` is a variable that can be assigned a datatype to represent and it can have its value changed after being assigned.  <br>
Its is the original way of declaring variables in Javascript, 
Since 2015 with ES6 Update, the new standard of declaring variables has shifted towards using `let` and `const`

`let`   is a variable that can have its value changed after being assigned.

`const`  is a read only variable that once its value is assigned, it cant be overwritten. (If a datatype such as array or object within an const object are excepted). It is good practice to use const wherever possible, until the editor complains that a variable needs to be accessed. This prevents accidental overwriting of variables from unwanted sources. <br>

### Declaration
You can delcare a variable, then assign its value later:
```javascript
let numberOfDogs;
numberOfDogs = 3;
```
Alternatively, you can also initialize a variable and declare its datatype value immediately
```javascript
const numberOfCats = 5; 
```
If you attempt to overwrite a primitive variable represented by a const, it will return an error
```js
const pizzaSlices = 8;
pizzaSlices = 5;  //
```

## Datatypes are
`number`      a datatype representing a number value <br>
`string`      a datatype representing a sequence of text <br>
`boolean`     a datatype representing a true or false value, they are mutually exclusive <br>
`undefined`   when no value is assigned yet. <br>
`null`        similar to undefined, its value is made intentionally empty <br>

`object`      a datatype representing a collection of key value pairs  <br>
`symbol`      a datatype representing a object property keys (ignore for now) <br>
`bigint`      a datatype representing an overly large integer value (ignore for now) <br>


## Primitive vs objects

In JavaScript, `primitive` data types are immutable, meaning they cannot be altered once they are created. They are also compared by value, not by reference and their values are fixed.
Primitive data types in JavaScript are:

`String:` Represents textual data, enclosed within single or double quotes. <br>
`Number:` Represents numeric data, this includes integers (whole numbers) and floating-point numbers (decimal numbers). <br>
`Boolean:` Represents a logical value, either true or false. <br>
`Undefined:` Represents a variable that has been declared but has not been assigned a value. <br>
`Null:` Represents the intentional absence of any value. <br>
`Symbol:` Represents a unique identifier, introduced in ECMAScript 6.

## Objects
The main mutable data type is `objects`. Mutable values are datatypes whos value can be changed, such as array, and objects. As such, mutable datatypes are often defined using `const`, as it is possible to change thier internal values. T here are other data types and structures that are also considered mutable because they allow for changes to their values or contents. In JavaScript they are:

`Objects:` Objects in JavaScript are mutable collections of key-value pairs where the values can be changed or updated. <br>
`Arrays:` Arrays are ordered collections of elements and are mutable. They can be modified by adding, removing, or updating elements. <br>
`Functions:` Functions in JavaScript are mutable. You can modify a function's behavior by adding or changing its properties, or by reassigning it to different variables.


An array is considered an object because it is mutable. 
I thought that an array was its own datatype, it falls under the datatype of object <br> `(If you do a console.log(typeof myArray); it outputs as object and not array;)`

## Literals vs non literals

The difference between declaring something as a literal vs non literal is determined by how you initialize the variable.  <br>
Example of an object literal: 
```js
const person = {
  name: "John",
  age: 30
};
//Here we create a const `person` and define it as an object with some key/values assigned to it.
//This makes it a literal, meaning it wasnt literally defined at creation.
```
Here is an example of an non-literal object created using a constructor: <br>
```js
const person = new Object();
person.name = "John";
person.age = 30;
//Here we create a const person and define it as a new object, it is essentially empty at this point.
//We later construct the object by defining some values within the object.
```

## Lexical Scoping for variables within Javascript

Javascript performs variable scope check following lexical scoping. 
Meaning that the scope of a variable is determined by its location within the code as a whole, rather than what the runtime arrives at.
Its useful reminder to think that local scope is defined by curlybraces.

When JS encounters a variable reference, it follows this sequence to determine what its scope is:

**1. `Local Scope` AKA Innermost Scope** -  Javasript first checks if the variable is stored within the current function or block. 
If the variable is declared locally, JS uses that variable.

**2. `Enclosing Scope` aka Outer Scope** - If the variable **isnt** located in local scope, JS searches in its enclosing scope, aka a level above.
This process continues outward until either the variable is found or the global scope is reached.

**3. `Global Scope` aka Outermost Scope** - If the variable **isnt** found in any enclosing scopes, JS finally checks the global scope. 
Variables declared outside of any function or curly block are a part of the global scope (within the file it is running in). 
If the variable is found in the global scope, JavaScript uses that variable. If it isnt found, then it will likely be undefined.


```js
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

# Strings

Strings are datatype that holds text information, aka string literals
```js
let studentFirstName = "Chris";
```
You can build a string with variables inserted between
```js
let customerName = "Chris";
let welcomeMessage = "Hello nice to meet you " +customerName". It's a nice day today.";
//console.log(welcomeMessage); will output
// "Hello nice to meet you James. Its a nice day today.";
```
Strings can be written with single or double quotes
```js
const doubleQuoteStr = "This is a string"; 
const singleQuoteStr = 'This is also a string';
```
Bonus, you can use backticks as a 3rd layer if you like to ennclose the other two within it.
```js
const backTickDemo = `this is a "backtick quote", if you like to enclose 'other quotes' within this one`; // (` ' ") all work to declare strings
```
String values in JavaScript may be written with single or double quotes, as long as you start and end with the same type of quote. This might happen if you want to save a conversation in a string and have the conversation in quotes. 
```js
let mortalKombatTaunt = 'Scorpion shouts across the room, "GET OVER HERE!"';
```

You can escape literal quotes in a string by using the backslash \ infront of the quote
```js
const sampleStr = "Jeff said \"My name Jeff\"."
console.log(sampleStr); //would read - Jeff said "My name Jeff".
```

### Concatenation
In JavaScript, when the + operator is used with a String value, it is called the concatenation operator. You can build a new string out of other strings by concatenating them together.
```js
const ourStr = "I come first. " + "I come second.";
console.log(ourStr); //will output: I come first. I come second.
```
We can also use the += operator to concatenate a string onto the end of an existing string variable. 
```js
let ourStr = "I come first. ";
ourStr += "I come second.";
console.log(ourStr); //will output: I come first. I come second.
```

You can build a string with variables too.
```js
const anAdjective = "awesome!";
let ourStr = "freeCodeCamp is ";
ourStr += anAdjective;
console.log(ourStr); //will output: freeCodeCamp is awesome!
```

You can determine the length of a string by using the .length property
```js
let name = "Christopher";
console.log(name.length); // would output 11
```

# Numbers and Operators
Number is a datatype in which defines numerical values. Whole numbers are referred to as integers, while decimals are referred to as floats.
//You can use basic mathematics with the following operators 

`+` for addition operations
```js
let sumValue = 5 + 10;
console.log(sumValue);  //will output: 15
```
`-` for subtraction operations
```js
let differenceValue = 32 + 8;
console.log(differenceValue);  //will output: 24
```
`*` for multiplication operations
```js
let productValue = 20 * 5;
console.log(productValue);  //will output: 100
```
`/` for division operations
```js
let quotientValue = 1024 / 2;
console.log(quotientValue);  //will output: 512
```
You can use compound assignments to modify the contents of a variable by any operator mentioned above. `+=` `-=` `*=` `/=`
```js 
let testVar = 10;
testVar += 15;  // is the same as testVar = testVar +15;
```
You can increment a value by +1 by using the `++` operator, or decrement by using the `--` operator
```js
var i = 13;
i++;
console.log(i); // would output: 14
i--;
console.log(i); // would output: 13
```
Modulus aka `%` is for calculating the remainder of an operation
```js
let remainderValueA = 400 % 360;      //in this usecase it will output: 40
```
Think of a 360 degree circle, where if the user inputs a higher value than the total, the remainder will overrun back into the defined value.

A common usage is to use the modulo `n % 2`,
this can be used do determine whether a number is even or odd outputting 0 if it is even and 1 if it is odd

```js
let remainderValueB = 4 % 2;    //will output: 0
let remainderValueC = 3 % 2;    //will output: 1
```



# IF statements, and ELSE IF statements

You can chain if statements together with `else if` statements.
If none of the conditons are met in any `if else` statement, you can wrap it with an `else` statement as a catch-all
```js
function checkNum(num){
  if (num > 15) {
      return "Bigger than 15";
  } 
  else if (num < 5) {
      return "Smaller than 5";
  } 
  else {
      return "Between 5 and 15";
  }
}
```
Many If else statements can be chained to do complex tasks
The function is executed from top to bottom so you will want to be careful when ordering what statement comes first.
```js
function checkSize(num){
  if (num < 5) {
      return "Small";
  }
  else if (num < 10) {
      return "Medium";
  }  
  else if (num < 15) {
      return "Large";
  }  
  else if (num <= 20) {
      return "Huge";
  }  
  else {
      return "Invalid size";
  }
}
console.log(checkSize(12)); // output would be: Large
```


### Conditional (ternary) operator
  The `?` is the only operator that takes 3 operands, a then an expression to execute if the condition is truthy followed by a colon (:), and finally the expression to execute if the condition is falsy. This is often used as an alternate to if..else statements.

Syntax is:  `condition ? exprIfTrue : exprIfFalse;`
```js
function getFee(isMember) {
  return isMember ? '$2.00' : '$10.00';
}
console.log(getFee(true));    // Expected output: "$2.00"
console.log(getFee(false));    // Expected output: "$10.00"
```


# For and While Loops  
Loops can be used to run the same code many times over, they can be run from within a function or an object, or outside of one 

`While loops ` will execute its code while a specified condition is true and ends once that value is false.
```js
var myArray = [];           // setup an empty array

var i = 0;
while(i < 5) {              //the loop will run while the variable i is less than 5
myArray.push(i);          //the loop will push the value of i into the array and make a new entry for each
i++;                      //increments i by 1
}
console.log(myArray);       // will output the result of the array [0, 1, 2, 3, 4]
```



`For loops` will run for a  specified number of times, they are controlled by three expressions. Example: `for` (`a`, `b`, `c`) { `code that the loop runs`} ;

`a` is the initial statement, usually a var assigned with a number
`b` is the condition that the loop will run for until it is false
`c` is the final expression, ususally used to update the loop variable

```js
var ourArray = [];// setup an empty array
for (var i = 1; i < 6; i++) {//beginning at 1, the loop will run until i is 6, each time incrementing by 1
myArray.push(i);//the loop will push the value of i into the array and make a new entry for each
}
console.log(myArray);//outputs => [1, 2, 3, 4, 5]
```
You can increment or decrement the final expression by something other than 1, it could even be negative
```js
var myArray = [];                      // setup an empty array
for (var i = 9; i > 0; i -= 2) {        //beginning at 9, the loop will run until i is 1, each time incrementing by negative 2
myArray.push(i);                      //the loop will push the value of i into the array and make a new entry for each
}
console.log(myArray);                 //will output the result of the array [1, 2, 3, 4, 5]
```


//It is common to iterate through the contents of an array. 
//This example will add all of the entries in the array and output a total number
```js
var myArr = [8, 16, 32, 64, 128];           //this array is declared with 5 entries
var total = 0;                              //the total will begin at 0
for (var i = 0; i < myArr.length; i++) {    // the loop will run for however long the array length is
total += myArr[i];                        //the total will take the value of the array at whatever index number the for loop is at and add it to the current total
}
console.log("Total = " + total);                 // the output should be: Total = 248
```

# Arrays
With array variables, we can store several pieces of data in one place.

You can declare an array with an opening square bracket, end it with a closing square bracket, and put a comma between each data type entry. Below is an array with a bunch of strings as elements.
```js
const computerParts = ["case", "power supply", "motherboard", "cpu", "ssd", "gpu", "fans"];
```
You can also nest arrays within other arrays, like below:
```js
const petsAtHome = [["Dogs", 6], ["Cats", 3]];
```
## Modify Array Data With Indexes 
We can access the data inside arrays using the array index with square brackets [], it defines a location to an entry within the array. 
```js
const array = [762, 545, 939];
const data = array[1]; //The first item in an array has an index # of 0.
```

^ In the above text, we created an array with 3 entries, then we created a new variable and assigned it to the value represented by the 2nd element in the array
the variable data is now the same value as the 2nd entry within the array = `545`

The entries of arrays are editable and can be changed freely, even if the array was declared with const.
```js
const ourArray = [50, 40, 30];
ourArray[0] = 15; 
//the first entry within the array is now defined as 15 and not 50
```


## A multi-dimensional array, is as an array of arrays. 
When you use brackets to access your array, the first set of brackets refers to the entries in the the first level, and each additional pair of brackets refers to the next level of entries inside. <br>
In this example, subarray has the value `[[10, 11, 12], 13, 14]`, nestedSubarray has the value `[10, 11, 12]`, and element has the value `11`.
```js
const arr = [[1, 2, 3],[4, 5, 6],[7, 8, 9],[[10, 11, 12], 13, 14]];
const subarray = arr[3];
const nestedSubarray = arr[3][0];
const element = arr[3][0][1];
```

Its possible array with mixed data types, not just a single data type like strings or numbers
`var mixedData = ["abcd", 1, true, undefined, null, "all the things"];`

Nested arrays can be particularly hard to read, so it's common to write them on one line, using a newline after each comma, like this arrangement
```js
const arraysInArrays = [
  [1, 2, 3], 
  ["Julia", "James"], 
  [true, false, true, false]
];
```
It is possible to change an element in an already defined array:
```js
let donuts = ["glazed", "powdered", "sprinkled"];
donuts[1] = "blueberry flled"; // the second element which was the powdered donut is now redfined as blueberry filled
```

## array.length
// the command array.length is useful for accessing the number of elements in a given array
```js
let dogs = ["shi-tzu", "husky", "shiba","pomeranian"];
console.log(dogs.length); // would output 4, as there are 4 entries in the array
```

## array.push() method
adding elements to an array can be done via the `.push()` method
```js
let pcParts = ["CPU", "motherboard", "powersupply", "SSD"];
pcParts.push ("GPU"); //adds a new string element "GPU" to the end of the array
console.log(pcParts); //would output  "CPU", "motherboard", "powersupply", "SSD", "GPU"
```

## array.pop() method
adding elements to an array can be done using the `.pop()` method
```js
let stuffOnMyDesk = ["monitor", "keyboard", "mouse","mousepad","microphone","chocolate bar", "glass of milk"];
stuffOnMyDesk.pop();            //removes the last element from the array
stuffOnMyDesk.pop();            //removes the last element from the array
console.log(stuffOnMyDesk);     //would output  "monitor", "keyboard", "mouse","mousepad","microphone"
```
## array.splice() method
the `.splice()` method can be used to add and remove elements anywhere within an array
```js
let dogs = ["Poodle", "Collie", "Labrador", "Beagle"];
dogs.splice(2, 2, "Golden Retriever", "mexican spaniel");
// should output [ 'Poodle', 'Collie', 'Golden Retriever', 'mexican spaniel' ]
```
Following is the syntax breakdown of splice() method:

arrayName.splice(`arg1`, `arg2`, `item1`, ....., `itemX`); where,

`arg1` = Mandatory argument. <br>
Specifies the starting index position to add/remove items. 
You can use a negative value to specify the position from the end of the array e.g., -1 specifies the last element.<br>

`arg2` = Optional argument. 
Specifies the count of elements to be removed. If set to 0, no items will be removed.

`item1`, `.....,` `itemX` are the items to be added at index position arg1<br>

If passing in a negative integer into the first arguement, it will count backwards from the end of the array. <br>
(-2) for example will reference the second last index number as in the array


## array sort

    
## reverse method
you can reverse an array using the reverse method<br>
NOTE: reverse is destructive -- it changes the original array contents.

```js
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);  //output: "Array1:" ["one", "two", "three"]

const reversedArray = array1.reverse();
console.log('reversedArray:', reversedArray);  //output: "reversed:" ["three", "two", "one"]
console.log('array1:', array1);
// Expected output: "Array1:" ["three", "two", "one"]
// Even though a new variable was declared
```


## for..of loops and for..in loops
  //For..of is a new type of loop in ES6 and are useful for looping over iterable data structures, such as arrays, strings and more.
  //the syntax of a for..of loop is the following


```js
for (variable of iterable){
//code that the loop will execute
}
```

// here is an example
//first define an iterable element that you want the loop to go over, for example an array of character names
let characters = ["Mario", "Luigi","Link","Zelda","Samus","Ridley"];

//the variable will then 
for (list of characters){
  console.log(list);
}  // should output the contents of the array, outputting: "Mario", "Luigi","Link","Zelda","Samus","Ridley"

//using the break feature
  //you can use the break feature in an if statement to exit out of the loop early.
  for (list of characters) {
    if (list === "Zelda"){
      break
    }
    else{
      console.log(list);
    }
  }
  // should output the contents of the array and it will stop once the string "Zelda" is reached
  // outputting: "Mario", "Luigi","Link","Zelda"                              



## for..in loops (used for objects)
for..in is used for iterating over the contents of an object and its properties

```js
const someObject = { 
  animal: "Dog", 
  sound: "Woof Woof", 
  favFood: "Treats",
};
for (const key in someObject) {
  const value = someObject[key];
  console.log(key, value); // Will output "animal", "Dog" and "sound", "Woof Woof" and "favFood", "Treats"
}
```



# Functions

### Creating functions
We can create blocks of code that are reusable called functions, they are declared and given a name with parenthesis at the end.
The contents of a function are surrounded with curlybraces, the code written within these curly braces is what the function will run when called. 

Here is an example of a function declaration.
```js
function functionName() {
  console.log("Hello World");
};
```
Alternatively you can declare a function expression, where the function is assigned to a variable, 
```js
const sayHello = function () {
  console.log("Hello, world");
};  
sayHello();    
```
### Function calling
Functions can be called upon later by using its name with brackets
when calling a function, you can pass information into the function via the brackets, the one below is empty and passes in nothing
```js
functionName();
```

### Function parameters
Parameters are variables that act as placeholders for the values that are to be input to a function when it is called. The actual values that are input (or "passed") into a function when it is called are known as arguments.  
  
Here is a function with two parameters, parameter1 and parameter2:
The two arguements are "Im" and "the best!"

```js  
function testFunc(parameter1, parameter2) {
  console.log(parameter1, parameter2); //output => "Im the best!"
}
testFunc("Im", "the best!");
```

## Return 
  You can use a return statement to send a value out of a function
```js
function plusThree(num) {
  return num + 3;
}
const answer = plusThree(5); //output => 8
```

  the new variable answer will be equal to whatever the function returns when you input 5 as appear within the brackets


## Variable Scope
Variables outside of functions have global scope, meaning they can be seen everywhere (within its file).<br>
Its possible to have a global and a local scope variable with the same name, in the even this happens, local will take precedent over global check this section on [lexical scope](#lexical-scoping-for-variables-within-javascript)

```js
var globalVar = "Im visible everywhere";    // is visible everywhere on the file only

function localScopeDemo() {
  var localVar = "Im visible locally";    // localVar only has scope within its function, will not be accessible outside of the func 
  console.log(globalVar);
  console.log(localVar);
}
localScopeDemo();
console.log(globalVar);
console.log(localVar);   // this line will not be outputted and result in an error as it is calling a variable local to the function
```

## Function return
 A function doesnt NEED to have a return statement, if it is missing and you call it, it will run the contents but will return the value of undefined.

```js
var sum = 10;
function calculate() {
  sum = sum + 5;
}
function(addThree);       //when this function is called, it runs and calculates sum = sum + 5.
console.log(sum);         //as there was no return statement as a result of running the function, the console outputs the original sum of 10
```  

## Function Properties
Since functions are technically objects, we can assign values to them as though they were an object. These can be accessed and changed later on as well

```js
const myFunc = function() {
  console.log("I am function.");
}
myFunc.someAttribute = 42;
console.log(myFunc);
console.log(myFunc.someAttribute);
myFunc();
// output is: 
// [Function: myFunc] { someAttribute: 42 }
// 42
// I am function.
```



# Comparisons and Booleans

//If statements are used to make decisions within functions in code.
  //The keyword if runs the code in the curly braces under certain conditions that are defined in the parentheses. 
  //These conditions are known as Boolean conditions and they may only be true or false.

  function trueOrFalse(arguement) {
    if (arguement) {
      return "Yes, that was true";
    }
    return "No, that was false";
  }
  console.log(trueOrFalse(true));     // the output would display true, as we passed in a true arguement into the function

//EQUALITY comparator is ==
  
  // you can set the conditions of an if statement to equal something, in this case if the value passed in is equal to 12, run the contents of the statement
  function testEqual(val) {
    if (val == 12) {
      return "Equal";
    }
    return "Not Equal";
  }  
  console.log(testEqual(10));       // would output not equal

//NOT EQUALS comparator is !=
  // The operator to check if two values are NOT equal is !=
  function test(val) {
    if (val != 99) {            //If the value is NOT equal to 99, return a TRUE boolean and outputs "Not Equal"
      return "Not Equal";
    }
    return "Equal";
  }  
  console.log(test(10));


// Strict equality === is similar to ==. 
//Although === literally checks if the datatypes are identical, == can perform type conversions between string and numbers
3 ===  3  // true as they are both number 3
3 === '3' // false as one is numerical 3 is and the other is string '3'

// Strict inequality !== is the counterpart to strict equality === , if the conditions are met, will output true.
6 !==  6  // returns false
6 !== '6' // returns true


//The operator for GREATER THAN is >
6  >  1  // returns true
7  > '3' // returns true      also accepts strings

//The operator for LESS THAN is <
6  <  1  // returns false
3  < '7' // returns true      also accepts strings

//The operator for GREATER THAN OR EQUAL TO to is >=
6  >=  1  // returns true
6  >=  6  // returns true
2  >= '5' // returns false      also accepts strings

//The operator for LESS THAN OR EQUAL TO than is <=
6  <=  1  // returns false
7  <= '7' // returns true      also accepts strings


//The logical OR operator is || 
//returns true if any of the of the operands is true. Otherwise returns false boolean.
function testForOR(num){
  if (num > 10 || num < 5) {
      return "No";
    }
    return "Yes";
}
console.log(testForOR(45)); // output would be no as the number 45 is outside of the range 



//The logical AND operator is &&
//returns true if both (or all) of the operands are true. Otherwise returns false boolean.
function testForAND(num){
if (num > 10 && num < 5) {
    return "No";
  }
  return "Yes";
}
console.log(testForAND(8)); // output would be no as the number 8 is inside the range 









# Objects
An object is a data structure in JS that is versatile for storing data in key-value pairs. 
Unlike arrays, objects are useful in storing data that do not need to rely on its internal index

## Declaration
  Objects can be declared using curly braces {}
  `let myObject = {};`

## Object properties
the properties of an object, AKA key-object pairs can be added or accessed using dot notation or square bracket notation.
`myObject.key = "value";`
or
```js
myObject["anotherKey"] = 42;
myObject["totallyDifferentKey"] = "Hello I'm a string";
console.log(myObject);      
// will output: key: 'value', anotherKey: 42, totallyDifferentKey: 'Hello im a string'
```  
Alternatively, you can declare an `object literal` with the following syntax. This one creates an object car and defines its propeties right away.
```js
let car = {
  make: "Honda",
  model: "Civic",
  color: "Graphite",
  mileage: 3000,
  year: 2022,
};
```
### Delete keys
removes the year property and displays the object without that property
`  delete car.year;`


It is possible to define a string and pass it in via square bracket notation
const key = "size";
```js
const coffee = {
  type: "latte",
  size: 400,
  cupType: "paper",
};

console.log(coffee[key]);  // will output: size: 400
```
note: how passing in a variable does not use  console.log(coffee.[key]);       remember to avoid the dot before adding variable

### Object.keys() method
The Object.keys method is used to extract the keys from an object and return them as an array. The syntax for the Object.keys() method is as follows:
```js
let employee = {
  name: 'John',
  age: 30,
  job: 'Construction'
};
//Here, obj is the object for which you want to retrieve the keys.
let keys = Object.keys(employee);  
console.log(keys); // Will Output the keys: ['name', 'age', 'job']
  ``` 

### Object.values() method
  //Performs similarly to the The object.keys method, and its used to extract the value from an object and return them as an array. 
  //The syntax for the object.values() method is as follows:

```js
let boss = {
  name: 'Tony',
  age: 56,
  job: 'Waste Management Consulting'
};
//Here, obj is the object for which you want to retrieve the values.
let values = Object.values(boss);  
console.log(values); // Will Output the values: ['Tony', '56', 'Waste Management Consulting']
```

 <br> <br> <br> <br> ------------------------------------------<br> <br> <br> <br> <br>

# Weekly Notes Recap


# `Week 1`
`Gists` are a part of github that function as repositories for singular files, they can be forked/cloned and shared via link for peers to review

`Refactoring` is the practice of going back to your code and cleaning up. During this process you remove redundant logic and streamline code for readability. Lightweight code is better

`ESlint` is a npm package for node used to format your .js files to a certain standard

`Markdown` aka .md is a filetype similar to .txt but it is much more versatile. Generally youll find find one in most github repos as a README.md

`Command line arguments`
The built in node method `process.argv` takes whatever we input into our console and returns an array with every arguement as its own string within an array.

If we write into terminal: `$ node cmdLineArgs.js 16 32 16`

```js
//cmdLineArgs.js
const commandLineArgs = process.argv; //is an array of strings
console.log(commandLineArgs); //displays what our input is from cmd line
function sumArguments(input) {
  let total = 0;
  for (const arg of input) {
    const converted = Number(arg);//converts the string numbers to integers
    if (Number.isInteger(converted) && converted > 0) {
      total += converted; //adds our numbers
    }
  }
  return total; //returns total to be printed
}
console.log(sumArguments(commandLineArgs)); //prints our sum of 64
```



# `Week 2`
## Primitives Datatypes Vs Objects
[covered here](#primitive-vs-objects)

## Object Iteration
 Object iteration is most commonly done using the `for..in` loop. As opposed to the `for..of` or `c-style for loop` that is used for arrays. Remember my mnemonic of `foreign object = for..in object` when judging which type of loop to use in which case.
```js
const person = {
  name: 'Alice',
  age: 30,
  city: 'Midland',
  job: 'Hair Stylist'  
};
for (const key in person) {
  console.log(`${key}: ${person[key]}`);
}
```

## Higher Order functions
Higher order functions take in another function as an arguement, <b>or</b>
returns a function as its result. 
<br> Here is an example; `applyOperation` takes in 2 numbers and a function, and <b>also</b> returns a function.

```js
//This is a higher order operation because returns another function as an arg.
function applyOperation(x, y, operation) { 
  return operation(x, y);
}
function add(a, b) {
  return a + b;
}
function multiply(a, b) {
  return a * b;
}
console.log(applyOperation(2, 3, add)); // Output: 5
console.log(applyOperation(2, 3, multiply)); // Output: 6
```

Here is another
```js
function greet(name, formatter) {
  return formatter(name);
}
function capitalize(name) {
  return name.charAt(0).toUpperCase() + name.slice(1);
}
function addExclamation(name) {
  return name + '!';
}
console.log(greet('alice', capitalize)); // Output: "Alice"
console.log(greet('bob', addExclamation)); // Output: "bob!"
```

## Callbacks
Callbacks are a type of higher order function. They are a function that is passed in by reference into another function, known as the `reciever`. The `reciever` can call the callback function as many times as needed
```js
function greet(name, callback) {//this is the reciever function
  return "Hello, " + callback(name);
}
function passName(personGreeted) {//this is the callback function, it will return its results into the reciever function
  return `${personGreeted}, what a nice day today!`;
}
console.log(greet("Steve", passName)); 
// Output: Hello Steve, what a nice day today!
```

## Anonymous functions
Anonymous functions are unique in that they do not be defined to a variable or named. Often times `callback functions` and `arrow functions` are anonymous as they only really function to return a value and dont need to be defined.

```js
function longNames(names, callback) {
  let maxIndex = 0;
  
  for (let i = 1; i < names.length; i++) {
    if (names[i].length > names[maxIndex].length) {
      maxIndex = i;
    }
  }
  callback(names[maxIndex]);
}
//this function passed in as an arg is is anonymous
longNames(["Alexander", "Christopher", "Anastasia", "Gabrielle"], function(index) {
  console.log("The longest name here is:", index);
});
```

### Hoisting anon functions
Anonymous functions are unique in that they are moved to the top of their containing scope during the compilation phase, before the code is executed. This means that you can use the function or before it's declared.

```js
functionA(); // This works even though foo is declared later in the code
function functionA() { 
  console.log("Hello, world!");
}
```
Function expressions are not hoisted to the top. Example:

```js
functionB(); // This would result in error because function is not defined yet
var functionB = function() {
  console.log("Here I Am!");
};
```

## Arrow functions 

`Arrow functions` are a different syntax of function that behaves similarly to normal functions. Is main advantage is that its syntax very short, its strength is being able to fit on one line (including its execution code).

```js
[1,2,3].forEach(function(num){
  console.log(`num: `, num);
});
```
Here is the same anonymous callback function from above, but this time utilizing the arrow function syntax
```js
[1,2,3].forEach((num) => {
  console.log(`num: `, num);
});
```
Arrow functions commonly have very short execution code, so it can be refactored into one line, here is the same function but refactored:
```js
[1,2,3].forEach((num) => {console.log(`num: `, num);});
```
Actually an even shorter syntax for an arrow function in a single line omits the use of curlybrackets `{}`. It is implicit that anything following the arrow `=>` represents the code that the function will execute. If there is only one parameter being passed into the arrow function, you can remove the brackets `()` representing our arguments before the arrow `=>` for readability. However, if passing in 2 parameters, braces are recommended such as '(time, date)'
```js
[1,2,3].forEach(num => console.log('num: ', num));
```

### Larger Arrow Fucntion syntax

Arrow functions be as large as normal function expressions, or anon functions.  Here is an example
```js
const calculate = (a, b, operation) => {
  let result;
  if (operation === '+') result = a + b;  
   else if (operation === '-') result = a - b;  
   else if (operation === '*') result = a * b;
   else if (operation === '/') result = a / b;
   else  result = 'Invalid operation';  
  return result;
};
console.log(calculate(16, 4, "+")); // Output: 64
```
Note: Arrow functions dont get assigned a value that the method `this.` can use. So you wont find many uses of the method inside an arrow function. Arrow functions inherit thier scope from the object they are called.

##  Vim Terminal Text Editor
[Check big Terminal and Git Note file](Terminal-and-git-notes.md)

# `Week 3`

## Object Methods
Object methods are `functions` that are defined as a property within an object. They are commonly used to perform operations to the datastructure within the object it resides.A method has access to the datastructure and can self reference itself using the `this` keyword.
Methods are invoked by calling them through dot notation. Example : `person.fullname();`
```js
const person = {
  firstName: 'Abraham',
  lastName: 'Lincoln',
  fullName: function() {
    return person.firstName + ' ' + person.lastName;
  }
};
console.log(person.fullName()); // Output: "Abraham Lincoln"
```


## This
`this` is a dynamically scoped keyword that is context dependant. Usually it refers to the object or function it is being called within. Below is an example where `this` is referring to the object it is scoped within. In this case it is the fantasyNovel object.

```js
const fantasyNovel = {
  chapters: { 1 : "Life at Home",
              2 : "Call to Adventure",
              3 : "Ignoring the Call",
              4 : "Crossing the Threshold",
              5 : "Conflict",
              6 : "Reward",
              7 : "Return to the Kingdom"
  },
  whereILeftOff :function(bookmark){
    console.log(this.chapters[bookmark]);//`this` is referring to fantasyNovel
  }
}
book.whereILeftOff(4);
```
Reminder:<br>
When using `this` within an arrow function it will 


## Recursion
Recursion is when a function calls upon itself. This is commonly used as a substitute instead of a `for` or `while` loop in certain cases.<br> 

Recursive loops require a `base case`, and a `recursive case` for proper looping, otherwise we could not get it to run at all, or get a stack overflow.<br>
The `recursive case` is what will will allow the loop to continue<br>
The `base case` is the condition that will cause the loop to exit <br>


```js
function countEvenToTwelve(number) {
  if (number <= 12) { // Recursive Case, runs as long as its true
    console.log(number);    
    countEvenToTwelve(number+2);// function calls itself
  }
  // Base case is implicit here, do nothing when number reaches 12
}
countEvenToTwelve(0);
```
Here is another example of a recursive loop that `returns` the value into itself to continue
```js
function sumToOne(n) {
  if (n === 1) {// base case, exits the loop and no longer calls itself
    console.log(n);
    return 1;
  }
console.log(n);
  return n + sumToOne(n - 1);//recursive case, will run infinitely if there is no base case
}
console.log(sumToOne(4));
```
In this example we are attempting to flatten nested arrays. Our recursive case plugs back our array it back into our function when it encounters a nested array and print its items individually
```js
const printItems = function(array) {
  array.forEach((item) => {
    if (Array.isArray(item)) {      
      printItems(item); //our recursive case, runs function again and passes in the subarray
    } else {
      console.log(item);
    }//our base case is implied when it reaches the end of array
  });
}
const arrayB = ["A", ["B", "C"], "D", "E"];
printItems(arrayB); // results in a flat array => ["A", "B", "C", "D", "E"]
```

## Modules
`Node.js` is the runtime we've been running our javascript files in. Within node, every file we've been running is actually its own module. Files are implicitly modules. <br>

By default when we `console.log(module)` to see what our current file's module is like, we notice information like the paths and we can notice that `exports` is an empty object.
```js
//firstFile.js
console.log(module);
//this is the output in console
 Module {
  id: '.',
  path: '/home/labber/lighthouse/focal',
  exports: {},    //  <- Notice how exports is empty
  parent: null,
  filename: '/home/labber/lighthouse/focal/firstFile.js',
  loaded: false,
  children: [],
  paths: [
    '/home/labber/lighthouse/focal/node_modules',
    '/home/labber/lighthouse/node_modules',
    '/home/labber/node_modules',
    '/home/node_modules',
    '/node_modules']}
```
If we clear and setup our firstFile.js like this:
```js
//firstFile.js
const goodMorning = function(person) {
  console.log(`Good Morning ${person}! How are you doing?`);
}
```
In order for modules to communicate across modules and pass information to one another we need to add `require` keyword and pass the file into our second file.<br>
<i>-Technically adding .js to the filename is not required as its implicit-</i>
```js
//secondFile.js
const goodMorning = require('./firstFile.js');
//this assumes we have a file in our directory named firstFile.js
//Note: we can define the location using relative paths ^
goodMorning("Kathy");
```
Our output will still not be functioning correctly. We are still returning an empty object from firstFile.js. In order to remedy this we need to add `module.exports` and define our function.
```js
//firstFile.js
const goodMorning = function(person) {
  console.log(`Good Morning ${person}! How are you doing?`);
  module.exports = goodMorning;
}
```

## NPM and definitions
`NPM `is a package manager used for downloading open-source `packages` so that node.js can have a greater functionality. Packages are self contained `libraries` that may or may not include dependencies, ie packages that <b>They</b> also rely on to function properly.<br>

`Package` is a collection of JS modules commonly paired with a package.json file, many of them are made open-source on NPM

A `library` is a bit different from a package, they are independant collections of ready made code that can be downloaded for developers to use in thier programs (not specific to Javascript).

`package.json` are an outline of the packages properties, and details, often containing `scripts` and other info.

Often looks like this example, and appears similar to objects in .js files<br> Hence the name <i>Java-Script-Object-Notation</i>
```json
{
  "name": "project-name",
  "version": "1.0.0",
  "description": "Short project summary",
  "main": "index.js",
  "scripts": {
    "myscript": "ENV=development node index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "MIT",
  "dependencies": {
    "express": "^4.13.4"
  }
}
```
`package-lock.json` is a list of all of the depencies for this project. This file and `package.json` should be included when checking projects into git

`node_modules` folder is often ignored with a .gitignore rule as we dont want to include that in our repos.

To create a .gitignore pwd to your repo and `$ touch .gitignore`. Open the .gitignore in VSC and if you want to ignore files with .log extension and a directory named node_modules, your .gitignore file would look like this:
```
*.log
node_modules/
```
After saving, git will ignore the files and directories when you perform Git operations like `git add`, `git commit`, and `git status`.

[Heres a useful resource on gitignore](https://github.com/github/gitignore?tab=readme-ov-file#a-collection-of-gitignore-templates)

### Installing packages with NPM
Cd into our working directory and run `$ npm init` <br>
It asks a series of initialization questions when generating the package.json, this can be edited later. 

We can run `$ npm install chalk@4.1.2` to install chalk in our pwd at a specified version by defining it with `@4.1.2`



### Require
Remember to include require our `require` somewhere within our .js files so that we can import functionality of the installed packages into our projects.

```js
const chalk = require("chalk");
const message = `${chalk.red("Red,")} ${chalk.green("Green,")} ${chalk.blue("Blue")}`;
console.log(message); //=> Red, Green, Blue! 
//Now our letters are rgb shaded in console
```



## Unit Testing
Unit testing is the practice of writing code to programmatically test the actual code we want to write.


## with Mocha and Chai

## Object Oriented JS
sunday asdasdasd












# Week 4

## aa


## bb 


## cc 


## dd


































<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
# extra unsorted stuff

note during the LHL Git and GitHub Account Setup
  
  make sure the terminal in VSC is set to the LHL Linux Terminal
  an error was made when attempting to use the default windows one

practice setting up new github account and getting ssh key process locked down, to not be clueless on process ever again

useful references
http://rogerdudler.github.io/git-guide/files/git_cheat_sheet.pdf
http://rogerdudler.github.io/git-guide/
