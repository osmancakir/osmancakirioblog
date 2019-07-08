---
title: "Javascript ES7 4 : Destructuring and Constructor Functions"
author: "Osman Cakir"
date: 2019-07-04
description: "Javascript ES7 Functionalities"
type: technical_note
draft: false
---
This is going to be the last notebook for our small project about learning JS and ES7 functionalities. Hope you enjoyed learning it. 


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


     19 - Destructuring Assignment to Assign Variables from Objects
             * Change the order of elements in arrays with destructuring
             * Another use of Destructuring
             * Destructuring Assignment to Pass an Object as a Function's Parameters
     20 - Create Literals Using Template Literals 
     21 - Write Concise Object Literal Declerations Using Simple Fields
     22 - Write Concise Declarative Functions
     23 - Using class Syntax to Define a Constructor Function
     24 - Use getters and setters to Control Access to an Object
     25 - Import and Export vs Require

## 19 - Destructuring Assignment to Assign Variables from Objects


```python
%%node
var voxel = {x:3.6, y:7.4, z:6.54}; 
var x = voxel.x
var y = voxel.y
var z = voxel.z // old way to assign an js object's properties to variables
```


```python
%%node
const { x: a, z: b, k:c } = voxel // 
```


```python
%%node
// you can also use destructuring assignment with arrays 
const [z,x,,y] = [1,2,3,4,5,6]; // will take 1,2 and 4. 3 is skipped with a comma. assignment follows order
console.log(z,x,y)
```

### Change the order of elements in arrays with destructuring


```python
%%node
let a1 = 8, b1 = 6;
(() => {
    "use strict"
    [a1,b1] = [b1,a1]
})()
console.log(a1)
console.log(b1)
```

    ... ... ...
    8
    
    6
    


### Another use of Destructuring


```python
%%node
const source = [1,2,3,4,5,6,7,8,9,10];
function removeFirstTwo(list) {
    const [, , ...arr] = list; //spread operator used to copy the rest. 
    return arr;
}
const arr = removeFirstTwo(source);
console.log(arr)
```

    ... ... ...
    [ 3, 4, 5, 6, 7, 8, 9, 10 ]
    


### Destructuring Assignment to Pass an Object as a Function's Parameters

Below stats object passed in wholely but we use only two elements in half() function.  Insted of doing it like this we can pass in object destructuring directly inside the half function and so do not need to pull all the objects data but get only the data we need


```python
%%node
const stats = {
    max : 56,
    median: 34,
    min: 0.75 
}
const half = (function() {
    return function half(stats) {
        return (stats.max + stats.min) / 2.0
    }
})();

console.log(half(stats))
```

    ... ... ... ...
    ... ..... ..... ...
    28.375
    


Now we will only get the max and min elements when stats object is passed in to the half() function. This is especially important with API calls. When you are getting information from an AJAX request or API request it will often will have lot more information than what you need. and you can use destructuring to get the only things you want!


```python
%%node
 const stats1 = {
    max : 56,
    median: 34,
    min: 0.75 
}
const half = (function() {
    return function half({ max, min }) {
        return (stats1.max + stats1.min) / 2.0
    }
})();

console.log(half(stats1))
```

    ... ... ... ...
    ... ..... ..... ...
    28.375
    


## 20 - Create Literals Using Template Literals 
- Use back ticks \``
- Multi line strings are possible
- You don't need to escape double or single quaotation marks in your strings
- You can put variables right inside the strings with `${person.name}` for example. person is an object and name is an   element of this object in
  this example

## 21 - Write Concise Object Literal Declerations Using Simple Fields


```python
%%node
  const createPerson = (name, age, gender) => {
        return {
            name: name, 
            age: age,
            gender: gender
        }
    }
```

    ... ..... ..... ..... ..... ...


above was the way we learned to create a js object with a function. 
instead of this we can do also 


```python
%%node
const createPerson1 = (name, age, gender) => ({name,age,gender})
```

## 22 - Write Concise Declarative Functions 


```python
%%node
const bicycle = {
    gear: 2,
    setGear: function(newGear) {
        "use strict";
        this.gear = newGear;
    }
}
bicycle.setGear(3)
```

    ... ... ..... ..... ..... ...


we can also do this without calling function! 


```python
%%node
const bicycle = {
    gear: 2,
    setGear:(newGear) {
        "use strict";
        this.gear = newGear;
    }
}
bicycle.setGear(3)
```

## 23 - Using class Syntax to Define a Constructor Function


```python
%%node
function makeClass() {
    class Vegetable {
        constructor(name){
            this.name = name
        }
    }
    return Vegetable
}

const Vegetable = makeClass()
const carrot = new Vegetable('carrot')
console.log(carrot.name)
```

## 24 - Use getters and setters to Control Access to an Object


```python
%%node
class Book {
    constructor(author) {
        this._author = author; // this means that you are creating a private variable that is accesible within the 
        // scope of this code. by convention this variables start with _notation
    }
    // getter
    get writer(){
        return this._author;
    }
    // setter
    set writer(UpdatedAuthor){
        this._author = updatedAuthor;
    }
}
```

## 25 - Import and Export vs Require

    export const capitalizeString  = (string) => ....// function to be exportable to another file. 
    import { capitalizeString } from "./string_function" the file name
    
    export a variable : export const foo = "bar"
    exporting a function another way : export {capitalizeString}
    
    import everything from a file : import * as capitalizeStrings from "capitalizeStrings"
    export default function ..... : you gonna only export this from this file
    import subtract from "math_functions" notice you did not need the curly brackets to import an export default function

# Thank You! 

Please let me know any typos or suggestions regarding the notebook. 
