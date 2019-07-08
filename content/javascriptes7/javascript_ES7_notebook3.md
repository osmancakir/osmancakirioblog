---
title: "Javascript ES7 3 : Objects, Loops, Advanced Operators"
author: "Osman Cakir"
date: 2019-07-04
description: "Javascript ES7 Functionalities"
type: technical_note
draft: false
---
The first 2 notebooks were actually the basics of javascript. The 3rd and 4th notebooks are more focused on new functionalities of ES7 and some advanced programming in JS.

# Contents

     11 - Build Javascript Objects [3rd Notebook]
             * Manipulate Complex Objects in JS
     12 - Loops
             * while Loop
             * for Loop
             * Nested for Loop
             * Do While Loops
     13 - Generate Random Numbers 
             * parseInt()
     14 - The Conditional (Ternary) Operator
     15 - Let and Const Variable Declaration in Detail
     16 - Specify a Default Value For a Function
     17 - Rest Operator
     18 - Spread Operator


```python
#!pip install pixiedust
#!pip install pixiedust_node
```


```python
import pixiedust
import pixiedust_node
```

    Pixiedust database opened successfully
    pixiedust_node 0.2.5 started. Cells starting '%%node' may contain Node.js code.


## 11 - Build Javascript Objects 
    - very similar to dictionaries in Python!. 
    - Keys are called properties. 
    - Values are called values.
    - you can access its properties with dot. notation
    - you can also access with bracket notatiton.
    - Accessing Object Properties with variables: 
        - With bracket notation you can also access an object's property with a variable
    - Updating the properties in a javascript object: 
        - you can do that with dot. notation
    - Adding new propoerties to an js object: 
        - you can do that with dot notation or bracket notation
    - Deleting the propoerties to a js object: 
        delete keyword with dot notation
    - You can use objects to lookup instead of writing gigantic switch cases. 
    -Testing objects for Properties
        - hasOwnProperty() method.



```python
%%node
var ourDog = {
    "name": "Leo", 
    "legs": 4,
    "tails":1,
    "friends": ["everything"],
    "the drink": "water",
    12 : "number"
};
```

    ... ... ... ... ... ... ...



```python
%%node
var legs = ourDog.legs // access with dot
var drinks = ourDog["the drink"]; // access with brackets
var playerNumber = 12; // access with a variable equal to one of the keys
var player = ourDog[playerNumber];
ourDog.name = "Happy Leo" // updating
ourDog.bark = "woof" // adding
ourDog['level'] =  45 // adding
// delete ourDog.level;
console.log(ourDog)
```

    { '12': 'number',
    name: 'Happy Leo',
    legs: 4,
    tails: 1,
    friends: [ 'everything' ],
    'the drink': 'water',
    bark: 'woof',
    level: 45 }



```python
%%node
function phoneticLookUp(val) { //lookup example
    var result = ""
    var lookup = {
        "alpha": "adam",
        "bravo": "boston"
    }
    result = lookup[val];
    return result;
}
console.log(phoneticLookUp("alpha"))

```

    ... ... ..... ..... ..... ... ... ...
    adam



```python
%%node
function checkObj(checkProp) { // checking propoerties
    if (ourDog.hasOwnProperty(checkProp)) {
        return ourDog[checkProp]         
        }
         else {
            return "not found"
        }
}
console.log(checkObj("tails"))
```

    ... ..... ..... ... ..... ..... ...
    1
    


### Manipulating Complex Objects in js
    - flexible complex data storage units
    - very similar to JSON files.
    - below we see an array with objects in it.  
    - Accessing nested objects in objects is possible with dot.dot notation.


```python
%%node
var myMusic = [
    {
        "artist": "Billy Joel",
        "title": "Piano Man",
        "release_year": 1973,
        "formats": ["CD", "ST", "LP"], 
        "gold": true
    },{
        "artist": "Bobby",
        "title": "Creal",
        "release_year": 2009,
        "formats": ["youtube videos"], 
        "gold": true
    }
]

var secondTree = myMusic[1].release_year // accessing obj. property nested in an array. 
console.log(secondTree) // combine bracket and dot notation.
```

    ... ... ... ... ... ... ... ... ... ... ... ... ... ...
    2009
    


## 12 -  Loops
    - while loop
    - for loop [3 components: initilization(usually a variable) ; condition ; final expression)]
    - nested for loops
    - do while loops: runs at least ones the code before checking the condition


```python
%%node
var myArray = [];
var i = 0
while (i<5) {
    myArray.push(i);
    i++;
}

console.log(myArray)
```

    ... ... ...
    [ 0, 1, 2, 3, 4 ]
    



```python
%%node
var myArray2 = [];
for (var i =0; i < 8; i++) { // for loop example
    myArray2.push(i);
}
console.log(myArray2)
```

    ... ...
    [ 0, 1, 2, 3, 4, 5, 6, 7 ]
    



```python
%%node
var myArray3 = [2,3,4,5,6]; // another for loop example with iteration on an array.
var total= 0;
for (var i = 0 ; i < myArray3.length; i++){
    total += myArray3[i]
}
console.log(total)
```

    ... ...
    20
    



```python
%%node
function multiplyAll(arr) { // nested for loops
    var product = 1 
    for (var i = 0; i < arr.length; i++){
        for (var j = 0; j< arr[i].length; j++){
            product *= arr[i][j]
        }
    }
return product
}

var product = multiplyAll([[1,2], [3,4], [5,6,7]])
console.log(product)
```

    ... ... ..... ....... ....... ..... ... ...
    5040
    



```python
%%node
var myArray4 = []
var i = 10

do { // do while loop example!
    myArray4.push(i)
    i++;}
    while (i<5) {
        myArray.push(i)
    }
console.log(i, myArray4)
```

    ... ... ... ... ...
    11 [ 10 ]


## 13 - Generate Random Functions 


```python
%%node
function randomFraction() {
    return Math.random(); //generates a random number between 0 and 1
}
console.log(randomFraction());
```

    ... ...
    0.20582776591657392
    



```python
%%node
var randomNumberBetween0and19 = Math.floor(Math.floor(Math.random()*20)) //Math.floor rounds up
function randomWholeNum() {
    return Math.random();
}
console.log(randomWholeNum());
console.log(randomNumberBetween0and19)
```

    ... ...
    0.3352099482101052
    
    17
    


### parseInt() Function
    - takes a string and returns an integer
    - radix argument tells us the base. default base is 10


```python
%%node
function convertToInteger(str) {
    return parseInt(str,2) // 2 is the base ; radix argument
}
console.log(convertToInteger("10011"))
```

    ... ...
    19
    


 ## 14 - The Conditional (Ternary) Operator
    - condition ? statement-if-true : statement-if-false;
    - multiple conditions are possible


```python
%%node
function checkEqual(a,b) {
    return a === b ? true : false;
    
}
console.log(checkEqual(1,2))
```

    ... ... ...
    false
    



```python
%%node
function checkSign(num) {
    return num > 0 ? "positive" : num < 0 ? "negative" : "zero" // multiple conditions
}
console.log(checkSign(0))
```

    ... ...
    zero


## 15 - let and const variable declaration in more detail

- with ES6 it is possible to declare variables with let and const
- let : only allows you declare a variable once. you can not declare it with the same name twice. you can set it twice though. you can reassign it.
- let is only limited to block scope so your variable can be accessed only inside a block of a code. {} : is a block scope means
- const is a read only variable decleration meaning you can not reassign it. but you can mutate if const is an array using [] notation.
- by convention const are ALLCAPITALS



```python
%%node
function printManyTimes(str) {
    "use strict"; // catches common coding mistakes. such as if you create a varible but don't declare it.
    const SENTENCE = str + " is cool";
    for(let i = 0; i< str.length; i+=2){
        console.log(SENTENCE)
    }
}
printManyTimes("art")
```

    ... ... ... ..... ..... ...
    art is cool
    art is cool


#### Prevent Object Mutation
- Object.freeze(MATH_CONSTANTS) will prevent any kind of mutation on your variable. put it somewhere in your function.

## 16 - Arrow functions to write concise Anonymous Functions

- below function is an anonymous function. it is assigned to a variable but it doesn't have a name.


```python
%%node
var magic = function() {
    return new Date();
}
```

    ... ...


- you can convert an anon function to an arrow function as shown below =>


```python
%%node
var magic2 = () => {
    return new Date()
}
```

    ... ...


- you can even shorten this arrow function as shown below.


```python
%%node
const MAGIC3 = () => new Date();
```


```python
%%node
var myConcat = (arr1, arr2) => arr1.concat(arr2);
var myConcat1 = (arr1, arr2) => { //the same as above
    return arr1.concat(arr2);
}
console.log(myConcat1([1,2], [3,4,5]))
```

    ... ...
    [ 1, 2, 3, 4, 5 ]
    


### High Order Arrow Functions
    - map, filter and reduce are high order functions. 
    - they take functions as arguments for processing collections of data


```python
%%node
const REALNUMBERARRAY = [4,5.6,-9.8, 3.14,42, 6, 8.34]

const SQUARELIST = (arr) => {
    const SQUAREDINTEGERS = arr.filter( num => Number.isInteger(num) && num > 0).map(x => x*x)
    return SQUAREDINTEGERS
}
const SQUAREDINTEGERS = SQUARELIST(REALNUMBERARRAY)
console.log(SQUAREDINTEGERS)
```

    ... ... ...
    [ 16, 1764, 36 ]
    


## 16 - Specify a Default Value For a Function
    - function fede(number, value = 1) value is set to 1 by default even if it is not passed it 
    - console.log(fede(5,2)) sets the value = 2 
    - console.log(fede(5)) sets the value =1 bcs it is the default value.

## 17 - Rest Operator
    - allows you to create functions that can take variable number of arguments
    - ....args is the notation

## 18 - Spread Operator
    - basically a way to copy arrays. the changes on the copied won't effect the original array. 
    - arr1 = [...arr2] is the notation.


```python

```
