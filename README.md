# Javascript (ES6) Basics For iOS Developers

> Note: When in doubt, just try something. Chances are the code is going to be the same or similar to swift. <http://i.imgur.com/AwYW1jY.jpg>

## Variables

Like Swift and Objective-C, Javascript uses variables and constants to store and refer to values.

In modern Javascript, we declare a new variable using one of the following keywords:

* `let` to create a new variable.
* `const` to create a new constant.
* `var` the old way of creating variables. We won't use `var`.


| Javascript | Swift|
| --- | --- |
| `let`  | `var`  |
| `const`  | `let`  |
| `var`  | Doesn't exist in swift |

This can be a little confusing because we're used to `let` being a constant. Just remember that `let` will create a variable, not a constant, in Javascript.

*Swift:*

```swift
var currentTemperature = 14
let hoursInADay = 24
```

*Javascript:*

```js
let currentTemperature = 14;
const hoursInADay = 24;
```

[Javascript variables](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript#Variables)

## Types

[Javascript types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

Types are the kind of variables and constants that we are creating. Strings, Integers, Arrays, etc. We haven't told Javascript what kind of variable we are creating, we just create the variable and assign a value to it. Javascript uses these values to assume what kind of variable you wanted to create. 

```js
let myVariable = 1; // Number
const myConstant = "1"; // String
```

We can check the type of a variable by using the `typeof` operator which returns a string.

```js
console.log(typeof myVariable);
// Prints 'number' to the console
```

> `console.log()` is the equivilent of `print()` in Swift.


This is similar to the way we create variables in swift, but there are two major differences. 

1. In Swift we can specify a type, in Javascript we cannot.
2. In Swift, once a type has been set, it can never be changed. In Javascript, types can change all the time.

#### Types can change

JavaScript is a loosely typed or a dynamic language. That means you don't have to declare the type of a variable ahead of time. It also means that you can have the same variable as different types:

*Swift:*

```swift
var greeting :String // greeting is now a string forever
greeting = "Hello, world!" // We can assign any string value to greet
greeting = 10 // Assigning any other value to greeting will cause an error
```

*Javascript:*

```js
let greeting; // greeting is defined but has not type. Actually it's type is 'undefined'
greeting = "Hello, world!" // greeting is now a string with the value "Hello, world!"
greeting = 10 // greeting is now a number with the value 10
greeting = String(greeting) // greeting is now a string with the value "10"
greeting = true;  // greeting is now a Boolean
```

#### No explicit types

Every variable in swift has a type weather you specify it or not. If a variable doesn't have a type, your app will not compile.

In Javascript, a variable doesn't have a type until a value is assigned to it and there is no way to explicitly specify a type without assigning a value.

*Swift:*

```swift
var greeting :String // greeting is now a string type
greeting = "Hello, world!" // We can assign any string value to greet
```

*Javascript:*

```js
let greeting; // greeting is defined but has not type. Actually it's type is 'undefined'
greeting = "Hello, world!" // greeting is now a string with the value "Hello, world!"
```

This can lead to some scary code:

*Swift:*

```swift
func sum(array: [Int]) -> Int {
    return array.reduce(0) { (resultSoFar, currentNumber) -> Int in
        return resultSoFar + currentNumber
    }
}

print(sum(array: [1, 2, 3, 4]))
```

*Javascript:*

```js
function sum(array) {
  return array.reduce((resultSoFar, currentNumber) => {
    return resultSoFar + currentNumber;
  });
}

console.log(sum([1, 2, 3, 4]));
```

In swift we have to be very explicit about the type of parameters a function can accept, and the type that it returns. Javascript has none of this safety. So in Javascript, we just have to hope that the person calling the function calls it with an array of numbers and expects a number to be returned. But in reality, anything could be passed into or returned from this function in Javascript. There's nothing stopping us from calling the following code:

```js
sum("some string");
```

> Note: Our app would throw an error when this line of code runs. But there would be no issues until it gets called.

Different types:

* Boolean
* Null
* Undefined
* Number
* String
* Symbol 
* Object

We'll take a look at Numbers, Strings, and Objects.

## Numbers

Javascript doesn't differentiate between the different types of numbers, you just get a 64 bit number. So there's no such thing as an integer in JavaScript, everything's pretty much treated as a double.

### Special numbers

The first two are Infinity and -Infinity, which represent the positive and negative infinities. Infinity - 1 is still Infinity, and so on. Don’t put too much trust in infinity-based computation. It isn’t mathematically solid, and it will quickly lead to our next special number: NaN.

NaN stands for “not a number”, even though it is a value of the number type. You’ll get this result when you, for example, try to calculate 0 / 0 (zero divided by zero), Infinity - Infinity, or any number of other numeric operations that don’t yield a precise, meaningful result.

### Arithmatic

Same as swift `+ - * / =`

## String & Interpolation

* Single and double quotes in javascript. Doesn't matter which, just make sure they match.
* Concatinate strings using +
* Interpolotation using `\`${variable\``


*Swift:*

```swift
let greeting = "Hello"
let name = "Sam"

print(greeting + " " + name) // Hello Sam
print("\(greeting) \(name)") // Hello Sam
```

*Javascript:*

```js
const greeting = "Hello"
const name = "Sam"

console.log(greeting + " " + name) // Hello Sam
console.log(`${greeting} ${name}`) // Hello Sam
```


### String methods

You can find a list of string methods and properties [here](https://www.w3schools.com/jsref/jsref_obj_string.asp). But you can basially acheieve anything in Javascript that you can in swift.

*Javascript:*

```js
const greeting = "Hello"

greeting.length // 5
greeting.toLowerCase() // hello
```

## Objects (Dictionaries)

JavaScript objects can be thought of as simple collections of name-value pairs, so they are similar to dictionaries in Objective-C and Swift. Or tuples in Swift.

```js
{
	key: value,
	anotherKey: anotherValue
};
```

> Note: Remember that JSON stands for JavaScript Object Notation. Also remember that we convert JSON to a dictionary before we us the data in our iOS apps.

Create an empty object:

```js
const myObject = {};
```

Create an object with some default values:

```js
const dog = {
  name: "Fluffy",
  age: 7
};
```

An object's properties can again be accessed in one of two ways:

```js
dog["name"]; // Like a dictionary in Swift
dog.age; // Like an object in Swift

dog.home = "Lighthouse Labs";
dog["age"] = 8;
```

> Note: let and const are only for assignment, all objects in javascript are mutable.

The key part of the object is a JavaScript string, while the value can be any JavaScript value — including more objects. This allows you to build data structures of arbitrary complexity.

```js
const dog = {
  name: "Fluffy",
  age: 7,
  owner: {
  	name: "Larry",
  	pets: ["Fluffly", "George"]
  }
};
```


## Arrays

Arrays in JavaScript are actually a special type of object. They work very much like regular objects (numerical properties can naturally be accessed only using [] syntax) but they have one magic property called 'length'. This is always one more than the highest index in the array.

Create an empty array:

```js
const myArray = [];
```

Create an array with some default values:

```js
const animals = ['dog', 'cat', 'hen'];
```

Access an array:

```js
const totalAnimals = animals.length; // 3
const first = animals[0]; // dog
const last = animals[animals.length - 1]; // hen
const position = animals.indexOf('cat'); // 1
```

Modify an array:

```js
animals.push('duck'); // [ 'dog', 'cat', 'hen', 'duck' ]
animals.unshift('donkey'); // [ 'donkey', 'dog', 'cat', 'hen', 'duck' ]
const duck = animals.pop; // [ 'donkey', 'dog', 'cat', 'hen' ]
const donkey = animals.shift; // [ 'dog', 'cat', 'hen' ]
```

## Control Structers if, while, for, & switch

Control structers in Javascript are very similar to Swift & Objective-C

```js
const name = 'kittens';
if (name == 'puppies') {
  name += ' woof';
} else if (name == 'kittens') {
  name += ' meow';
} else {
  name += '!';
}
name == 'kittens meow';
```

```js
while (true) {
  // an infinite loop!
}
```

```
for (let i = 0; i < 5; i++) {
  // Will execute 5 times
}
```

```js
for (let value of array) {
  // do something with value
}
```

```js
for (let property in object) {
  // do something with object property
}
```

```js
switch (action) {
  case 'draw':
    drawIt();
    break;
  case 'eat':
    eatIt();
    break;
  default:
    doNothing();
}
```

## Opperators and Equality

Opperators in Javascript are pretty much the same as they are in Swift:

`+ - * / =`

`==` is different though. When you use the double equals, javascript compares two values for equality after converting both values to a common type:

```js
123 == '123'; // true
1 == true; // true
```

In this code, `'123'` and `true` will get converted to numbers before being compared. To avoid type coercion, use the triple-equals operator:

```js
123 === '123'; // false
1 === true;    // false
123 === 123    // true
```

> Note: There are also != and !== operators.

## Semicolons

Notice that we are using semicolons in all of the Javascript example. Semicolons are not required in Javascript, but unlike swift, it's good practice to always add a semicolon. 

## Functions

Functions in Javascript are very similar to functions in Swift. You can create functions in javascript using the `function` keyword. 

```js
function greet() {
    console.log("hello")
}

greet() // call the greet function
```

Functions can take parameters and return values. The main difference between swift and javascript is that you don't specify any types in javascript.

*Swift:*

```swift
func welcome(name: String, day: Int) -> String {
    return "Hello \(name), today is the \(day)th."
}

let result = welcome("Anna", day: 11); 
```

*Javascript:*

```js
function welcome(name, day)  {
    return "Hello \(name), today is the \(day)th."
}

const result = welcome("Anna", 11); 
```

## Anonymous Functions

In Swift, we call unamed functions closures. Or the inverse, functions are closures with a name. 

```swift
let wordPrinterClosure = { (word:String)->(Void) in
    print("\(word)")
}
```

In Javascript we just call these anonymous functions and we can declare them using either of the following two syntaxes:

```js
const wordPrinterClosure = function(word) {
    console.log("\(word)");
}
```
```js
const wordPrinterClosure = (word) => {
    console.log("\(word)");
}
```

The second of these two examples, known as a fat arrow function, is the prefered way of declaring an anonymous function.

Both Swift and Javascript have higher order functions, functions that accept another function as a parameter. This is where we most commonly see uses of anonymous functions. Here's an example of using map on an array of numbers in both languages:

*Swift:*

```swift
let numbers = [10, 7, 28, 9, 83, 73, 65, 2, 39]

let numbersMultipliedByThree = numbers.map( { (number: Int) -> Int in
    return number * 3
})

print(numbersMultipliedByThree)
```

*Javascript:*

```js
const numbers = [10, 7, 28, 9, 83, 73, 65, 2, 39];

const numbersMultipliedByThree = numbers.map( (number) => {
    return number * 3
});

console.log(numbersMultipliedByThree);
```

Both languages also have shorthand syntaxes when using their anonymous functions:

*Swift:*

```swift
numbers.map { number in number * 3 }
```

*Javascript:*

```swift
numbers.map( number => number * 3 );
```

## Node Modules

Like #import in Objective-C

To include a module, use the require() function with the name of the module:

```js
// Import the file system module
var fs = require('fs');
```

#### Create Your Own Modules

You can create your own modules, and easily include them in your applications.

The following example creates a module that returns a date and time object:

```js
// datetime.js
exports.myDateTime = function () {
    return Date();
};
```

Use the exports keyword to make properties and methods available outside the module file.

```js
var datetime = require('./datetime');
```

Notice that we use ./ to locate the module, that means that the module is located in the same folder as the Node.js file.

### Node.js file system

The Node.js file system module allows you to work with the file system on your computer.

To include the File System module, use the require() method:

```js
var fs = require('fs');
```

Common use for the File System module:

* Read files
* Create files
* Update files
* Delete files
* Rename files

### Read Files

The fs.readFile() method is used to read files on your computer.


## Extra Resources

* <https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript>