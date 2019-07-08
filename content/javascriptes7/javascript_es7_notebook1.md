---
title: "Javascript ES7 1 : Introduction"
author: "Osman Cakir"
date: 2019-07-04
description: "Javascript ES7 Functionalities"
type: technical_note
draft: false
---
I started learned programming with Python and Jupyter Notebooks. The ease to share a notebook and watching cell by cell what the code does was key to me to demistify software development. I am now addicted to this approach. 

Currently I am working on a research data management tool which is written in pure JS and so I want to get better at JS7 functionalities.  I also wanted to have a reference sheet for myself. I learned I can run JS code inside the jupyter notebook cells with just 2 additional packages. Thus, this is why and how this notebook came to existence. 

I hope it will be useful to you as much as it is useful to me. I know it is not always self explanotory for someone who is not familiar to coding right now. I am always open to suggestions and corrections. 

Let's get to it!


To be able to write js code inside the jupyter notebook let's first install these two packages. 
    * pixiedust
    * pixiedust_node. 
Now we can run JS code inside the notebook cells that started with
    * %%node 
more info at : https://medium.com/codait/nodebooks-node-js-data-science-notebooks-aa140bea21ba
_____

You can directly install pixiedust and pixiedust_node inside the notebook as well. 


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


# Contents

     1 - Hello World
     2 - Declaring Variables / Initializing Variables
     3 - Data Types in Js
     4 - Incrementing Decrementing Variables
     5 - Basic Mathematical Operations
     6 - Compound Assignment with Augmented Addition
     7 - String Variables
             * Declare String Variables
             * Escape Character in JS
             * Concatenate Strings
             * Bracket notation to find the first character (0 based indexing)
             * Finding any character
             * String immutability
             * Function w/strings

## 1 - Hello World
________


```python
%%node
// to print something
console.log('hello world');
```

    hello world


## 2 - Declaring A Variable
____


```python
%%node
var a // declares a variable
var a = 2; // declares and assign the variable
a =3 // just assigns
console.log(a) // let's see a at the console
```

    3
    


Other ways of declaring a variable are 'let' and 'const'. It is recommended to use let and const to declare variables wherever possible opposed to 'var' method. It will prevent many bugs!


```python
%%node 
var number = 5; // declaring a variable with var makes it usable in the whole programme (global)
var myname = 'osman'
let ourName = 'freefall' // only to be used within the scope
const pi = 3.14 // a variable that is not changeable
console.log(pi)
```

    3.14
    


Scope of variables are actually a little bit more complex topic than explained above. We will go into details about them later. Just go along with the general wisdom that declaring a variable using var is not the best practice any more. Use let or const whenever possible.
____

## 3 - Data types in  JS
____
 * undefined: you may have a variable that you haven't set to be anything yet. 
 * null: is nothing, 
 * boolean: true or false variables
 * string: strings as usual  
 * symbol: an immutable primitive value that is unique 
 * number: numbers, floats 
 * object: stores key value pairs of different types

**Data is anything meaningful to a computer in computer science**

_______
## 4 - Basic Mathematical Operations 
___


```python
%%node
console.log(10+10) // sum
console.log(10-5) // difference
console.log(8*10) // multiplication
console.log(10/2) // division
console.log(10**3) // exponentiation
console.log(10%3) // remainder

```

    20
    
    5
    
    80
    
    5
    
    1000
    
    1
    


**Strings can be added too**


```python
%%node
var mystring = 'I am a'
var yourstring = ' string' 
console.log(mystring + yourstring)
```

    I am a string


## 5 - Incrementing / Decrementing Variables 


```python
%%node
// incrementing a variable 
var myVar = 87; 
myVar = 87 +1; // is equal to below statement
myVar++;
// decrementing a varible 
var myVart = 11
myVart = myVart -1  // is equal to below statement
myVart--
```

## 6 - Compound Assignment with Augmented Addition

Let's say we declared a variable called a and assigned its' value as 3. 
`var a = 3;`
These two statements are equivalent in JS. with compound assignment with augmented addition; `a = a + 12` and `a+=12`. And analogously other mathematical operations too.    
* `a = a + 12` and `a+=12`   
* `a = a - 2` and `a -= 2`
* `a = a*5` and `a*=5`
* `a = a /12` and `a /=12`


```python
%%node
var a = 0
var b = 0
console.log(a=a+12)
console.log(b+=12)
```

    12
    
    12
    


## 7 - Declare String Variables


```python
%%node
var firstName = 'Alan'
var myFirstName = 'Carnes'
```

* **Escaping in JS**


```python
%%node
var myStr1 = "I am a \"double quoted\" string inside"
var myStr2 = "<a href=\http://example.com\" target=\"blank\">Link</a>";
var myStr3 = '<a href="http://example.com" target="_blank">Link</a>';
/* Code output
\' single quote
\" double quote
\\ backslash 
\n newline
\r carriage turn
\t tab
\ backspace
\f form feed
*/
var myStr4 = "firstline\n \t SecondLine\nThirdline"
console.log(myStr1)
console.log(myStr2)
console.log(myStr3)
console.log(myStr4)
```

    ... ... ... ... ... ... ... ... ...
    I am a "double quoted" string inside
    <a href=http://example.com" target="blank">Link</a>
    <a href="http://example.com" target="_blank">Link</a>
    firstline
    SecondLine
    Thirdline


* **Concatenate Strings**


```python
%%node
var ourStr = "I come first. " + "I come second"
console.log(ourStr);
var myName = "osman "
var myStr1 = "my name is " + myName
console.log(myStr1);
var myStr2 = 'This is the first sentence. '
myStr2 += 'This is the second sentence'
console.log(myStr2)
myStr1 += myStr2
console.log(myStr1)
```

    I come first. I come second
    my name is osman
    This is the first sentence. This is the second sentence
    my name is osman This is the first sentence. This is the second sentence


* **Find the length of a string**


```python
%%node
var myStrLength = 0
myStrLength = myStr1.length
console.log(myStrLength)
```

    71
    


* **Bracket notation to find the first character (0 based indexing)**


```python
%%node
var firstLetterOfStr = ""
console.log(firstLetterOfStr)
firstLetterOfStr = myStr1[0]
console.log(firstLetterOfStr)
```

    m


 * **You can find the any characters position using the brackets**


```python
%%node
var firstName = 'Ada'
var lastletter = firstName[firstName.length-1]
console.log(lastletter)
```

    a


* **String Immutability**


```python
%%node
var myStr0 = 'jello world'
// this won't work!: myStr0[0] = 'H'
myStr0 = 'hello world would work'
console.log(myStr0)
```

    hello world would work


* **Function example with Strings**

Just to let you know the fun has not even started yet. We will take a closer look at functions of course.


```python
%%node
function wordBlanks(myNoun, myAdjective, myVerb, myAdverb) {
    var result = ""
    result += "The " + myAdjective + " " + myNoun + " " + myVerb + " its' tail."
    return result;
}

console.log(wordBlanks("snake", "big", "ate", "quickly"))
```

    ... ... ... ...
    The big snake ate its' tail.



# Thank You! 

Please let me know any typos or suggestions regarding the notebook. 
