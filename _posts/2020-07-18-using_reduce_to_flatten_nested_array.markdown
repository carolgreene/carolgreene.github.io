---
layout: post
title:      "Using .reduce() to flatten nested array"
date:       2020-07-18 20:40:17 +0000
permalink:  using_reduce_to_flatten_nested_array
---


I went over the basics of the reduce() method in a previous post and am going to go over how to flatten an array using  it here. To review, the reduce() method executes a reducer function on each element of an array and gives a single output value. 


The reducer function can take up to four arguments:

Accumulator
Current Value
Current Index
Source Array
The callback function will execute on each element in the array(except the first, if no initial value is given).

When you flatten an array, you can take an array of arrays, or nested array, and convert it into 1 single array. Here's an example listed below:

```
let array = [ [1,2,3], [4,5,6], [7,8,9] ]
```
To flatten this array using .reduce, all we need to do is call .reduce on the array and set the arguments of the Accumulator, which will hold the values from the array and the Current Value, which will be the nested array being reduced.

```
const flat = array.reduce((acc, currVal) => {
console.log('Accumulator', acc, 'currVal', currVal)
return acc.concat(currVal)
})

console.log(flat)
```
When I call the method, I get the following in the Console:

```
"Accumulator", [1, 2, 3], "currVal", [4, 5, 6]
"Accumulator", [1, 2, 3, 4, 5, 6], "currVal", [7, 8, 9]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

I included some console.logs in the method so you can see what happens with each run through. Because I did not give an initial value to the Accumulator, it took the first nested array and used that as the initial value so the first run through shows [1, 2, 3] as the Accumulator total.  The currVal shows the 2nd nested array of [4, 5, 6]. On the 2nd run through you can see the 2nd array is now included in the Accumulator along with the first array and the last array is in the currVal. Finally, you see a listing of the full flattened array showing the nesting is gone and all elements are listed in the one single array.





