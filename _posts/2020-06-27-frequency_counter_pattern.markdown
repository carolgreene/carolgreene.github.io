---
layout: post
title:      "Frequency Counter Pattern"
date:       2020-06-27 21:46:16 +0000
permalink:  frequency_counter_pattern
---


I've been learning about Problem Solving Patterns while going through Colt Steele's JavaScript Algorithm and Data Structures class. These patterns make it easier to solve difficult coding problems and can often help you solve these problems using the steps they lay out. One of the patterns that can be used often is the Frequency Counter Pattern.

The Frequency Counter Pattern is good to use when you need to compare the values in 2 or more arrays or other data structures. When you use the Frequency Counter Pattern, you create objects that will collect the number of times numbers in the arrays occur. You can then compare the values for each key to see if the 2 arrays match.

An example of a problem that’s a good candidate for this pattern is a function called sameSquared(). sameSquared() accepts 2 arrays of numbers and has to check to see if each number in the second array is the squared value of each of the numbers in the first array.

We can compare 2 different ways to solve this problem. First we can use a typical basic solution of using nested loops to iterate through the arrays to square each number in the first array and then check to see if those numbers are in the second array. This ends up being a lot of calculations to find the answer.

```
function sameSquared(arr1, arr2) {
  if(arr1.length !== arr2.length) {
  return false;
}
for(let i = 0; i < arr1.length; i++){
  let correctIndex = arr2.indexOf(arr1[i] ** 2)
	if(correctIndex === -1) {
	  return false;
	}
	arr2.splice(correctIndex, 1)
	}
	return true
}

Time Complexity-  0(N^2)
Space Complexity- 0(1)
```


Our other option is to use the Frequency Counter Pattern. In this example we create 2 objects to hold the numbers from each array as the keys and then use the number of times each number occurs as the values for these keys. We then compare to see if the keys from the first frequencyCounter object squared are the keys in the second frequencyCounter object. Then we check to see if the values match for each one.

```
function sameSquared(arr1, arr2) {
  if(arr1.length !== arr2.length) {
	  return false;
	}
	let frequencyCounter1 = {};
	let frequencyCounter2 = {};
	for(let val of arr1) {
	  frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1
	}
	for(let val of arr2) {
	  frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1
	}
	for(let key in frequencyCounter1) {
	  if(!(key ** 2 in frequencyCounter2)) {
		  return false;
		}
		if(frequencyCounter2[key ** 2] !== frequncyCounter1[key]) {
		  return false;
		}
	}
	return true;
}

sameSquared([1,2,3,2], [9,1,4,4])

Time Complexity- 0(N)
Space Complexity- 0(1)		
```

Both of these options will return true, but the Frequency Counter Pattern is much more efficient doing it. This makes a big difference if you're working with large arrays or other data types.


