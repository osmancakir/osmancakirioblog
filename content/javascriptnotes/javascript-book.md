---
title: "Javascript Book with ES7 Features"
author: "Osman Cakir"
date: 2020-09-03T11:53:49-07:00
description: "A Javascript book to understand the syntax and fundementals with ES7 features"
type: technical_note
draft: false
---

I wrote a javascript book over the years I started to learn it. I wasn't purposefully writing it to make it readable or understandable for other learners, rather my sole aim was understanding it myself. I collected example codes and explanations from various resources and didn't pay attention to the bibliography of it. So please if you see your example and explanation in this document and want to have it changed or take credit for it, contact me by the [contact form](https://osmancakir.io/#contact) or by [twitter.](https://twitter.com/osmancakirio)

I will try to structure it in a way you can start reading the book from top to bottom. But in the beginning, I am afraid I won't be very successful at it. I promise it will get better in time. I will also recommend memorizing especially the definitions even if you don't grasp them as a whole. Because if you build that memory, it will be more easy to make sense of it when I explain that topic or definition in more detail as we progress in the book. In my opinion, this approach is almost a requirement for learning a programming language. Because however you try to make it understandable as step-by-step, you will be lost at some point due to the interconnectivity of the concepts. Memorizing key definitions and feautures will be like loading the programming language into your brain and you will be first able to some sort of 'speak the language' before being able to code. 

The sections and examples of this book will be divided into different notebooks on this website too. So people can look exactly what they need, without searching the whole document.

## General Info

Javascript is an interpreted language. It is not compiled like C. When you write your javascript code it needs an interpreter to run. Interpreters read your code line by line from top to bottom and execute them. Each browser has its own JavaScript engine, which either interprets the code or uses some sort of lazy compilation.
Javascript engine means Javascript interpreter? MOST PROBABLY.

+ Chrome: V8,
+ Firefox : SpiderMonkey,
+ Safari: JavaScriptCore, etc...

They each implement the ECMAScript standard, but may differ for anything not defined by the standard.

## Javascript Data Types

There are two different category for data types in Javascript.

+ Primitive Data Types
+ Objects

Javascript defines 5 types of primitive data types: 

+ string
+ number
+ boolean
+ null
+ undefined

**A primitive data type** is data that has a primitive value.
**A primitive value** is a value that has no properties or methods.

And everyting else in Js are objects. 

When you think of objects you should think of C structs. C structures contain a number of 'fields' or 'members' which we might call 'properties' in object-oriented jargon. But properties themselves can not ever stand on their own. For example in below C code I declared a struct type car.

```c
struct car
{
	int year;
	char model[10];
}
```
Then I can create a car which can have struct car properties:

```c
struct car herbie;

herbie.year = 1963;      /* here year and model are part of the 'struct car' you can not save them as; */
herbie.model = "beetle"; /* year = 1963 or model = "beetle" */

```
In Js, objects can have methods, besides properties. 

**Method**: functions that are inherent to the object, mean nothing outside of it. Thus just like properties, methods can not ever stand on their own.

+ `function(object); -> This is not object oriented programming!`
+ `object.function(); -> This is object oriented programming!. Object is the center of attention!`

The fields and methods of an object are similar in spirit to the idea of a dictionary, which is familiar if you come from python. So above struct in c can be written in javascript as follows: key value pairs. 

```javascript
// A js object is created with object literals {}
var herbie = { year:1963, model:'beetle' }

```
**SideNote**: Note that we didn't write the keys as strings. Property names (keys) are automatically coerced into a string.

In JavaScript, objects are king. If you understand objects, you understand JavaScript.

In JavaScript, almost "everything" is an object.

+ Booleans can be objects (if defined with the new keyword)
+ Numbers can be objects (if defined with the new keyword)
+ Strings can be objects (if defined with the new keyword)
+ Dates are always objects
+ Maths are always objects
+ Regular expressions are always objects
+ Arrays are always objects
+ Functions are always objects
+ Objects are always objects

All JavaScript values, except primitives, are objects. We will get back into objects later. 

**SideNote**: `typeof(null)` returns `"object"`. This is a known bug for JS. Why not removed/fixed already? It will crash many websites. This is a weird feature of JS.

## Javascript Variables

The 5 concepts to understand variables in Javascript:

+ **Decleration of Variables**: Defining variables without assigning a value to them. 

```javascript
x // Uncaught ReferenceError: x is not defined at <anonymous>:1:1
var a // var is defined but not assigned. returns undefined
let b
const c // Uncaught SyntaxError: Missing initializer in const declaration
```

+ **Assignment of Variables**: Assigning a value to variables.

```javascript
a = true
b = "hello world"
```

+ **Initialization of Variables**: Declaring and Assigning variables at the same time.

```javascript
x = 10 // will not throw Uncaught ReferenceError.
var d = "false"
let e = "how are you world?"
const c = 42 // will not throw Uncaught SyntaxError.

```

**SideNote**: You can not declare / define or assign global (`x`) or const (`c`) variables, you can only initialize them. Compare x,c at Decleration and x,c at Initialization.

+ **Hoisting**: Interpreter taking the definitions of variables and function definitions and hoisting them to the top of the script. For example: 

```javascript
console.log(x); // returns undefined. Will not throw an error.
var x = 82;
```

**SideNote**: Precedence of hoisting: function definitions goes to the top then come variables.

+ **Scope of Variables**:

Until ECMAScript 6 Javascript had only two types of scope. Global and Function. Block scope come into play with ECMAScript 6.

+ Global Scope: Variables declared outside a function have global scope. In global scope, context (value of `this`) is the global object (in a browser environment; Window object). 
+ Function Scope (also referred as Local Scope): Variables declared inside a function have function scope. In function scope, you need to study the context (value of this). There are several rules to determine it. 
+ Block Scope: Variables that only scoped between curly braces `{}`. We can write variables that are scoped between `{}` if we declare them with the `let` or `const` keyword. This means that a new, local scope is created from any kind of block, including function blocks, if statements, and for and while loops.

We also need to understand Lexical Scope concept: 

**Lexical Scope (Sometimes Referred as Static Scope)**

Lexical scope means that in a nested group of functions, the inner functions have access to the variables and other resources of their parent scope. This means that the child functions are lexically bound to the execution context of their parents. Lexical scope is sometimes also referred to as static scope. For Eample: 

```javascript
function grandfather() {
	var name = 'Hammad';
	// 'likes' is not accessible here
	function parent() {
    	// 'name' is accessible here
    	// 'likes' is not accessible here
    	function child() {
        	// Innermost level of the scope chain
        	// 'name' is also accessible here
        	var likes = 'Coding';
    	}
	}
}

```

The thing you will notice about lexical scope is that it works forward, meaning name can be accessed by its children's execution contexts. But it doesn't work backward to its parents, meaning that the variable `likes` cannot be accessed by its parents.

This also tells us that variables having the same name in different **execution contexts** gain precedence from top to bottom of the **execution stack**. A variable, having a name similar to another variable, in the innermost function (topmost context of the execution stack) will have higher precedence.

I know above paragraph is a bit too much to grasp but bear with me. Key things to keep in mind for later here: 

* Scope refers to the visibility of variables.
* Context refers to the value of `this` in the same scope. Context is used to refer to the value of `this` in some particular part of your code.

When especially debugging your code you will often ask yourself these two questions: 

* Is my variable really visible? -> What is the scope of it? -> Where does it sit lexically in my code? 
* When has my variable been declared? -> What is the execution context of it? -> Where does it sit lexically in my code? 

We can also change the context using function methods which are `bind()`, `call()`, `apply()`. We will look into this topic later.

Now I can give more information about JS variables especially for the scope of them, reassigning and redeclaring them : 

**Initialization, Reassignment and Redeclaration of Variables within the same scope:**

```javascript
// Initialization
x = 44; // creates a global variable, hoisted? 
var y = 44; // might have global or function scope, hoisted
let z = 44; // might have global/function/block scope, not hoisted
const q = 44; // might have global/function/block scope, not hoisted.

// Reassignment 
x = 45; // This operation is actually re-decleration and it is possible.
y = 45 // vars can be reassigned
z = 45 // lets can be reassigned
q = 45 // consts can not be reassigned (Uncaught TypeError: Assignment to constant variable)

// Redecleration 
x = 46 // global variables can be redeclared.
var y = 46 // vars can be redeclared
let z = 46 // lets can not be redeclared (SyntaxError: redeclaration of let z)
const q = 46 // consts can not be redeclared (SyntaxError: redeclaration of const q)

```

**Initialization, Reassignment and Redeclaration of Variables within the different scopes:**

You can reinitialize, reassign and redeclare your variables in different scopes. But remember;

+ global variables (variables declared with `var`, and variables initialized without a keyword (`x=42`)) can not have block scope!. 
+ The difference between let and const lies on reassigment. Consts can not be reassigned.

**SideNote**: Consts can not be reassigned but can be mutated. Consts are just created with a constant reference in memory. Hence if you do not attempt to change the memory location you are fine. Mutation is fine.
Assignment and mutation difference topic will come [later](https://dev.to/boywithsilverwings/reassignment-vs-mutability-21ob). 


## Javascript Comparison Operators, Logical Operators, Conditionals (if, else if, else, switch, ternary)

to be continue next week...

