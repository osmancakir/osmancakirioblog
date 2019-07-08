---
title: "Javascript ES7 2 : Arrays, Functions and Logic"
author: "Osman Cakir"
date: 2019-07-04
description: "Javascript ES7 Functionalities"
type: technical_note
draft: false
---
Let's continue where we left off.

# Contents

    8 - Arrays

            * Store Data in Arrays
            * Nested Arrays : Multidimensional Arrays
            * Access Data in Arrays with Indexes
            * Arrays are Mutable
            * Manipulating Arrays
                push()
                pop()
                shift()
                unshift()

    9 - Functions

            * A Simple Function
            * Global Scopes and Functions
            * Local Scopes and Functions
            * Understanding Undefined Value Returned From A Function
            * Assignment with A Returned Value
            * Stand in Line.

    10 - Logical Operators and If Statements
    
            * Strict Equals
            * Other Operators
            * Switch Statements
            * Returning Early Pattern From Functions



```python
import pixiedust
import pixiedust_node
```

    Pixiedust database opened successfully
    pixiedust_node 0.2.5 started. Cells starting '%%node' may contain Node.js code.


## 8 -  Arrays 

* **Store Data in Arrays**


```python
%%node
var ourArray = ["john", 23];
```

* **Nested Arrays : multidimensional array** 


```python
%%node
var ourArray2 = [["the universe", 42], ["everything", 101010]];
```

* **Access Data in Arrays Data with Indexes**


```python
%%node
var ourArray3 = [50, 60, 70];
var ourData = ourArray2[0];
console.log(ourData)
```

    [ 'the universe', 42 ]


* **Access elements in nested arrays** 


```python
%%node
var ourData2 = ourArray2[0][0];
console.log(ourData2)
```

    the universe


* **Strings were immutable but arrays are mutable.** 


```python
%%node
ourArray3[1] = 45;
console.log(ourArray3) // pay attention to (30 -> 45) change in ourArray3
```

    [ 50, 45, 70 ]
    


* **Manipulate Arrays with push()**


```python
%%node
ourArray.push("happy")
console.log(ourArray)
ourArray.push(["cheerful", 40])
console.log(ourArray)
```

    [ 'john', 23, 'happy' ]
    [ 'john', 23, 'happy', [ 'cheerful', 40 ] ]


* **Anologously;**
    * Manipulate Arrays with pop() : last element goes
    * Manipulate Arrays with shift() : first element goes.
    * Manipulate Arrays with unshift() : adds element as the first element.


```python
%%node
var removedFromArray = ourArray.pop()
console.log(removedFromArray)
console.log(ourArray)
console.log(ourArray.shift())
ourArray.unshift(("alexa"))
console.log(ourArray)
```

    [ 'cheerful', 40 ]
    [ 'john', 23, 'happy' ]
    john
    [ 'alexa', 23, 'happy' ]


## 9 - Functions

* **A Simple Function With Arguments**

Below function will take the difference of its 2 arguments.



```python
%%node
function ourFunctionWithArguments(a,b) {
    console.log(a-b);
}
ourFunctionWithArguments(10,5) 
```

    ... ...
    5
    


### Global scope and functions: 
    - variables that are defined outside a function block have global scope
    - variables that are defined inside a function with var keyword has limited scope. 
    - if you define a variable inside a function but without using the var keyword, that variable
      becomes automatically global scope.

###  Local Scopes and Functions

    function myLocalScope() {
        var myVar = 5;
        console.log(myVar);
    }
    myLocalScope(); // will output 5 
    console.log(myVar); // will give me an error. Becuase myVar has a local scope. it is not callable

You can have a global and local scope variables with the same name!


```python
%%node
    function myLocalScope() {
        var myVar = 5;
        console.log(myVar);
    }
    myLocalScope(); // will output 5 
    console.log(myVar); // will give me an error. Becuase myVar has a local scope. it is not callable
```

    ... ... ...
    5
    
    ReferenceError: myVar is not defined


### Understanding Undefined Value Returned from a Function.

   * funtions can have return statements but they don't have to
                var sum = 0;
                function addThree() {
                    sum = sum + 3;
                }
   * if you don't specify return value it is going to be undefined. 
   
                function addFive() {
                    sum = sum += 5;
                }
   * so if we log this out it would be undefined! 
    

### Assignment with a Returned Value
        var processed = 0; 
        function processedArg(num) {
            return (num+3)/2;
        }
        processed = processedArg(7);
* processed is changed to 5!


```python
%%node
var processed = 0; 
function processedArg(num) {
    return (num+3)/2;
}
processed = processedArg(7);
console.log(processed)
```

    ... ...
    5
    


### Stand in Line 
    
In computer science a cue is an abstract data structure where items are kept in order. New items can be added to the back of the cue and old items can be removed from the front. 


```python
%%node
function nextInLine(arr,item){
    arr.push(item)
    return arr.shift()
}
var testArr = [1,2,3,4,5]
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr,6));
console.log("After: "+ JSON.stringify(testArr)); 
```

    ... ... ...
    Before: [1,2,3,4,5]
    1
    
    After: [2,3,4,5,6]


## 10 - Logical Operators and if Statements


```python
%%node
function testEqual(val) {
    if (val == 12) {
        return "Equal"
    }
    return "Not Equal";
}
console.log(testEqual(10))
```

    ... ..... ..... ... ...
    Not Equal


### Strict Equals 
* '==' operator can check 3 == '3' and can tell true. Because it can convert the string to a number. 
* '===' Strictly Equal Operator doesn't convert any value.


```python
%%node
function testStrict(val) {
    if (val === 12) {
        return "Equal"
    }
    return "Not Equal";
}
console.log(testStrict('12'))
```

    ... ..... ..... ... ...
    Not Equal


### Other Operators 

    * inequality operator: !=  (it also does type converting) strict inequality operator : !==
    * greater than > and < and >= <=
    * logical operators and : &&  or : || 
    * else statement: else {}
    * else if statement: else if {}


```python
%%node
function testElseIf(val) {
    if (val > 10) {
        return 'greater than 10';
    }   else if (val < 5) {
        return 'smaller than 5';
    }
        else {
        return 'between 5 and 10'
    }
}
console.log(testElseIf(7))
// order in logical statements: be careful above! 
```

    ... ..... ..... ..... ..... ... ..... ..... ...
    between 5 and 10


### Switch statements: instead of a chained elseif statements we can use a switch statement.


```python
%%node
function caseInSwitch(val) {
    var answer = "";
    switch(val) {
        case 1: // works as strictly equal!
        answer = "alpha"
        break; // breaks are important otherwise will continue to assign below.
        case 2:
        answer = "beta"
        break;
        default: //adds a default option for cases outside switch 
        answer = "stuff"
        break;
    }
    return answer;
}

console.log(caseInSwitch(1))
// when you want to give the same output for different cases just take out the break between those cases.
```

    ... ... ..... ..... ..... ..... ..... ..... ..... ..... ..... ..... ... ...
    alpha


### Returning Early Pattern From Functions.


```python
%%node
function abTest(a,b) {
    if (a < 0 || b < 0) {
        return undefined;
        
    }
    return 5
}
console.log(abTest(2,3))
```

    ... ..... ..... ..... ... ...
    5
    


______
### Continue to Notebook 3 :)
