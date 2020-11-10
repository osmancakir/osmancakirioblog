---
title: "Python 1 : Introduction"
author: "Osman Cakir"
date: 2020-11-10
description: "Introduction to Python: datatypes, variable decleration"
type: technical_note
draft: false
---
Python started as a fun project by a dutch guy who got bored on a Christmas Holiday. Check out this guy. He is cool. [Guido van Rossum](https://www.youtube.com/watch?v=xLVxoz-mQFs)

Anyways we are going to do some basic calculations, introducing variables and data types in this introduction tutorial. 

Let's Start I am psyched!

I started to write this tutorial 2 years ago 02 Dec 2018 now I am slowly updating it

## Calculations

As you can guess basic calculation operators are : summing: ' + ', subtracting: ' - ', Multiplying: ' \* ' Division: ' / ', Exponentiation: ' \*\* ', and Modulo: ' % ' (Which is the operation for giving you the result of the reminder of a division)


```python
1+5
```




    6




```python
7-3
```




    4




```python
9*23
```




    207




```python
48/43
```




    1.1162790697674418




```python
67%8
```




    3




```python
3+2 * 4+1
```




    12




```python
(3+2)*(4+1)
```




    25



+ Important note here: Python does the mathematical operations in mathematical order. So be careful to wrap in paranthesis where you need.



## Variable Assignment

Variables are used to call up a value. To create a variable you just use equals sign (=). Variable names are case sensitive and you can not start with a number or special character. 


```python
height=182
```


```python
weight=65
```

+ height and weight variables are created. 


```python
5aba=76
```


      File "<ipython-input-9-0958b357e6cd>", line 1
        5aba=76
           ^
    SyntaxError: invalid syntax




```python
%aba=45
```

    ERROR:root:Line magic function `%aba` not found.


+ 5aba and %aba variables couldn't be created. 

## Data Types

* Usually the online courses start with introducing 4 data types.
   * int: Integers
   * float: Real numbers with an integer part and a fraction part
   * str: Strings. Python's text. You can use both single quotation and double quotation when writing strings in Python.
   * bool: Booleans. True or False statements. 
* the variables created with these 4 represents a single value. I will go ahead and introduce you the data types that when assigned to a variable can take multiple values as well. These are lists, sets, dictionaries and tuples.


```python
#integers
5
```




    5




```python
#floats
5.0
```




    5.0




```python
#Strings
'hello' 
```




    'hello'




```python
#or
"hello"
#both works
```




    'hello'




```python
#If you want to say something like 'let's go' in strings just wrap it with double quatation.
"let's go"
```




    "let's go"




```python
#Booleans
True
```




    True




```python
#Booleans
False
```




    False



To learn about a variable's type you can use `type()` function. For example: 


```python
type(height)
```




    int



You can add strings. When you do it, they are placed together. For example: 


```python
'ab'+'cd'
```




    'abcd'



But you can not substract, multiply or divide strings. 

* 'hey' - 'hey' : error
* 'hey' * 'hey' : error
* 'hey' / 'hey' : error
* 'heyhey' - 'hey' : also error 
* 'hey' * 2 : works
* 'hey' + 2 : error

To print a result use print() function. For Example: 


```python
savings=200
print(savings)
```

    200


You can convert variables to each other. To do that use: 

* str(variable name) : to convert it to a string
* float(variable name) : to convert it to a float
* bool(variable name) : to convert it to a boolean.

But this only works if two data types are convertible to each other

### Lists

to create a list, use brackets `[]`. Lists can contain any data types. Floats, booleans, strings, integers; anything.


```python
['a','b','c']
```




    ['a', 'b', 'c']




```python
heights=[1.73, 1.82, 1.75,1.90]
```

Lists can also contain different types of data in one list. 


```python
heights2=['berk', 1.73, 'salih', 1.82, 'dad', 1.75, 'mum', 1,65]
```

Lists can also contain other lists.


```python
heights3=[['berk', 1.73],['salih', 1.82], ['dad', 1.75], ['mum',1.65]]
```

### List Indexing

To print specific elements of a list you can use indexing. Python indexes data as

* from left to right :      0  1  2  3  4  5 ... 
* from right to left : ... -6 -5 -4 -3 -2 -1 

to call an indexed element from a list: 


```python
heights2[0]
```




    'berk'




```python
heights3[-1]
```




    ['mum', 1.65]



to slice a list, use colon `[:]` notation. The first indexed element is going to be included but the last indexed element is not going to be included in the list. 

* `[:]` : will take the entire list
* `[2:]` : will take from 2nd indexed element (inclusive) till the last element (inclusive again)
* `[:9]` : will take from the first element (inclusive) till the 9th indexed element (exclusive)


```python
heights[0:2]
```




    [1.73, 1.82]



As you can see above 0 indexed element in the list (1.73) is included but the 2nd indexed element (1.75) (third element in the list) is not included in the output.

Subsetting List of Lists


```python
parents = heights3[2:]
```


```python
parents
```




    [['dad', 1.75], ['mum', 1.65]]




```python
dad_height=heights3[2][1]
```


```python
dad_height
```




    1.75



### Tuples

The main difference between tuples and lists is that the values in tuples are immutable!. Tuples are created with paranthesis notatiton `()`.


```python
(1,2,3,4)
```




    (1, 2, 3, 4)




```python
type((1,2,3,4))
```




    tuple




```python
a=(1,2,3,4)
```


```python
a[0]
```




    1



### Sets

Sets are defined by unique elements. Sets are created by {} notation. And they do not support indexing. 


```python
{1,1,1,2,2,2,3}
```




    {1, 2, 3}




```python
a={1,2,3}
```


```python
a[0]
```


    ---------------------------------------------------------------------------

    TypeError 
    Traceback (most recent call last)

    <ipython-input-79-5ccf417d7af1> in <module>()
    ----> 1 a[0]
    
    TypeError: 'set' object does not support indexing


### Dictionaries

Dictionaries are key and value pairs. They also do not support indexing. Dictionaries do not hold elements in sequence. Instead you can call their values by the keys. 


```python
d={'key1':'value', 'key2': 'value2'}
```


```python
d[0]
```


    ---------------------------------------------------------------------------

    KeyError
    Traceback (most recent call last)

    <ipython-input-81-17371c6688f6> in <module>()
    ----> 1 d[0]
    
    KeyError: 0



```python
d['key1']
```




    'value'


