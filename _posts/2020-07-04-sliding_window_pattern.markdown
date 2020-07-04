---
layout: post
title:      "Sliding Window Pattern"
date:       2020-07-04 15:50:09 +0000
permalink:  sliding_window_pattern
---


I’ve been learning about Problem Solving Patterns while going through Colt Steele’s JavaScript Algorithm and Data Structures class. These patterns make it easier to solve difficult coding problems by using the steps they lay out. One of the patterns that can be used often is the Sliding Window Pattern.

The Sliding Window Pattern is good to use when you have a set of data, like an array, and need to find a subset that is continuous. When you use the Sliding Window Pattern, you create a window, which can either be an array position or number from one position to another. Depending on a certain condition, you can then increase, decrease, or slide the window to create a new window.

An example of a problem that’s a good candidate for this pattern is a function called maxSubarraySum(). maxSubarraySum() accepts an array of integers and a number called n. The function has to calculate the sum of each set of n numbers to check to see which set has the highest sum.

We can compare 2 different ways to solve this problem. First we can use a typical basic solution of using nested loops to iterate through the array to add each group of numbers in the array, put the sum in a temp variable and then check to see if the temp variable is larger than the max that has been found so far. If so, make the max equal to temp. This ends up being a lot of calculations to find the answer.

```
function maxSubarraySum(array, num) {
  if (num > array.length) {
    return null;
  }
  let max = -Infinity;
  for (let i = 0; i < array.length - num + 1; i ++) {
    temp = 0;
    for (let j = 0; j < num; j++) {
      temp += arr[i + j];
    }
    if ( temp > max ) {
      max = temp;
    }
  }
  return max;
}

maxSubarraySum([2,6,9,2,1,8,5,6,3], 3)

Time Complexity-  0(N^2)
```

Our other option is to use the Sliding Window  Pattern. In this example we set up maxSum and tempSum and set to zero. We then set up a for loop and add the first set of numbers and store it in maxSum & tempSum. Then, instead of adding the next 3 numbers together, we take our previous sum in temp sum and subtract the number in the lowest index and add in the number in the next index. This way we don't have to do a nested loop.

```
function maxSubarraySum(array, num) {
  let maxSum = 0;
  let tempSum = 0;

  if (array.length < num) return null;
  for (let i = 0; i < num; i++) {
    maxSum += array[i]
  }
  tempSum = maxSum;
    for (let i = num; i < array.length; i++) {
    tempSum = tempSum - array[i - num] + array[i];
    maxSum = Math.max(maxSum, tempSum);
  }
  return maxSum;
}

maxSubarraySum([2,6,9,2,1,8,5,6,3], 3)

Time Complexity- 0(N)
```


		
Both of these options will return 19, but the Sliding Window Pattern is much more efficient doing it. This makes a big difference if you’re working with large arrays or other data types.


