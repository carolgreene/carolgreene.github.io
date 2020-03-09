---
layout: post
title:      "What's not to like?"
date:       2020-03-09 23:25:59 +0000
permalink:  whats_not_to_like
---


As I continue to review JavaScript, I've been doing small projects along with mixing in some of the new JavaScript material from the class that was not available when I did this section.  I completed 2 small apps and then decided to try the js dom challenge. I thought it was a great lab. It had a working version of the app, that I just had to recreate with my own code. No tests, just working in the browser. I was really happy to see that I felt very comfortable with the lab and was able to work my way through it without too much difficulty, reinforcing the skills I've learned.

While I was completing the portion of the lab where I had to make the like button work, I thought about how often that type of coding is done. Liking something is one of the most common things we see in websites. The first thing I did was to look at the html code to check the button so I'd know what to grab.

```
</h1>
  <button id='minus' > ➖ </button>
  <button id='plus' > ➕ </button>
  <button id='heart' > ❤️ </button>
  <button id='pause' > pause </button>

  <ul class='likes' id="likes"></ul>

```
I assigned a variable to grab the id for the like and also assigned a variable for the ul likes so I'd have somewhere to put the phrase.

```
const like = document.getElementById("heart")
const likes = document.getElementById("likes")

```
I then assigned an event listener to listen for when the like button was clicked. The event listener then called my addLike() to actually add the like.

```
like.addEventListener("click", function(e) {
  addLike()
})

```
My addLike() creates a new li element, assigns it's innerText , and appends it to the likes ul.

```
function addLike() {
  const addLikeLi = document.createElement('li')
  addLikeLi.innerText = counter.innerText + " has been liked"
  likes.appendChild(addLikeLi)
}

```
Now I just have to work out how to calculate how many likes each number gets.

All and all I think this was a great exercise for me to do. Reviewing JavaScript and completing additional projects has really made me feel much more confident in my skills.  


