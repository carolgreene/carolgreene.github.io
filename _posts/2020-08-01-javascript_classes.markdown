---
layout: post
title:      "JavaScript Classes"
date:       2020-08-01 17:22:51 +0000
permalink:  javascript_classes
---


Prior to the 2015 implementation of ES6, JavaScript did not have classes. With their addition, JavaScript can now look more like other languages. However, classes don't offer any additional functionality over what was already available with prototypes and inheritance. Because of this, they are often describes as 'syntactical sugar'. One difference to keep in mind is that function declarations are hoisted and class decorations are not. 

A JavaScript class is a type of function that is declared with the class keyword and its structure is very similar to a constructor function.

```
// Initializing a constructor function
function Dog(breed, name) {
  this.breed = breed;
  this.name = name;
}
```

```
//Initializing a class definition
class Dog {
  constructor(breed, name) {
    this.breed = breed;
    this.name = name;
  }
```

With constructor functions, we assign the method  directly to the prototype as shown below:

```
// Initializing a constructor function
function Dog(breed, name) {
  this.breed = breed;
  this.name = name;
}

//Adding a prototype method
Dog.prototype.walk = function() {
  return `${this.name} the ${this.breed} is going for a walk.`
}
```

To add a method to the class, you leave off the function keyword and just list the method as shown below:

```
//Initializing a class definition
class Dog {
  constructor(breed, name) {
    this.breed = breed;
    this.name = name;
  }

//Adding a method
  walk() {
    return `${this.name} the ${this.breed} is going for a walk.`
  }
}
```

Creating a new object is done the same way, with the new keyword, whether you're using the constructor function or the class definition.

```
let max = new Dog('labradoodle', 'Max')
console.log(max)
```

The output returns the object showing its properties of breed and name, along with the prototype function, walk().
```
{
  breed: "labradoodle",
  name: "Max",
  walk: function() {
  return `${this.name} the ${this.breed} is going for a walk.`
}
}
```

Overall, I think classes are a good addition to JavaScript. The format is easier to read than functional prototypes and they make the code look more like other languages. Classes in JavaScript also offer some additional features such as static methods & extend that I'll go over in a future blog.




