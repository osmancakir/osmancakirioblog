---
title: "Python 2 : Manipulating Lists"
author: "Osman Cakir"
date: 2018-12-02
description: "Python tutorial 2 manipulating lists"
type: technical_note
draft: false
---
First let's create a list called cars


```python
cars=['porsche',60, 'audi',37, 'mercedes', 45, 'bmw',43, 'vw', 32]
```

**Changing Elements** is easy. Call the element by it's index and equal to something else. 


```python
cars[8]='skoda'
```


```python
cars
```




    ['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'skoda', 32]



You can change multiple entries analoguously. 


```python
cars[8:]=['fiat',22]
```


```python
cars
```




    ['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]



**Adding Elements** might be even easier. Just call your list and add something to it. 


```python
cars + ['lancia', 33]
```




    ['porsche',
     60,
     'audi',
     37,
     'mercedes',
     45,
     'bmw',
     43,
     'fiat',
     22,
     'lancia',
     33]



**important** thing to note here. Adding elements to a list with this way won't change the list in memory. If we look at the cars list again it will be same. Lancia will not appear. 


```python
cars
```




    ['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]



If you want to save it, you can give a new name to your list . If you want the changes to be saved in the list you are working on you should use .append() method. (We will cover methods and functions of Python later in more detail, so no worries!)


```python
cars_ext=cars + ['lancia', 33]
```


```python
cars_ext
```




    ['porsche',
     60,
     'audi',
     37,
     'mercedes',
     45,
     'bmw',
     43,
     'fiat',
     22,
     'lancia',
     33]




```python
cars.append('lancia')
```


```python
cars
```




    ['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22, 'lancia']



**Deleting Elements** : For this purpose you can use del() function. 


```python
del(cars[-1])
```


```python
cars
```




    ['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]



**Another important note** When you create a list such as cars here, the variable name cars is just a reference where your list is stored. lets say you created another list (cars2) which is equal to cars (cars=cars2) and then changed one element in cars2. Your cars list will be also affected by this change. Python does not copy unless you specifically copy the list. You can copy the list by:
* cars2=list(cars)
* cars2=cars[:]


```python
cars2=cars
```


```python
cars2[0]='ferrari'
```


```python
cars
```




    ['ferrari', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]




```python
cars=['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]
```


```python
cars2=list(cars)
```


```python
cars2[0]='ferrari'
```


```python
cars
```




    ['porsche', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]




```python
cars2
```




    ['ferrari', 60, 'audi', 37, 'mercedes', 45, 'bmw', 43, 'fiat', 22]



### Adding Two Lists Together 

very intuitional just type : merged_list = list1 + list2


```python
cars_merged=cars + cars2
```


```python
cars_merged
```




    ['porsche',
     60,
     'audi',
     37,
     'mercedes',
     45,
     'bmw',
     43,
     'fiat',
     22,
     'ferrari',
     60,
     'audi',
     37,
     'mercedes',
     45,
     'bmw',
     43,
     'fiat',
     22]



### List Comprehension 

This is actually going to be extremely easy when we learn the numpy arrays but for now it is a nice to know feature so I am gonna add it here. Let's say you have a list x=[1,2,3,4] and you want to make a calculation for every element in the list. Lets say you want to square every element in your list. you just type the following line below. 


```python
x=[1,2,3,4]
x_squared = [num**2 for num in x]
```


```python
x_squared
```




    [1, 4, 9, 16]




```python

```
