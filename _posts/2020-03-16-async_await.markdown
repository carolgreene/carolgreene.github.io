---
layout: post
title:      "async/await"
date:       2020-03-17 00:56:06 +0000
permalink:  async_await
---


While I was reviewing different aspects of JavaScript, I decided to go over the fetch() function again. In this case, I was fetching a url to give me random pictures of dogs.

```
function loadImages() {
  const imgUrl = "https://dog.ceo/api/breeds/image/random/4"
  fetch(imgUrl) 
  .then(resp => resp.json())
  .then(results => {
    results.message.forEach(image => addImage(image))
  console.log("image loaded")
  })
}
```
In this code, I assigned a constant variable to the url that I wanted to get the images from.  Once I fetched the url, I had to chain .then statements so the program would know not to do the next step until the step before it was complete.  Once I received the response from my fetch, I converted it to json. After that, I took the results and iterated over the array of images & sent each image to the addImage function in order to display it in the DOM.

While I was doing further research on fetch(), I discovered a different way to do it that was introduced in ES2017................async/await!

The purpose of async/await is to simplify using promises synchronously, and to perform some behavior on a group of Promises. When you use await, it allows the program to run sychronously, even though it is  asynchonous.  

Here is the code I wrote when I used await. I had to add the word async before I named my function and then added the word await next to my fetch and response.

```
async function loadImages() {
  const imgUrl = "https://dog.ceo/api/breeds/image/random/4"
  const response = await fetch(imgUrl) 
  const json = await response.json()
  json.message.forEach(image => addImage(image))
}
```

The code looks a lot cleaner and is easier to read without having to chain .then and the results are exactly the same as the first version. It was fun to practice using fetch again and learn new ways to improve my code by using await!

