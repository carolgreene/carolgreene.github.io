---
layout: post
title:      "My Sinatra Project"
date:       2018-05-12 03:49:30 +0000
permalink:  my_sinatra_project
---



I was really excited to get started on my Sinatra Project. I was so nervous before I started the first project, but after doing it, I realized that the projects really give you  a chance to put everything together and solidify what you've been learning.  We had a lot of practice doing CRUD apps, Create, Read, Update, & Delete so I thought this should be pretty straight forward.

We had the following requirements:

-Build an MVC Sinatra Application.
-Use ActiveRecord with Sinatra.
-Use Multiple Models.
-Use at least one has_many relationship on a User model and one belongs_to relationship on another model
-Must have user accounts. The user that created a given piece of content should be the only person who can  modify that content
-Must have the abilty to create, read, update and destroy any instance of the resource that belongs to a user.
-Ensure that any instance of the resource that belongs to a user can be edited or deleted only by that user.
-You should also have validations for user input to ensure that bad data isn't added to the database. The fields in your signup form should be required and the user attribute that is used to login a user should be a unique value in the DB before creating the user.

I started out by creating my repository and then using a great gem called corneal that I read about created by flatiron alum Brian Emory. It was really great. It created the file tree I needed and loaded the gems I needed for my project. It made getting started much easier. Thanks Brian!  I was really having trouble deciding what type of app to create and then decided to stick with doing something related to travel since that's what I did for my first project.

I made my Trip-Tracker app to have Trips that belong to Users and the Users would have many Trips. My databases were pretty straight forward and I followed a lot of the format from our Fwitter lab. 

I decided I wanted to make the users be able to get to their own list of trips from the index list so I put a link on the bottom of the page. I then made the users list be clickable so they could get to the show page from their list and then edit or delete from show.

I worked through the app on the browser as a user would and tried to take care of any problems that arose, while also making sure they could link to whatever screen they wanted to. I also made sure they got error messages if they tried to alter another users' trips or if they entered their user name or password wrong. 
I ran into a few problems figuring out how to do the validation messages and Dakota was a big help. Thanks to him!  

I know I can do alot to add additional databases & relationships to make my app more useful & complicated in the future. All in all, this was a really fun project that helped me understand Sinatra a lot better. I can't wait to get started on Rails!
