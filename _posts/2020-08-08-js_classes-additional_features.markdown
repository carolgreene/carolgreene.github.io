---
layout: post
title:      "JS Classes-Additional Features"
date:       2020-08-08 17:40:41 +0000
permalink:  js_classes-additional_features
---


In addition to being able to create new objects using constructor and offering prototype methods for these objects to use, JavaScript classes also give us some additional features such as static methods and extends.

A static method is a method that can only be called on the class, meaning they can't be called on an instance of the class. They are often used to create utility functions for the application and are created by writing the word static before the method for the Dog class listed below:


```
let dogs = []

//Initializing a class definition
class Dog {
  constructor(breed, name) {
    this.breed = breed;
    this.name = name;
  }

//Adding a static method
  static printDogs() {
    dogs.map(dog => {
      console.log(dog.name)
    })
  }	
}
```

If I create new Dogs and run the static method on the class I'll get the following output:

```
//Run static method on class
let tommy = new Dog('poodle', 'Tommy')
let mollie = new Dog('lab', 'Mollie')
Dog.printDogs()

//output
"Tommy"
"Mollie"
```

If I try to run the static method on a dog instance, I'll get an error method:

```
//Run static method on instance of dog
let tommy = new Dog('poodle', 'Tommy')
let mollie = new Dog('lab', 'Mollie')
tommy.printDogs()

//output
"Uncaught TypeError: tommy.printDogs is not a function"
```

JavaScript classes also lets you make a class a child of another class by using the keyword extends. This allows the child to inherit the methods of the parent class.

```
//Initializing a class definition
class Dog {
  constructor(name) {    
    this.name = name;
  }

//Adding a method
  walk() {
    return `${this.name} is going for a walk.`
  }
}

//Add child class
class Breed extends Dog {
  constructor(name, breed) {
    super(name)
    this.breed = breed
  }

  show() {
    return this.walk() + '' + this.name + ' is a ' + this.breed
  }
}
```

When you create a new Poodle and run the show method you'll get the following:

```
let tommy = new Breed('Tommy', 'poodle')
console.log(tommy.show())

//output
"Tommy is going for a walk.Tommy is a poodle"
```

JavaScript classes are a good addition to JavaScript. They are easy to read and static methods and extends add to their functionality.

