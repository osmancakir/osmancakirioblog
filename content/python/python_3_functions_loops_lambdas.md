---
title: "Python 3 : Functions, Loops, Lambdas"
author: "Osman Cakir"
date: 2018-12-02
description: "A few more python programming concepts for data analysis"
type: technical_note
draft: false
---
Please note, this is not meant to be a comprehensive overview of Python or programming in general, but this crash course covers the basics that you need to know when you work with the data. I am planning to provide some more python learning material that focuses on more of the software development topics too. However for now here we focus on **data science** aspects of it. 

Since I do not want to divide the topic into more sub topics any more, this notebook will be a little bit long and we will cover many stuff. Get your pen and paper ready to take notes. 

Let's see what we will cover : 


* Comparison Operators
* if,elif, else Statements
* for Loops
* while Loops
* range() function
* list comprehension
* Creating Custom Functions
* lambda expressions
* map() and filter() functions
* Various methods
____

## Comparison Operators

Here you can see how you can create comparison operators in Python. Comparison operators output a boolean value depending on the statement is whether true or not. 


```python
1 > 2
```




    False




```python
1 < 2
```




    True




```python
1 >= 1
```




    True




```python
1 <= 4
```




    True




```python
1 == 1
```




    True




```python
'hi' == 'bye'
```




    False




```python
'hi' != 'bye'
```




    True



## Logic Operators

With Logic Operators you can combine multiple comparison operators together. Logic Operators will output boolean values

* and operator: all of the conditions must be met in order to have 'true' as the output
* or operator: it is sufficient to meet one of the conditions as true in order to have 'true' as the output. 
**Remember** : 'and' and 'or'  logic operators can only work with one instance of condition.


```python
(1 > 2) and (2 < 3)
```




    False




```python
(1 > 2) or (2 < 3)
```




    True




```python
(1 == 2) or (2 == 3) or (4 == 4)
```




    True



## if,elif, else Statements

If statements basically tell us : ' If the condition is true, then run the following code after the colon (:)'


```python
if 1 < 2:
    print('Yep!')
```

    Yep!



```python
if 1 < 2:
    print('yep!')
```

    yep!


When combined with else statement it tells us ' If the condition is not true after the if statement, go for the else statement. And run it's code after the colon (:)' 


```python
if 1 < 2:
    print('first')
else:
    print('last')
```

    first



```python
if 1 > 2:
    print('first')
else:
    print('last')
```

    last


You can combine if statements with elif statements. It tells us ' If the condition is not true after the if statement, go for the elif statement. And run it's code after the colon (:). If elif's statement was not also true, go for the else statement and run else's code.' **Remember** whichever statement's the condition is first met the code of that statement will be executed.


```python
if 1 == 2:
    print('first')
elif 3 == 3:
    print('middle')
else:
    print('Last')
```

    middle


## for Loops : Iterate through a sequence


```python
seq = [1,2,3,4,5]
```

For Loops are used when you have a block of code which you want to repeat a fixed number of times. The Python for statement iterates over the members of a sequence in order, executing the block each time. Item here is a temporary variable. You can write whatever you want. 


```python
for item in seq:
    print(item)
```

    1
    2
    3
    4
    5



```python
for item in seq:
    print('Yep')
```

    Yep
    Yep
    Yep
    Yep
    Yep



```python
for jelly in seq:
    print(jelly+jelly)
```

    2
    4
    6
    8
    10


## while Loops

While loops, like the ForLoop, are used for repeating sections of code - but unlike a for loop, the while loop will not run n times, but until a defined condition is no longer met. If the condition is initially false, the loop body will not be executed at all. If you do not have defined condition at the bottom you can create an infinite loop. In this case you can have a crash. In order to solve it, go to Kernel and press restart. You can also try to interrupt but it is not always helpful. 


```python
i = 1
while i < 5:
    print('i is: {}'.format(i))
    i = i+1
```

    i is: 1
    i is: 2
    i is: 3
    i is: 4


## range()

Range function creates a sequence automatically. It takes three arguments. range(start(inclusive), stop(exclusive), step)


```python
range(5)
```




    range(0, 5)




```python
for i in range(5):
    print(i)
```

    0
    1
    2
    3
    4



```python
list(range(5))
```




    [0, 1, 2, 3, 4]



## list comprehension

It is a shortcut when you want to make a quick calculation over all of the elements in your list. It is a nice to know thing but this kind of operations will be extremely easy with Numpy.


```python
x = [1,2,3,4]
```


```python
out = []
for item in x:
    out.append(item**2)
print(out)
```

    [1, 4, 9, 16]



```python
[item**2 for item in x]
```




    [1, 4, 9, 16]



## Creating Custom Functions

To create your own functions you should use 'def function_name():' then write the code of your function. You can create a doctstring for your function as shown below. (Your doctstring will be shown when shift+tab is pressed.) 


```python
def my_func(param1='default'):
    """
    Docstring goes here.
    """
    print(param1)
```


```python
my_func
```




    <function __main__.my_func>




```python
my_func()
```

    default



```python
my_func('new param')
```

    new param



```python
my_func(param1='new param')
```

    new param


A lot of times you will want to return a value so you can get it equal to another value instead of just printing out with print() function.


```python
def square(x):
    return x**2
```


```python
out = square(2)
```


```python
print(out)
```

    4


## Lambda Expressions or Anonymous Functions


```python
def times2(var):
    return var*2
```


```python
times2(2)
```




    4



The lambda operator or lambda function is a way to create small anonymous functions, i.e. functions without a name. These functions are throw-away functions, i.e. they are just needed where they have been created. With lambda expressions above 2 lines of code can be decreased to one line. You can define functions with lambda expressions. 


```python
lambda var: var*2
```




    <function __main__.<lambda>>




```python
t2=lambda var: var*2
```


```python
t2(2)
```




    4



## map() and filter() functions

Let's say you have a list called seq. Untill now we learned that you can use list comprehension for basic calculation operations over the elements of a list . Here we add one more way to do this; map() function. With map() function you can iterate through any function over your sequence. You can use lambda expressions, built-in functions or your own functions. It takes two arguments: map(function, sequence). When you concenate it with the list function you can create lists with it. 


```python
seq = [1,2,3,4,5]
```


```python
map(times2,seq)
```




    <map at 0x105316748>




```python
list(map(times2,seq))
```




    [2, 4, 6, 8, 10]




```python
list(map(lambda var: var*2,seq))
```




    [2, 4, 6, 8, 10]



If you want to filter out elements in a sequence based off of a function you can use filter() function. filter() function takes (should take) a function or a lambda expression as the first argument and creates a Boolean value for each element in the sequence. If you concatenate the filter function with a list function you can get a list.


```python
filter(lambda item: item%2 == 0,seq)
```




    <filter at 0x105316ac8>




```python
list(filter(lambda item: item%2 == 0,seq))
```




    [2, 4]



## Various common methods

Below I tried to add some commonly used methods for various data types. 

## String Methods


```python
st = 'hello my name is Sam'
```


```python
st.lower()
```




    'hello my name is sam'




```python
st.upper()
```




    'HELLO MY NAME IS SAM'




```python
st.split()
```




    ['hello', 'my', 'name', 'is', 'Sam']




```python
tweet = 'Go Sports! #Sports'
```


```python
tweet.split('#')
```




    ['Go Sports! ', 'Sports']




```python
tweet.split('#')[1]
```




    'Sports'



## Dictionary Methods


```python
d
```




    {'key1': 'item1', 'key2': 'item2'}




```python
d.keys()
```




    dict_keys(['key2', 'key1'])




```python
d.items()
```




    dict_items([('key2', 'item2'), ('key1', 'item1')])




```python
d.values()
```




    dict_values(['item1', 'item2'])



## List Methods


```python
lst = [1,2,3]
```


```python
lst.pop()
```




    3




```python
lst
```




    [1, 2]



In operator : This is an easy way to check whether one element is in your list. 


```python

```


```python
'x' in [1,2,3]
```




    False




```python
'x' in ['x','y','z']
```




    True



## Tuple Unpacking Method

Let's have a list called x which contains tuples. To unpack the tuples inside we can use for loops. Tuple unpacking will be useful for reassignments. Remember tuples are normally immutable. 


```python
x=[(1,2),(3,4),(5,6)]
```


```python
for (a,b) in x:
    print(a)
```

    1
    3
    5


Above code will also work without parenthesis (a,b). By convention you can use them


```python
for a,b in x:
    print(a)
```

    1
    3
    5


# Well Done!
