## Questions for exam

Topic: **Node.js, V8 engine, NPM, Version system, and Module system**

1. What is Node.js? What is the V8 engine? How does Node.js use the V8 engine to execute JavaScript code, and how does it contribute to its performance?

    **Answer:** V8 is Google’s open source high-performance JavaScript and WebAssembly engine, written in C++. Node.js is a JavaScript runtime built on top of the V8 JavaScript engine. It allows developers to run JavaScript on the server to build network applications, using JavaScript as the programming language on both the front-end and back-end. Node.js uses V8 to execute JavaScript code on the server side. When a developer writes JavaScript code for a Node.js application, the code is passed to V8 for execution.

2. Explain the significance of NPM in the Node.js ecosystem and why it is considered a crucial tool.
    
    **Answer:** The package manager in the Node.js ecosystem is NPM (Node Package Manager). It is a command-line tool and a vast repository of reusable code modules and libraries. NPM allows developers to easily manage dependencies and integrate third-party functionality into their Node.js applications.
3. What is versioning in software development? Describe the MAJOR, MINOR, and PATCH versioning system commonly used in package management.
    
    **Answer:** The Node Package Manager (npm) ecosystem uses Semantic Versioning as the standard for version numbers which follows the convention of MAJOR.MINOR.PATCH. This is to differentiate between versions that introduce major breaking changes, minor backwards-compatible changes, and patch changes for small fixes.
4. How do you use modules in JavaScript? How can you write your own module? Provide an overview of the module system in Node.js.
    
    **Answer:** Module in Node.js is a simple or complex functionality organized in single or multiple JavaScript files which can be reused throughout the Node.js application. Built-in Modules, Local modules, Third-party modules. Node.js has two module systems: CommonJS (`require()`, and variables and functions export from a CommonJS module with `module.exports`) modules and ECMAScript (`import` and `export` statements) modules. Authors can tell Node.js to use the ECMAScript modules loader via the .mjs file extension, the package.json "type" field. ES modules are the standard for JavaScript, while CommonJS is the default in Node.js
5. What are global modules in Node.js, and how do they differ from local modules? How do you interpret version specifications like "1.2.3", "~3.2.0", or "^2.1.0"?
   
    **Answer:** Generally, modules are scoped inside the project directory only, it means you can’t use them outside the project. But as global modules are installed on the computer (mostly root location), they can easily be used anywhere in our system. 
Install a module locally if you're going to require() it. Install a module globally if you're going to run it on the command line. ~1.2.3 is equivalent to >=1.2.3 <1.3.0; ^1.2.3 is equivalent to >=1.2.3 <2.0.0
```shell
npm install <module>
npm install <module> --global
```

Topic: **JavaScript Basics**

6. What is the difference between regular functions and arrow functions in JavaScript? How are they used, and when should you prefer one over the other?

   **Answer:** Differences:
   - `this` value: `this` value inside a regular function is dynamic and depends on the invocation. But `this` inside the arrow function is bound lexically and equals to `this` of the outer function.
   - constructors: an arrow function cannot be used as a constructor.
   - `arguments` object: arguments object inside the regular functions contains the arguments in an array-like object. The arrow function, on the opposite, doesn't define arguments (but you can easily access the arrow function arguments using a rest parameter `...args`).
   - implicit return: if the arrow function has one expression, then the expression is returned implicitly, even without using the `return` keyword.
   - methods: you can define methods using the arrow function syntax inside classes. Arrow methods bind `this` value to the class instance. Anyhow the arrow method is invoked, `this` always equals the class instance, which is useful when the methods are used as callbacks.
   - hoisting: arrow functions cannot be accessed before initialization.
   - duplicate named parameters: arrow functions can never have duplicate named parameters, whether in strict or non-strict mode.
```javascript
function regularFunction(param) {
    // Function body
    return param;
}
const arrowFunction = (param) => {
    // Function body
    return param;
};
```
7. Explain the difference between `let` and `const` in JavaScript, including their scoping rules and immutability features.

   **Answer:** `const` is a signal that the identifier won’t be reassigned. `let` is a signal that the variable may be reassigned. It also signals that the variable will be used only in the block it’s defined in, which is not always the entire containing function.
8. What are the different data types in JavaScript? Provide examples of each data type.

   **Answer:**
   - String
   - Number
   - Bigint
   - Boolean
   - Undefined
   - Null
   - Symbol
   - Object (object, array, date)
9. How does hoisting work in JavaScript, and how can it affect variable declarations and function definitions?
  
   **Answer:** hoisting is a concept where a variable or function is lifted to the top of its global or local scope before the whole code is executed. This makes it possible for such a variable/function to be accessed before initialization. All functions and variables in JavaScript are hoisted, but only declared functions can be accessed before initialization. Variables declared with `let` and `const` are hoisted, but they cannot be accessed before the line they are initialized.
10. Describe how logical operations work in JavaScript, and name all the object methods available for Boolean objects.

    **Answer:** there are four logical operators in JavaScript: `||` (OR), `&&` (AND), `!` (NOT), `??` (Nullish Coalescing). `??` returns the first argument if it’s not null/undefined. Otherwise, the second one. For Boolean objects, there are several methods available:
    - `Boolean.prototype.toString()` - a string representation of the Boolean object's value ("true" or "false").
    - `Boolean.prototype.valueOf()` - primitive value (Boolean) of the Boolean object.

Topic: **Objects and Functions**

11. How do objects look like in JavaScript, and what are property descriptors associated with object properties?

    **Answer:** an object is a collection of key-value pairs, where keys are strings (or Symbols) and values can be of any data type, including other objects or functions. Objects allow you to group related properties and methods together, providing a structured way to represent real-world entities or concepts. A property descriptor of an object consists of some of the following attributes to define each property:
    - value: the value associated with the property that is called.
    - writable: indicates if the property can be changed or not. It only returns true if the property can be manipulated.
    - enumerable: if the property is visible during enumeration of the properties of the corresponding object, then it returns true. 
    - configurable: indicates if the property descriptor can be changed or removed from the corresponding object.
```javascript
const obj = {
    property1: 2
};
Object.defineProperty(obj, "property1", {
    value: "Hello",
    writable: false,
    enumerable: true,
    configurable: true
});
const descriptor1 = Object.getOwnPropertyDescriptor(obj, 'property1');
```
![Untitled.png](file%2FUntitled.png)

12. What is a deep clone of an object, and how can you proceed to create one in JavaScript?

    **Answer:** a deep copy is a copy of all elements of the original object. Changes made to the original object will not be reflected in the copy. BFS (Breadth-First Search) and DFS (Depth First Search). Ways:
    - Using `JSON.parse()` and `JSON.stringify()`
    - Using a Recursive Approach
    - Using External Libraries (lodash)
```javascript
export const deepCloneObject = (obj) => {
    if (typeof obj != 'object' || obj == null) {
        return obj;
    }
    const result = {};
    const keys = Object.keys(obj);
    for (let key in keys) {
        result[keys[key]] = deepCloneObject(obj[keys[key]]);
    }
    return result;
}
```
13. Explain the CommonJS module system and how it is utilized in Node.js to organize and share code between different files.

    **Answer:** the CommonJS module format specifies a way to define a module using a `require()` function to load modules and `module.exports` or `exports` object to expose functionality. Files with a .js extension when the nearest parent package.json file contains a top-level field `type` with a value of `commonjs`.
14. How do you create and export a module in Node.js, and how do you import it into another file using `require`?

    **Answer:** 
```javascript
const circle = require('./circle.js');
exports.area = (r) => PI * r ** 2;
module.exports = add
```
15. Describe the roles of the "require" function in Node.js when dealing with modules, and how does it help manage dependencies?

    **Answer:**  the `require()` function will return an object, function, property or any other JavaScript type, depending on what the specified module returns.
16. What is the difference between "exports" and "module.exports" in a Node.js module? How can you use them to expose functionalities?

    **Answer:** in Node.js, `module` is a plain JavaScript object with an `exports` property. `exports` is a plain JavaScript variable that happens to be set to `module.exports`. When you require a module in another file, the code within that module is executed, and only `module.exports` is returned. When should you choose `exports` over `module.exports`? The short answer is that you probably shouldn't. While `exports` may be shorter and seem more convenient, the confusion it can cause is not worth it. Remember that `exports` is just a reference to `module.exports`, and assigning a new object to `exports` breaks that reference.
![img.png](file%2Fimg.png)

    In summary, the key difference is that `exports` is a shorthand reference to `module.exports`, and you can attach properties and methods to it, while `module.exports` is the actual object that determines what is exported when a module is required. If you want to replace the entire exported object, you should use `module.exports`. If you just want to attach properties or methods to the existing export, you can use `exports`.
17. What is the difference between "exports" and "require" in a Node.js module? How are they related to each other in the module system?

    **Answer:** `exports` is used within a module to expose functionality to other parts of your application, while `require` is used to import functionality from other modules into your current module. These two concepts work together to create a modular structure in your Node.js application, promoting code reusability and maintainability.
```javascript
const circle = require('./circle.js');
exports.area = (r) => PI * r ** 2;
module.exports = add
```

Topic: **Type Conversion**

18. What is type conversion in JavaScript, and why is it necessary? Provide examples of implicit and explicit type conversions.

    **Answer:** There are two types of type conversion in JavaScript:
    - implicit Conversion - automatic type conversion.
    - explicit Conversion - manual type conversion (done using built-in methods).
```javascript
let result = '3' + 2; 
console.log(result) // "32"
//and
result = Number('324'); //String(), Boolean()...
console.log(result); // 324
```

19. Explain the concept of truthy and falsy values in JavaScript and how they relate to boolean conversions.

    **Answer:** when non-boolean values are used in a boolean context, such as the condition of an if statement, they will be coerced into either true or false. Values that are coerced into true are called truthy and values that are coerced into false are called falsy.
    JavaScript contains the following falsy values:
    - false
    - 0, -0 and 0n
    - "", '' (empty strings)
    - null, undefined and NaN 
    - document.all

    All other values are truthy.
20. How can you convert a variable of type string to a number in JavaScript using built-in functions like `Number()`, `parseInt()`, and `+` (unary plus)?

    **Answer:**
```javascript
const str = "25";
const a = Number(str);
const b = parseInt(str);
const c = +str;
```

Topic: **Function Concepts**

21. What is an IIFE (Immediately Invoked Function Expression) in JavaScript, and what problem does it solve? Provide an example of its usage.

    **Answer:** an IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined. The plan is that once we’ve created an IIFE, we have no intention of calling the function again. Use cases:
    - avoid polluting the global namespace
    - execute an async function
    - the module pattern
```javascript
(function () {
    // …
})();

(() => {
    // …
})();

(function() {
 var x = 20;
 var y = 20;
 var answer = x + y;
 console.log(answer);
 })();
```

22. How do you define a function in JavaScript? Provide examples of both function declarations and function expressions.

    **Answer:** 
```javascript
function square(number) {
  return number * number;
}

const square = function (number) { //expression declaration
    return number * number;
};
```
23. Can a function in JavaScript accept multiple arguments? If yes, how do you pass and handle them within the function?

    **Answer:**  we can handle it in two ways:
    - `arguments` object (ES5) - is a local JavaScript object variable that is available in all non-arrow functions. arguments is an Array-like object accessible inside functions that contain the values of the arguments passed to that function.
    - rest parameters `...args` (ES6) - provides an easier and cleaner way of working with an indefinite number of arguments.
    
    The main difference between rest parameters and the `arguments` object is:
    - all the array methods like map, sort, and filter can be applied directly on the rest parameters array but not on the `arguments` object. To use Array methods on the `arguments` object, it must be converted to a real array first.
    - the `arguments` object is not available in arrow functions.
```javascript
function foo() {
  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}
function my_log(...args) {
    // args is an Array
    console.log(args);
    // You can pass this array as parameters to another function
    console.log(...args);
}
```
24. Provide an example of a closure in JavaScript and explain how it works.

    **Answer:** closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

```javascript
const add = (function () {
  let counter = 0;
  return function () {counter += 1; return counter}
})();

add();
add();
add();
```

Topic: **Pure Functions and Immutability**

25. What is a pure function in JavaScript, and what characteristics define a function as "pure"? How do pure functions relate to immutability in JavaScript?

    **Answer:** is a function that always returns the same result if the same arguments are passed (idempotent). It does not depend on any state or data change during a program’s execution. Rather, it only depends on its input arguments. Also, a pure function does not produce any observable side effects such as network requests or data mutation, etc. Pure functions don't modify their input. They treat the input values as immutable. Advantages:
    - More readable 
    - Better for optimisation 
    - Better for testing
26. Describe the concept of named immutable methods in JavaScript and provide examples of such methods. 

    **Answer:** the concept of named immutable methods refers to a programming pattern where methods are designed to perform operations on data without modifying the original data. Instead of directly altering the existing data, these methods return new copies or instances with the desired changes applied. Here are some examples of named immutable methods in JavaScript:
    - Array.prototype.map()
    - Array.prototype.concat()
    - String.prototype.slice()
27. Provide an example of a Higher-Order Function in JavaScript and explain how it can accept another function as an argument.

    **Answer:** higher order function is a function that takes one or more functions as arguments, or returns a function as its result.
```javascript
function callbackFunction(){
    console.log('I am  a callback function');
}

// higher order function
function higherOrderFunction(func){
    console.log('I am higher order function')
    func()
}

higherOrderFunction(callbackFunction);
```
28. How do you pass arguments to a function in JavaScript, and how can a function return a value?

    **Answer:** rest parameters parameters, default parameters values, rest parameters `...args`, `arguments` object.

Topic: **Function Composition and Array Methods**

29. What is currying in JavaScript, and how does it help with function composition? Provide an example of currying.

    **Answer:** currying is a transformation of functions that translates a function from callable as `f(a, b, c)` into callable as `f(a)(b)(c)`. Currying in JavaScript transforms a function with multiple arguments into a nested series of functions, each taking a single argument. Currying helps you avoid passing the same variable multiple times, and it helps you create a higher order function.
```javascript
function curry(f) { // curry(f) does the currying transform
  return function(a) {
    return function(b) {
      return f(a, b);
    };
  };
}

// usage
function sum(a, b) {
  return a + b;
}

let curriedSum = curry(sum);

alert( curriedSum(1)(2) ); // 3
```
30. Provide an example of function composition and describe its advantages over nested function calls.

    **Answer:** function composition is a powerful technique used in programming to combine multiple functions into a single, more complex function. It allows developers to create more efficient and reusable code by breaking down complex operations into smaller, more manageable pieces. Advantages of Function Composition:
    - Readability and Clarity
    - Reusability 
    - Modularity 
    - Flexibility and Extensibility 
    - Testability

    In contrast, nested function calls can lead to "callback hell," reduced code readability, and make it harder to reason about complex behaviors. Function composition provides a more structured and organized way to combine functions, leading to cleaner and more maintainable code.
```javascript
let hello = (x) => `Hello, ${x}`;
let toUpperCase = x => x.toUpperCase();
let greeting = x => hello(toUpperCase(x));

function outerFunction(outerParam) {
    console.log("Outer function is called with:", outerParam);

    function innerFunction(innerParam) {
        console.log("Inner function is called with:", innerParam);
    }

    // Call the inner function
    innerFunction("Inner parameter value");
}
```
31. Describe various array methods such as map, filter, reduce, and forEach, and provide examples of their usage.

    **Answer:**
```javascript
a.every(x => x%2 === 0) // true, when all elements folow this rule
a.some(x => x%2 === 0) // [2,4] -> true, [2,3] -> true, [1,3] -> false
a.map(x => x*x)
a.filter(x => x%2 === 0)
a.reduce((acc, item) => item * acc, 1)
a.forEach(x => console.log(x))
```
32. How do you create and initialize objects using object literals and the "new" keyword in JavaScript? How can you access, modify, and delete object properties?

    **Answer:** creating and Initializing Objects:
    - Object Literals
    ```javascript
    const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    isStudent: false
    };
    ```
    - Using the "new" Keyword
    ```javascript
    function Person(firstName, lastName, age, isStudent) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
        this.isStudent = isStudent;
    }
    const person = new Person("John", "Doe", 30, false);
    ```
    Accessing, modifying, deleting adding:
    ```javascript
    console.log(person.firstName);
    person.age = 31;
    delete person.isStudent;
    person.city = "New York";
    person["country"] = "USA";
    Object.getOwnPropertyNames();
    Object.defineProperty();
    Object.defineProperties();
    ```

Topic: **Prototypes and Object-Oriented Programming**

33. What is the prototype in JavaScript, and how does it work with objects? Explain the prototype chain.

    **Answer:** all JavaScript objects inherit properties and methods from a prototype. When we call myObject.toString(), the browser:
    - looks for toString in myObject 
    - can't find it there, so looks in the prototype object of myObject for toString 
    - finds it there, and calls it.

The prototype chain is a mechanism that allows objects to inherit properties and methods from other objects. Every object can have exactly one prototype object. That prototype object can also have a prototype object, and so on, creating a chain of inheritied properties and methods. The end of this chain is called the null prototype.

```javascript
const animal = {
    dna: 'ATCG',
};

const dog = {
    face: '🐺',
}

Object.setPrototypeOf(dog, animal);
Object.getPrototypeOf(dog) === animal; // true
Object.getPrototypeOf(animal) === Object.prototype; // true
Object.getPrototypeOf(Object.prototype) === null; // true

function Student() {
    this.name = 'John';
    this.gender = 'M';
}

var studObj = new Student();

console.log(Student.prototype); // object
console.log(studObj.prototype); // undefined
console.log(studObj.__proto__); // object

console.log(typeof Student.prototype); // object
console.log(typeof studObj.__proto__); // object

console.log(Student.prototype === studObj.__proto__ ); // true
```
34. How do objects, prototypes, and property descriptors tie together to form the foundation of object-oriented programming in JavaScript?

    **Answer:** we have an object linked to a prototype. Prototypes contain all methods and these methods are accessible to all objects linked to this prototype. This is called Prototypal Inheritance (or Prototypal Delegation).
    There are three main ways to implement Prototypal Inheritance:
    - Using Constructor Functions
    ```javascript
    function User(name){
        this.name = name;

        // never create function inside constructor function
        this.printName = function(){
        console.log(this.name);
        }
        console.log(this);
    }
    
    // or
    User.prototype.printName = function(){
	    console.log(this.name)
    }

    let kedar = new User("kedar")
    ```
    - Using ES6 Classes
    ```javascript
    class User{
	    constructor(name){
    	    this.name = name
        }
    
        printName(){
            console.log(this.name);
        }
    }

    const kedar = new User("kedar")
    ```
    - Using Object.create() - returns a new object with the specified prototype object and properties.
    ```javascript
    const User = {
        init(name){
            this.name = name
        },
    
        printName(){
            console.log(this.name);
        }
    }

    let kedar = Object.create(User)
    kedar.init("kedar")
    kedar.printName()
    ``` 
35. How do you create an object in JavaScript using constructor functions or classes? Provide examples of both approaches.

    **Answer:**
```javascript
// 1 way: obj -> Object.prototype -> null
let obj = {a: 1};

// 2 way: newObj -> obj -> Object.prototype -> null
const newObj = Object.create(obj)

// 3 way: ES6 classes
class Rectangle {
	constructor(height, width){
		this.height = height;
		this.width = width;
	};
	getArea = () => this.width * this.height;
}
// 4 way: constructor func
function Person(firstName, lastName, age, isStudent) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    this.isStudent = isStudent;
}
const person = new Person("John", "Doe", 30, false);
```
36. Explain the attributes in a property descriptor, such as value, writable, enumerable, and configurable.

    **Answer:** Property attributes:
    - `[[Value]]` - value of field
    - `[[Get]]` - for getter (that’s why can be undefined)
    - `[[Set]]` - for setter (that’s why can be undefined)
    - `[[Writable]]` - default: true - can we rewrite the value
    - `[[Enumerable]]` - default: true - can we use with `for in`
    - `[[Configurable]]` - default: true - if false: not deletable, makes writable and enumerated = false, makes get and set false
37. What are accessor properties, and how can you define them using get and set in property descriptors?

    **Answer:** Descriptors for accessor properties are different from those for data properties. For accessor properties, there is no value or writable, but instead there are get and set functions. That is, an accessor descriptor may have:
    - get – a function without arguments, that works when a property is read
    - set – a function with one argument, that is called when the property is set 
    - enumerable – same as for data properties
    - configurable – same as for data properties
```javascript
//accessor descriptors
let user = {
  name: "John",
  surname: "Smith"
};

Object.defineProperty(user, 'fullName', {
  get() {
    return `${this.name} ${this.surname}`;
  },

  set(value) {
    [this.name, this.surname] = value.split(" ");
  }
});

//getter and setter
let user = {
    name: "John",
    surname: "Smith",

    get fullName() {
        return `${this.name} ${this.surname}`;
    },

    set fullName(value) {
        [this.name, this.surname] = value.split(" ");
    }
};
```
Topic: **Arrays**

38. Explain the difference between the splice and slice methods in JavaScript arrays. How are they used, and what are the key distinctions in their behavior? Provide examples to illustrate their usage.

    **Answer:** `slice` returns a piece of the array but it doesn’t affect the original array. `splice` changes the original array by removing, replacing, or adding values and returns the affected values.
```javascript
array.slice(startIndex, endIndex) //array of the values found between start and end excluding the value at end
array.splice(startIndex, deleteCount, newElem1, newElem2, newElemN);
// startIndex denotes the index from which the method will start its operation on the array.
// deleteCount denotes the number of values to be deleted from the start. If the value is 0, nothing will be deleted.
// newElem1 to newElemN denote the values that would be added after the start.
```
39. How can you loop through an array using a for loop, and what are the benefits of using array methods like forEach instead?

    **Answer:** `for`does not provide a facility for modification during iteration, but it is faster in performance; `forEach` cannot provide a facility to break the statement because of the callback method. The `for` loop consumes less execution time and is helpful in solving complex problems.
```javascript
//for...of
for(let value of a){
	console.log(value);
}

//for...in
for(let key in a){
	console.log(key); //just indexes (keys)
}

//for i
for(let i = 0; i<10; i++){
    
}

arr.forEach()//has the property of accessing both the index and value of each element
```
40. How do you create a multidimensional array in JavaScript, and how do you access and modify elements in such arrays?

    **Answer:** a multidimensional array in javascript is an array that has one or more nested arrays (array of arrays, matrix). There are two ways to create a multidimensional array in JavaScript:
    - Using array literal
    ```javascript
        var Employee = [
            [20, 'Pranshu', 'Lucknow'],
            [21, 'Sameer', 'Vanaras'],
            [22, 'Kartikey', 'Lakhimpur']
        ]
        //access
        console.log(x[0]); // [20, ‘Pranshu’, ‘Lucknow’]
        console.log(x[0][1]); // Pranshu
        //modify
        Students[1][3] = 'Day-Scholar';
        Students[1].push('Day-Scholar');
        //iterating
        studentsData.forEach((student) => {
            student.forEach((data) => {
                console.log(data);
            });
        });
    ```
    - Using array constructor
    ```javascript
        var Employee = Array(
            [20, 'Pranshu', 'Lucknow'],
            [21, 'Sameer', 'Vanaras'],
            [22, 'Kartikey', 'Lakhimpur']
         )
    ```
Topic: **Strings and Template Strings**

41. What are strings in JavaScript, and how do you create a string variable? Describe the difference between single quotes (''), double quotes ("") and backticks (``) when defining strings.

    **Answer:**
```javascript
const literal = `literal ${value}`
const single = 'single'
const double = "double"
const str = 'This is the first line \nThis is the second'
const s = 'You can\'f' // escaping
const str = "You can't" // don't need to escape single quote
const str2 = 'This is a quote:"..."' // don't need to escape double quote
```
42. What are template strings (or template literals) in JavaScript, and how are they different from regular strings? How do you create a template string, and what benefits do they offer over traditional strings?

    **Answer:** template literals are literals delimited with backtick (`) characters, allowing for multi-line strings, string interpolation with embedded expressions, and special constructs called tagged templates. Template literals are sometimes informally called template strings, because they are used most commonly for string interpolation.
```javascript
`string text`
    `string text line 1
     string text line 2`
    `string text ${expression} string text`
tagFunction`string text ${expression} string text`

const classes = `header ${
    isLargeScreen() ? "" : item.isCollapsed ? "icon-expander" : "icon-collapser"
}`;
const person = "Mike";
const age = 28;

function myTag(strings, personExp, ageExp) {
    const str0 = strings[0]; // "That "
    const str1 = strings[1]; // " is a "
    const str2 = strings[2]; // "."

    const ageStr = ageExp > 99 ? "centenarian" : "youngster";

    // We can even return a string built using a template literal
    return `${str0}${personExp}${str1}${ageStr}${str2}`;
}

const output = myTag`That ${person} is a ${age}.`;

console.log(output);
// That Mike is a youngster.
```
43. Describe how you can use String methods like toUpperCase, toLowerCase, trim, split, indexOf, substring, etc., to manipulate and extract information from strings.

    **Answer:**
```javascript
let re = /[A-Z]/;
let str = 'hi There! How are you?';
let index = str.search(re); // 3

let str = 'finding substring in string';
let index = str.indexOf('str'); //11

const str = 'Hello';
const substr = str.slice(3); // 'lo'
```
44. How can you concatenate strings in JavaScript using traditional methods, and how does it compare to concatenation with template strings? Provide examples of both approaches.

    **Answer:** there are four methods or ways by which we can concatenate strings in JavaScript:
    - using the `concat()` method - `String.concat()` method accepts a list of strings as parameters and returns a new string after concatenation i.e. combination of all the strings. If the parameters are not strings, the `concat()` method firstly converts them into strings and then concatenation occurs. As we know that strings in JavaScript are immutable, so the `concat()` method doesn't modify the input strings but returns a new string that has all the input strings concatenated.
    - using the '+' operator 
    - using the array `join()` method - the separator can be user-customized and by default, if not specified, it uses the (,) comma as a separator.
    - using template literals
    
45. What is the difference between a tagged template literal and a regular template literal? How can you use tagged template literals to customize string interpolation behavior?

    **Answer:** tags allow you to parse template literals with a function. The first argument of a tag function contains an array of string values. The remaining arguments are related to the expressions. The tag function can then perform whatever operations on these arguments you wish, and return the manipulated string. regular template literals provide simple string interpolation, while tagged template literals allow you to customize the interpolation process by using a tag function.
```javascript
const person = "Mike";
const age = 28;

function myTag(strings, personExp, ageExp) {
    const str0 = strings[0]; // "That "
    const str1 = strings[1]; // " is a "
    const str2 = strings[2]; // "."

    const ageStr = ageExp > 99 ? "centenarian" : "youngster";

    // We can even return a string built using a template literal
    return `${str0}${personExp}${str1}${ageStr}${str2}`;
}

const output = myTag`That ${person} is a ${age}.`;

console.log(output);
// That Mike is a youngster.
```