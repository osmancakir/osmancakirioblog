---
title: "Python 4 : Data Analysis with Numpy"
author: "Osman Cakir"
date: 2020-11-10
description: "Introduction to Numpy"
type: technical_note
draft: false
---

Published at: 02.12.2018
Updated at : 10.11.2020

 We will have 3 big sections on NumPy. 

* 1 - NumPy Introduction
* 2 - NumPy Indextion and Selection
* 3 - NumPy Operations


# 1 - NumPy Introduction

## Installation Instructions

It is highly recommended you install Python using the Anaconda distribution to make sure all underlying dependencies (such as Linear Algebra libraries) all sync up with the use of a conda install. If you have Anaconda, install NumPy by going to your terminal or command prompt and typing:
    
    conda install numpy
    
**If for some reason you do not like Anaconda and do not want to install it, go visit [Numpy's official documentation on various installation instructions.](http://docs.scipy.org/doc/numpy-1.10.1/user/install.html)**

## Using NumPy

Once you've installed NumPy you can import it as a library:


```python
import numpy as np
```

Numpy has many built-in functions and capabilities. We won't cover them all but instead we will focus on some of the most important aspects of Numpy: arrays (vectors, matrices), and number generation. Let's start by discussing arrays.

# Numpy Arrays

NumPy arrays are the main way we will use Numpy throughout the course. Numpy arrays essentially come in two flavors: vectors and matrices. Vectors are strictly 1-d arrays and matrices are 2-d (but you should note a matrix can still have only one row or one column).

Let's begin our introduction by exploring how to create NumPy arrays.

## Creating NumPy Arrays

### From a Python List

We can create an array by directly converting a list or list of lists:


```python
my_list = [1,2,3]
my_list
```




    [1, 2, 3]



One important **bullet point** here: Whenever you want to use a package's function you use `package_abbreviation.function` notation. (Ex.: `np.array()`)

package_abbreviation comes from how you imported the package (i.e. `import numpy as np`)


```python
np.array(my_list)
```




    array([1, 2, 3])




```python
my_matrix = [[1,2,3],[4,5,6],[7,8,9]]
my_matrix
```




    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]




```python
np.array(my_matrix)
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])



## Built-in Functions in NumPy to generate Arrays

There are lots of built-in ways to generate Arrays

### ``np.arange()`

Very similar to `range()` function, `np.arange(start(inclusive), stop(exclusive), step))` function returns evenly spaced values within a given interval.


```python
np.arange(0,10)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
np.arange(0,11,2)
```




    array([ 0,  2,  4,  6,  8, 10])



### zeros and ones

To generate arrays of zeros or ones: 

+ `np.zeros(shape of the matrix typed in as a tuple (rows, columns)`
+ `np.ones(shape of the matrix typed in as a tuple)` When only one argument is given, creates a vector.



```python
np.zeros(3)
```




    array([ 0.,  0.,  0.])




```python
np.zeros((5,5))
```




    array([[ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.]])




```python
np.ones(3)
```




    array([ 1.,  1.,  1.])




```python
np.ones((3,3))
```




    array([[ 1.,  1.,  1.],
           [ 1.,  1.,  1.],
           [ 1.,  1.,  1.]])



### `np.linspace()`
Returns evenly spaced numbers over a specified interval. `np.linspace(start, stop, number of numbers to be returned)`. **Notice** that stop is inclusive here. 


```python
np.linspace(0,10,3)
```




    array([  0.,   5.,  10.])




```python
np.linspace(0,10,50)
```




    array([  0.        ,   0.20408163,   0.40816327,   0.6122449 ,
             0.81632653,   1.02040816,   1.2244898 ,   1.42857143,
             1.63265306,   1.83673469,   2.04081633,   2.24489796,
             2.44897959,   2.65306122,   2.85714286,   3.06122449,
             3.26530612,   3.46938776,   3.67346939,   3.87755102,
             4.08163265,   4.28571429,   4.48979592,   4.69387755,
             4.89795918,   5.10204082,   5.30612245,   5.51020408,
             5.71428571,   5.91836735,   6.12244898,   6.32653061,
             6.53061224,   6.73469388,   6.93877551,   7.14285714,
             7.34693878,   7.55102041,   7.75510204,   7.95918367,
             8.16326531,   8.36734694,   8.57142857,   8.7755102 ,
             8.97959184,   9.18367347,   9.3877551 ,   9.59183673,
             9.79591837,  10.        ])



## `np.eye()`

Creates an identity matrix. Assuming you know what is an identity and matrix. Otherwise check it out the use of it.


```python
np.eye(4)
```




    array([[ 1.,  0.,  0.,  0.],
           [ 0.,  1.,  0.,  0.],
           [ 0.,  0.,  1.,  0.],
           [ 0.,  0.,  0.,  1.]])



## Generating Random Number Arrays

Numpy also has lots of ways to create random number arrays. Do not forget to type in `np.random` first when using random number generating functions!. It is a common mistake you will do when you start coding. 

### `np.random.rand()`
Creates an array of the given shape and populate it with
random samples from a uniform distribution
over ``[0, 1)``. If no argument is given, creates a single float`.


```python
np.random.rand(2)
```




    array([ 0.11570539,  0.35279769])




```python
np.random.rand(5,5)
```




    array([[ 0.66660768,  0.87589888,  0.12421056,  0.65074126,  0.60260888],
           [ 0.70027668,  0.85572434,  0.8464595 ,  0.2735416 ,  0.10955384],
           [ 0.0670566 ,  0.83267738,  0.9082729 ,  0.58249129,  0.12305748],
           [ 0.27948423,  0.66422017,  0.95639833,  0.34238788,  0.9578872 ],
           [ 0.72155386,  0.3035422 ,  0.85249683,  0.30414307,  0.79718816]])



### `np.random.randn()`

Returns a sample (or samples) from the "standard normal" distribution. Unlike rand which is uniform:


```python
np.random.randn(2)
```




    array([-0.27954018,  0.90078368])




```python
np.random.randn(5,5)
```




    array([[ 0.70154515,  0.22441999,  1.33563186,  0.82872577, -0.28247509],
           [ 0.64489788,  0.61815094, -0.81693168, -0.30102424, -0.29030574],
           [ 0.8695976 ,  0.413755  ,  2.20047208,  0.17955692, -0.82159344],
           [ 0.59264235,  1.29869894, -1.18870241,  0.11590888, -0.09181687],
           [-0.96924265, -1.62888685, -2.05787102, -0.29705576,  0.68915542]])



### `np.random.randint()`

Returns random integers from `low` (inclusive) to `high` (exclusive).


```python
np.random.randint(1,100)
```




    44




```python
np.random.randint(1,100,10)
```




    array([99, 75, 46, 34,  5, 24, 60, 10, 44, 20])



## Array Attributes and Methods

Let's discuss some useful attributes and methods or an array. Below two arrays created with `np.arange()` and `np.random.randint()`.


```python
arr = np.arange(25)
ranarr = np.random.randint(0,50,10)
```


```python
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23, 24])




```python
ranarr
```




    array([10, 12, 41, 17, 49,  2, 46,  3, 19, 39])



## `.reshape()`
With `.reshape()` method you can return an array containing the same data with a new shape. Below the one dimensional arr array is reshaped to 5 rows and 5 columns two dimensional matrix. Important **bullet point** here: When you apply methods to the objects (numpy objects or other objects that numpy can work with) you do not need to type in 'np.' notation any more. (ie. arr is an array object and numpy's `.reshape()` method can be run without `np.`)


```python
arr.reshape(5,5)
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])



### `max()`,`min()`,`argmax()`,`argmin()`

These are useful methods for finding max or min values in the arrays. To find their index locations use argmin and argmax.


```python
ranarr
```




    array([10, 12, 41, 17, 49,  2, 46,  3, 19, 39])




```python
ranarr.max()
```




    49




```python
ranarr.argmax()
```




    4




```python
ranarr.min()
```




    2




```python
ranarr.argmin()
```




    5



## Attributes : `shape`

`shape` shows the shape attribute of arrays. Attributes are not methods. Notice there are no paranthesis () on them.


```python
# Vector
arr.shape
```




    (25,)




```python
# Notice the two sets of brackets
arr.reshape(1,25)
```




    array([[ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
            17, 18, 19, 20, 21, 22, 23, 24]])




```python
arr.reshape(1,25).shape
```




    (1, 25)




```python
arr.reshape(25,1)
```




    array([[ 0],
           [ 1],
           [ 2],
           [ 3],
           [ 4],
           [ 5],
           [ 6],
           [ 7],
           [ 8],
           [ 9],
           [10],
           [11],
           [12],
           [13],
           [14],
           [15],
           [16],
           [17],
           [18],
           [19],
           [20],
           [21],
           [22],
           [23],
           [24]])




```python
arr.reshape(25,1).shape
```




    (25, 1)



### Attributes : `dtype`

`dtype` shows the data type of the object in the array. **Notice** it is different than the `type()` function. `type()` function shows the type of the object. -->`type(arr)` would return `numpy.ndarray`.


```python
arr.dtype
```




    dtype('int64')



*Well done Now you have finished the first Section of the NumPy! Have a break now, maybe grab a coffee or something, before continuing. : )* 

# 2 - NumPy Indexing and Selection

In this session we will see how to select elements or groups of elements from an array.


```python
# Let's create a sample array
arr = np.arange(0,11)
```


```python
#Show it
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])



## Bracket Indexing and Selection
This is the simplest way to pick one or some elements of an array. It's very similar to python lists:


```python
#Geting a value at an index
arr[8]
```




    8




```python
#Getting values in a range example
arr[1:5]
```




    array([1, 2, 3, 4])




```python
#Get values in a range example 2
arr[0:5]
```




    array([0, 1, 2, 3, 4])



## Broadcasting

This is a very important feature. Unlike Python lists, NumPy arrays have the ability to broadcast:


```python
#Setting a value with index range (Broadcasting)
arr[0:5]=100

#Show
arr
```




    array([100, 100, 100, 100, 100,   5,   6,   7,   8,   9,  10])



**Now again it is very important to keep in mind that Python will not copy the lists or arrays unless you specifically mean it. If you make changes on a slice of an array, the changes will be applied to the original list too.**


```python
# Reset array, we'll see why I had to reset in  a moment
arr = np.arange(0,11)

#Show
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])




```python
#Important notes on Slices
slice_of_arr = arr[0:6]

#Show slice
slice_of_arr
```




    array([0, 1, 2, 3, 4, 5])




```python
#Change Slice
slice_of_arr[:]=99

#Show Slice again
slice_of_arr
```




    array([99, 99, 99, 99, 99, 99])



Now note the changes also occur in our original array!


```python
arr
```




    array([99, 99, 99, 99, 99, 99,  6,  7,  8,  9, 10])



Data is not copied, it's a view of the original array! This avoids memory problems!


```python
#To get a copy, need to be explicit
arr_copy = arr.copy()

arr_copy
```




    array([99, 99, 99, 99, 99, 99,  6,  7,  8,  9, 10])



## Indexing a 2D array (matrices)

The general format is **`arr_2d[row][col]`** or **`arr_2d[row,col]`**. The second method is more common to see. But it is your taste how to index anyways.


```python
arr_2d = np.array(([5,10,15],[20,25,30],[35,40,45]))

#Show
arr_2d
```




    array([[ 5, 10, 15],
           [20, 25, 30],
           [35, 40, 45]])




```python
#Indexing row
arr_2d[1]
```




    array([20, 25, 30])




```python
# Format is arr_2d[row][col] or arr_2d[row,col]
# Getting individual element value 1st Method
arr_2d[1][0]
```




    20




```python
# Getting individual element value 2nd Method
arr_2d[1,0]
```




    20




```python
# 2D array slicing

#This will get all the elements of indexed 0 row and indexed 1 row and 
#from indexed 1 column to the rest of the columns.
arr_2d[:2,1:]
```




    array([[10, 15],
           [25, 30]])




```python
#This will get the indexed 2 row.
arr_2d[2]
```




    array([35, 40, 45])




```python
#This will alo get the indexed 2 row. 
arr_2d[2,:]
```




    array([35, 40, 45])



### Fancy Indexing

Fancy indexing allows you to select entire rows or columns out of order,to show this, let's quickly build out a numpy array:


```python
#Set up matrix
arr2d = np.zeros((10,10))
```


```python
#Length of array
arr_length = arr2d.shape[1]
```


```python
#Set up array

for i in range(arr_length):
    arr2d[i] = i
    
arr2d
```




    array([[0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
           [1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [2., 2., 2., 2., 2., 2., 2., 2., 2., 2.],
           [3., 3., 3., 3., 3., 3., 3., 3., 3., 3.],
           [4., 4., 4., 4., 4., 4., 4., 4., 4., 4.],
           [5., 5., 5., 5., 5., 5., 5., 5., 5., 5.],
           [6., 6., 6., 6., 6., 6., 6., 6., 6., 6.],
           [7., 7., 7., 7., 7., 7., 7., 7., 7., 7.],
           [8., 8., 8., 8., 8., 8., 8., 8., 8., 8.],
           [9., 9., 9., 9., 9., 9., 9., 9., 9., 9.]])



Fancy indexing allows the following


```python
arr2d[[2,4,6,8]]
```




    array([[2., 2., 2., 2., 2., 2., 2., 2., 2., 2.],
           [4., 4., 4., 4., 4., 4., 4., 4., 4., 4.],
           [6., 6., 6., 6., 6., 6., 6., 6., 6., 6.],
           [8., 8., 8., 8., 8., 8., 8., 8., 8., 8.]])




```python
#Allows in any order
arr2d[[6,4,2,7]]
```




    array([[6., 6., 6., 6., 6., 6., 6., 6., 6., 6.],
           [4., 4., 4., 4., 4., 4., 4., 4., 4., 4.],
           [2., 2., 2., 2., 2., 2., 2., 2., 2., 2.],
           [7., 7., 7., 7., 7., 7., 7., 7., 7., 7.]])



## A little bit external help is not harmful.
Indexing a 2d matrix can be a bit confusing at first, especially when you start to add in step size. Try google image searching NumPy indexing to find useful images

## Selection

Above we discussed how we can select elements from NumPy arrays with indexing. Let's briefly go over how to use brackets for selection based off of comparison operators.


```python
arr = np.arange(1,11)
arr
```




    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10])



With NumPy arrays operations with comparison operators creates arrays of boolean values. **Remember** This will not work with lists. And with NumPy arrays we can even do conditional selection using this feature.


```python
arr > 4
```




    array([False, False, False, False,  True,  True,  True,  True,  True,
            True])




```python
bool_arr = arr>4
```


```python
bool_arr
```




    array([False, False, False, False,  True,  True,  True,  True,  True,
            True])




```python
arr[bool_arr]
```




    array([ 5,  6,  7,  8,  9, 10])




```python
arr[arr>2]
```




    array([ 3,  4,  5,  6,  7,  8,  9, 10])




```python
x = 2
arr[arr>x]
```




    array([ 3,  4,  5,  6,  7,  8,  9, 10])



**Well done! Selection and Indexing is really really important. I can not recommend more to practice on this... Ready? Let's go the final session of NumPy.** 

# 3 - NumPy Operations

## Arithmetic

Arithmetic operations with matrices could never been easier! Let's see some examples:


```python
arr = np.arange(0,10)
```


```python
arr + arr
```




    array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])




```python
arr * arr
```




    array([ 0,  1,  4,  9, 16, 25, 36, 49, 64, 81])




```python
arr - arr
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])




```python
# Another nice feature of Numpy: NumPy will give you a warning on division by zero, but not an error!
# Just replaced with nan
arr/arr
```

    C:\ProgramData\Anaconda3\lib\site-packages\ipykernel_launcher.py:3: 
    RuntimeWarning: invalid value encountered in true_divide
    This is separate from the ipykernel package so we can avoid doing imports until

    array([nan,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.])




```python
# Getting a warning not an error policy also applies to integer/0. NumPy will output infinity.
1/arr
```

    C:\ProgramData\Anaconda3\lib\site-packages\ipykernel_launcher.py:2: 
    RuntimeWarning: divide by zero encountered in true_divide
      
    array([       inf, 1.        , 0.5       , 0.33333333, 0.25      ,
           0.2       , 0.16666667, 0.14285714, 0.125     , 0.11111111])




```python
arr**3
```




    array([  0,   1,   8,  27,  64, 125, 216, 343, 512, 729], dtype=int32)



## Universal Array Functions

Though NumPy is not a scientific calculation library, it comes with many [universal array functions](http://docs.scipy.org/doc/numpy/reference/ufuncs.html), which are essentially just mathematical operations you can use to perform the operation across the array. Let's show some common ones:


```python
#Taking Square Roots
np.sqrt(arr)
```




    array([0.        , 1.        , 1.41421356, 1.73205081, 2.        ,
           2.23606798, 2.44948974, 2.64575131, 2.82842712, 3.        ])




```python
#Calcualting exponential (e^)
np.exp(arr)
```




    array([1.00000000e+00, 2.71828183e+00, 7.38905610e+00, 2.00855369e+01,
           5.45981500e+01, 1.48413159e+02, 4.03428793e+02, 1.09663316e+03,
           2.98095799e+03, 8.10308393e+03])




```python
np.max(arr) #same as arr.max()
```




    9




```python
np.sin(arr)
```




    array([ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ,
           -0.95892427, -0.2794155 ,  0.6569866 ,  0.98935825,  0.41211849])




```python
np.log(arr)
```

    C:\ProgramData\Anaconda3\lib\site-packages\ipykernel_launcher.py:1: 
    RuntimeWarning: divide by zero encountered in log
      """Entry point for launching an IPython kernel.

    array([      -inf, 0.        , 0.69314718, 1.09861229, 1.38629436,
           1.60943791, 1.79175947, 1.94591015, 2.07944154, 2.19722458])



**Well Done!**

That's all we need to know for now!
