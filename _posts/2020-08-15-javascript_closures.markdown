---
layout: post
title:      "JavaScript Closures"
date:       2020-08-15 20:51:10 +0000
permalink:  javascript_closures
---


One of the most common questions asked in JavaScript interviews is to explain what a closure is. It's a concept that can be confusing.

A simple explanation is that a closure in JavaScript is when an outer function contains an inner function and returns that inner function. Because of this relationship, the inner function not only has access to it's own variables, it has access to the outer functions variables as well. Listed below is a simple example of a closure.
```
function outer() {
  let a = 10;

  function inner() {
    let b = 20;
    console.log(a + b)
  }
  return inner;
}

let x = outer()
console.log(x)

//output
function inner() {
  let b = 20;
  console.log(a + b)
}
```
Listed above are two functions.

* The outer() function has a variable named 'a' set to 10 and returns an inner function. 
* The inne()r function has variable 'b' set to 20 and console.logs a + b.
* The scope of variable 'a' is the outer() function.
* The scope of variable 'b' is the inner() function.

When we invoke and the outer() function by setting variable x to outer(), it will return and store the full inner function in x. It will not invoke the inner function. Once the outer() function is finished running all variables within its scope no longer exist. This is a very important point. Variables declared within a function only exist within that function, once the function is completed, they are gone.

In order to invoke the inner() function, we can invoke our variable x.

```
x()

//output
30
```
So when the inner() function is invoked, it console.logs(a + b). But wait, how did it add a + b if 'a' no longer exists once the outer() function has completed?! This is what closure is all about. It is often said that when you set up a closure, the inner function has a backpack and in this backpack are all of the variables declared in the outer function. That way the inner function has access to these variables when it is invoked.

Closures give the inner function access to it's own scope, the outer function's scope, and any global variables. This is called its Lexical Environment. This makes JavaScript a more powerful language.


