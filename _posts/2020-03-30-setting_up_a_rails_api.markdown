---
layout: post
title:      "Setting up a Rails API"
date:       2020-03-30 23:04:36 +0000
permalink:  setting_up_a_rails_api
---


I've spent this week working on the backend of my latest Rails/Javascript project called binge-tv. I decided with the stay at home order that has been instituted in my state, it would be good to have a listing of binge-worthy TV shows to watch, the happier the show the better!

It's funny how quickly you can forget the basics of setting up an app. I found I needed to look up the steps to follow to make sure I got them right. 

The first thing I did was to create an API-only Rails app by running the following in my terminal:

rails new binge-tv-api  --api

This created my rails app without any views, since I would be using the backend strictly as an api, and will be using JavaScript for the frontend.  Then I ran the rails generator to generate the resources for my app.  I'm keeping it simple to start so I'm just having show and user.

rails g resource show name genre summary
rails g rsource user email password_digest

This created my migrations, which I then ran with rails db:migrate to create my models and controllers.  I entered some simple seed data and verified it worked in the console. 


I then needed to make sure that I made my controllers API controllers since  they will inherit from ActionController::API instead of ActionController::Base. To do this I needed to add an API folder under contollers, and then add a V1 folder under the API folder. I then moved my ShowsController and UsersController files into the newly created V1 folder and changed the code in the controller as to reflect the change.

```
class Api::V1::ShowsController < ApplicationController

```

I entered some basic code in the controllers and then set up my api routes in config.routes:

```
Rails.application.routes.draw do
  namespace :api do
    namespace :v1 do
      resources :users
      resources :shows
    end
  end
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```

With this done, I was basically set up to go. I just need to set up my serializer and tell the controllers to render in json and get my users set up and then I can move on to the frontend. I'm sure I'll be adding additional features to this to make it more powerful, but this was a good refresher on the basics for setting up a Rails API.

