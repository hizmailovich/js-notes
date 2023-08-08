## Questions for exam

Topic: **Node.js, V8 engine, NPM, Version system, and Module system**

1. What is Node.js? What is the V8 engine? How does Node.js use the V8 engine to execute JavaScript code, and how does it contribute to its performance?

    **Answer:** V8 is Google’s open source high-performance JavaScript and WebAssembly engine, written in C++. Node.js is a JavaScript runtime built on top of the V8 JavaScript engine. It allows developers to run JavaScript on the server to build network applications, using JavaScript as the programming language on both the front-end and back-end. Node.js uses V8 to execute JavaScript code on the server side. When a developer writes JavaScript code for a Node.js application, the code is passed to V8 for execution.

2. Explain the significance of NPM in the Node.js ecosystem and why it is considered a crucial tool.
    
    **Answer:** The package manager in the Node.js ecosystem is NPM (Node Package Manager). It is a command-line tool and a vast repository of reusable code modules and libraries. NPM allows developers to easily manage dependencies and integrate third-party functionality into their Node.js applications.
3. What is versioning in software development? Describe the MAJOR, MINOR, and PATCH versioning system commonly used in package management.
    
    **Answer:** The Node Package Manager (npm) ecosystem uses Semantic Versioning as the standard for version numbers. The NPM ecosystem uses Semantic Versioning (SemVer) which follows the convention of MAJOR.MINOR.PATCH. This is to differentiate between versions that introduce major breaking changes, minor backwards-compatible changes, and patch changes for small fixes.
4. How do you use modules in JavaScript? How can you write your own module? Provide an overview of the module system in Node.js.
    
    **Answer:** Module in Node.js is a simple or complex functionality organized in single or multiple JavaScript files which can be reused throughout the Node.js application. Built-in Modules, Local modules, Third-party modules. Node.js has two module systems: CommonJS (`require()`, and variables and functions export from a CommonJS module with `module.exports`) modules and ECMAScript (`import` and `export` statements) modules. Authors can tell Node.js to use the ECMAScript modules loader via the .mjs file extension, the package.json "type" field. ES modules are the standard for JavaScript, while CommonJS is the default in Node.js
5. What are global modules in Node.js, and how do they differ from local modules? How do you interpret version specifications like "1.2.3", "~3.2.0", or "^2.1.0"?
   
    **Answer:** Generally, modules are scoped inside the project directory only, it means you can’t use them outside the project. But as global modules are installed on the computer (mostly root location), they can easily be used anywhere in our system. 
Install a module locally if you're going to require() it. Install a module globally if you're going to run it on the command line. ~1.2.3 is equivalent to >=1.2.3 <1.3.0; ^1.2.3 is equivalent to >=1.2.3 <2.0.0

Topic: **JavaScript Basics**

6. What is the difference between regular functions and arrow functions in JavaScript? How are they used, and when should you prefer one over the other?

   **Answer:** 
   - `this` value: `this` value inside a regular function is dynamic and depends on the invocation. But `this` inside the arrow function is bound lexically and equals to `this` of the outer function.
   - constructors: an arrow function cannot be used as a constructor.
   - `arguments` object: arguments object inside the regular functions contains the arguments in an array-like object. The arrow function, on the opposite, doesn't define arguments (but you can easily access the arrow function arguments using a rest parameter `...args`).
   - implicit return: if the arrow function has one expression, then the expression is returned implicitly, even without using the `return` keyword.
   - methods: you can define methods using the arrow function syntax inside classes. Arrow methods bind `this` value to the class instance. Anyhow the arrow method is invoked, `this` always equals the class instance, which is useful when the methods are used as callbacks.
   - hoisting: arrow functions cannot be accessed before initialization.
   - duplicate named parameters: arrow functions can never have duplicate named parameters, whether in strict or non-strict mode.
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

    **Answer:** there are four logical operators in JavaScript: || (OR), && (AND), ! (NOT), ?? (Nullish Coalescing). ?? returns the first argument if it’s not null/undefined. Otherwise, the second one. Boolean.prototype.toString(), Boolean.prototype.valueOf().

Topic: **Objects and Functions**

11. How do objects look like in JavaScript, and what are property descriptors associated with object properties?
12. What is a deep clone of an object, and how can you proceed to create one in JavaScript?
13. Explain the CommonJS module system and how it is utilized in Node.js to organize and share code between different files.
14. How do you create and export a module in Node.js, and how do you import it into another file using `require`?
15. Describe the roles of the "require" function in Node.js when dealing with modules, and how does it help manage dependencies?
16. What is the difference between "exports" and "module.exports" in a Node.js module? How can you use them to expose functionalities?
17. What is the difference between "exports" and "require" in a Node.js module? How are they related to each other in the module system?

Topic: **Type Conversion**

18. What is type conversion in JavaScript, and why is it necessary? Provide examples of implicit and explicit type conversions.
19. Explain the concept of truthy and falsy values in JavaScript and how they relate to boolean conversions.
20. How can you convert a variable of type string to a number in JavaScript using built-in functions like `Number()`, `parseInt()`, and `+` (unary plus)?

Topic: **Function Concepts**

21. What is an IIFE (Immediately Invoked Function Expression) in JavaScript, and what problem does it solve? Provide an example of its usage.
22. How do you define a function in JavaScript? Provide examples of both function declarations and function expressions.
23. Can a function in JavaScript accept multiple arguments? If yes, how do you pass and handle them within the function?
24. Provide an example of a closure in JavaScript and explain how it works.

Topic: **Pure Functions and Immutability**

25. What is a pure function in JavaScript, and what characteristics define a function as "pure"? How do pure functions relate to immutability in JavaScript?
26. Describe the concept of named immutable methods in JavaScript and provide examples of such methods.
27. Provide an example of a Higher-Order Function in JavaScript and explain how it can accept another function as an argument.
28. How do you pass arguments to a function in JavaScript, and how can a function return a value?

Topic: **Function Composition and Array Methods**

29. What is currying in JavaScript, and how does it help with function composition? Provide an example of currying.
30. Provide an example of function composition and describe its advantages over nested function calls.
31. Describe various array methods such as map, filter, reduce, and forEach, and provide examples of their usage.
32. How do you create and initialize objects using object literals and the "new" keyword in JavaScript? How can you access, modify, and delete object properties?

Topic: **Prototypes and Object-Oriented Programming**

33. What is the prototype in JavaScript, and how does it work with objects? Explain the prototype chain.
34. How do objects, prototypes, and property descriptors tie together to form the foundation of object-oriented programming in JavaScript?
35. How do you create an object in JavaScript using constructor functions or classes? Provide examples of both approaches.
36. Explain the attributes in a property descriptor, such as value, writable, enumerable, and configurable.
37. What are accessor properties, and how can you define them using get and set in property descriptors?

Topic: **Arrays**

38. Explain the difference between the splice and slice methods in JavaScript arrays. How are they used, and what are the key distinctions in their behavior? Provide examples to illustrate their usage.
39. How can you loop through an array using a for loop, and what are the benefits of using array methods like forEach instead?
40. How do you create a multidimensional array in JavaScript, and how do you access and modify elements in such arrays?

Topic: **Strings and Template Strings**

41. What are strings in JavaScript, and how do you create a string variable? Describe the difference between single quotes (''), double quotes ("") and backticks (``) when defining strings.
42. What are template strings (or template literals) in JavaScript, and how are they different from regular strings? How do you create a template string, and what benefits do they offer over traditional strings?
43. Describe how you can use String methods like toUpperCase, toLowerCase, trim, split, indexOf, substring, etc., to manipulate and extract information from strings.
44. How can you concatenate strings in JavaScript using traditional methods, and how does it compare to concatenation with template strings? Provide examples of both approaches.
45. What is the difference between a tagged template literal and a regular template literal? How can you use tagged template literals to customize string interpolation behavior?