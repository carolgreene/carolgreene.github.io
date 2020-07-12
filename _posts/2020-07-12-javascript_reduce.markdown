---
layout: post
title:      "JavaScript .reduce()"
date:       2020-07-12 15:57:48 +0000
permalink:  javascript_reduce
---


The reduce() method executes a reducer function on each element of an array and gives a single output value. It uses the basic format of 

array.reduce(callback( accumulator, currentValue[, index [, array]] ),  initialValue);

The reducer function can take up to four arguments:

1. Accumulator
2. Current Value
3. Current Index
4. Source Array

The callback function will execute on each element in the array(except the first, if no initial value is given).

As mentioned above, the callback function can take up to four arguments, of which, two are required.

accumulator- Required argument. The accumulator is the value that we end up with after the callback function iterates through each element of the array and is the return value of the function.

currentValue- Required argument. The current element that is being processed in the array.

index- Optional. The index of the current element that is being processed. It will start with 0 if an initialValue is given, otherwise it will start with 1.

array- Optional. This is the array that .reduce() is being called on.

initialValue- Optional. A value to use as the currentValue on the first element of the array.

Here's a simple example:
```
//Initial value
const initialValue = 0;

//array to use .reduce on
const numbers = [1, 2, 3, 4]


//reducer method taking in the accumulator & current value
const reducer = (accumulator, item) => {
  console.log("accumulator:", accumulator + item, "item:", item) 
  return accumulator + item;
}

//variable assigned to call the function
const total = numbers.reduce(reducer, initialValue)


//logged to the computer
"accumulator:", 1, "item:", 1
"accumulator:", 3, "item:", 2
"accumulator:", 6, "item:", 3
"accumulator:", 10, "item:", 4

```
I've added a console log to the method to show what happens when .reducer is called. You'll notice that it is called 4 times on the 4 elements of the numbers array. It starts by adding the item 1 to the initialValue of 0 for an accumulator total of 1 after the first call. It then goes on and adds each item to the accumulator value until it ends with the total of 10, which is the return value of the function.

This method can come in very handy when you need to accumulate the values in an array. I'll go into how to flatten an array using .reduce and how you can manipulate the values in a follow-up post.




