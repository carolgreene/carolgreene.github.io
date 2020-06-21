---
layout: post
title:      "Multiple Pointers Pattern"
date:       2020-06-21 02:13:03 +0000
permalink:  multiple_pointers_pattern
---


I've been spending time on my Computer Science skills and have been working through Colt Steele's JavaScript Algorithm and Data Structures class. One of the things it covers is Problem Solving Patterns that make it easier to solve difficult coding problems. These patterns can often help you solve these problems using the steps they lay out. One of my favorite patterns is the Multiple Pointer Pattern.

When you use the  Multiple Pointer Pattern you create two pointers that are given values that correspond to indexes in an array or other structure. You can then move these pointers through the structure depending on the results of the logic in your code. This pattern is very efficient for solving problems with minimal space complexity. It is important to note, though, it only works with a sorted structure. If the structure is not sorted, you can't use it unless you sort it yourself first.

An example of a problem that's a good candidate for this pattern is a function called sumZero. sumZero accepts a sorted array of numbers and has to find and return the first pair of numbers that equal zero.

We can compare 2 different ways to solve this problem. First we can use a typical basic solution of using nested loops to iterate through the array to add each number to every other number to check to see if they add to zero and then return the first pair that do. This ends up being a lot of calculations to find the answer.

```
function sumZero(arr) {
   
   for(let i = 0; i < arr.length; i++){     
     for(let j =  i + 1; j < arr.length; j++) {
         if(arr[i] + arr[j] === 0) {
             return [arr[i], arr[j]]
         }
     }
   }
}

sumZero([-4. -3, -2, -1, 0, 1, 2, 3, 5])

Time Complexity-  0(N^2)
Space Complexity- 0(1)
```

Our other option is to use the Multiple Pointers Pattern. In this example we create 2 pointers, one that will start at the beginning of the array(0 index) and the other will start at the end of the array(arr.length - 1). We'll add these 2 numbers together, and move the appropriate pointer depending on whether the total is less than or more than 0.

```
function sumZero(arr) {
    //set variables for the indexes of the 2 pointers
    let left = 0;
    let right = arr.length - 1;
    
    while(left < right) {        
        let sum = arr[left] + arr[right];
        
        if(sum === 0) {
            return [arr[left], arr[right]]            
        } else if(sum > 0) {
            right --;
        } else {
            left ++;
        }
    }
}

sumZero([-4, -3, -2, -1, 0, 1, 2, 3, 5])

Time Complexity- 0(N)
Space Complexity- 0(1)
```
Both of these options will return the same pair, -3, 3, but the Multiple Pointer Pattern is much more efficient doing it.  It does not seem like a big deal when you're working on a small array like the one in the example, but it makes a big difference if you have a lot of data to go through.
