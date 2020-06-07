---
layout: post
title:      "JavaScript Number Object Cheatsheet"
date:       2020-06-07 19:49:00 +0000
permalink:  javascript_number_object_cheatsheet
---


I've been making Cheatsheets for different aspects of JavaScript  to help me remember  them better. Listed below are the Properties and Methods from my Number Object Cheatsheet.



...........Number Object Properties................

* MIN_SAFE_INTEGER .......The maximum safe integer in JavaScript(253-1)
* MAX_VALUE......................Returns the largest numeric value in JavaScript.   1.79E+308. Values larger than MAX_VALUE are represented as infinity.
* MIN_SAFE_INTEGER.......The minimum safe integer in JavaScript(-(253-1))
* MIN_VALUE......................Returns the smallest positive number value in JavaScript. 5e-324. It is closest to zero, not the most negative number. Smaller numbers are converted to 0.
* NEGATIVE_INFINITY.........Represents the negative infinity value
* NAN....................................Represents "Not a Number" value
* POSITIVE_INFINITY..........Represents infinity value
* prototype............................Allows you to add new properties and methods to a Number object

...........Number Object Methods................

* isFinite()..................Checks whether passed value is a finite number
* isInteger()...............Checks whether passed value is an integer
* isNaN()...................Checks whether passed value is NaN & its type is Number
* isSafeInteger()........Checks whether value is a safe integer
* toExponential().......Converts number to exponential notation
* toFixed().................Formats a number using fixed-point notation
* toPrecision()...........Returns a string representing the number to a specific precision
* toString()................Converts a number to a string
* valueOf()................Returns the primitive value of a Number object

These properties and methods are good to keep in mind.
