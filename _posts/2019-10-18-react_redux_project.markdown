---
layout: post
title:      "React/Redux Project"
date:       2019-10-18 23:53:12 +0000
permalink:  react_redux_project
---


I was so happy to finally finish all of the labs and get to my final project. It's been a long haul with a lot of bumps along the way.  So far I've really liked doing the projects, they've helped me understand the sections so much better. The problem was, there are so many moving parts to the React/Redux project I felt overwelmed. The best advice I can give anyone, is to take some time to watch Howard & Anabel's videos about doing a project with a Rails backend & React/Redux frontend. They walk through it step by step and both do a great job explaining & asking questions to help you understand. It's a lot to get through but both series helped me a ton when it came to understanding just what I was trying to do.  The other thing I found helpful was to chart it all out on paper ahead of time so I understood how my different components would be laid out.

I decided to make a Movie App called Movie-Cue. It has a listing of movies that the user can click on to find out more about it and to read reviews. Users can add a movie, write a review, and read other's reviews. They can also edit & delete a movie & delete a review.

I took the advice I had heard from others and kept the app simple. I started  without a users component and figured I could add it, along with signing-up & signing-in, if I had time. I'm glad I did that because I ran into several problems and ended up just leaving it without a users component for now. 

Since you would never have a review without a movie, I decided to nest reviews within movies. I set up my routes like this:

``Rails.application.routes.draw do 
  namespace :api do
    namespace :v1 do       
      resources :movies do
        resources :reviews            #nested reviews inside of movies
      end
    end
  end
  
end`

```

I got the backend done pretty quickly, setting up my databases, models, & controllers. I used the fastJson serializer after I saw Howard's video &  thought it would be fun to try a different serializer.

I spent the bulk of the rest of my time working on the frontend.  I had laid out my basic set up ahead of time and had a Movies Container with MovieCard, MovieForm, & Movies components as children. The ReviewContainer was a child of MovieCard and ReviewCard, ReviewForm, & Reviews were the children of the ReviewContainer. 

All in all I thought this was a great exercise in learning how to work through a program. I used a lot of console.logs to find out where I was running into problems as I worked through the handlers, on to the actions and reducer.  I feel like I still have a lot to do to make it the way I'd like it to be, with users & also additional styling to make it look more professional.  But I'm happy with the app and am looking forward to fine tuning it and moving on to my job search!





