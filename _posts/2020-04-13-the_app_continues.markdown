---
layout: post
title:      "The App Continues"
date:       2020-04-13 20:55:30 -0400
permalink:  the_app_continues
---


While continuing to adjust to our new normal of the Covid-19 stay at home orders, I've continued to work on my Binge-TV Rails/JavaScript app. Both my husband and I are working our full-time jobs from home and each day seems to blend into the next. I find it can be more difficult to stay focused on what I'm trying to accomplish and have to stop myself from googling for updates on how the Coronavirus is affecting our area. The numbers are slowing so we're taking comfort in that & hoping that everyone will just stay the course until it's safe.

Once I get rolling on my project, it offers me a good distraction from the events of the day. I've completed my backend and have moved onto the frontend this past week. I've worked on Fetching the list of shows from my backend database and listing them in the DOM. 

```
function fetchShows() {
    let shows = document.getElementById("shows")
    let li = document.createElement("li")
  fetch(`http://10.0.0.99:3000/api/v1/shows`) 
  .then((res) => res.json())
  .then(results => {
     results.data.forEach(show => listShow(show)
        
     )
  })
}

function listShow(show) {
  let showsDiv = document.getElementById("shows")
  let newLi = document.createElement("li")
  newLi.innerText = show.attributes.name   /*`${show.attributes.name}-${show.attributes.genre}`*/
  console.log(show)
  showsDiv.appendChild(newLi)
  
}
```

As usual, once I got to this point, I decided I wanted to make some changes in my app.  I really want to work on how I'm displaying my data and decided to remove my User model for now  and have added a Network model in its place.  A network will have many shows and shows will belong to a network. This way I can focus on manipulating the data I have and improve my JavaScript and CSS skills in displaying it. I figure I can always go back and add the User class again later.  Along this line, I decided to work on some of the new labs in the JavaScript section that weren't included before.  I'm currently working on the Pokemon Teams lab. This is helping to firm up my understanding which I'm sure will help me do a better job on my Binge-TV project.
