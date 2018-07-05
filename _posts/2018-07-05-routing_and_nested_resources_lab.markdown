---
layout: post
title:      "Routing & Nested Resources Lab"
date:       2018-07-05 17:39:40 -0400
permalink:  routing_and_nested_resources_lab
---


As the Rails labs are getting more complicated, I've found that it really helps me to slow down and make sure to take it one step at a time. We often have to take several steps to get a specific test to pass, and it's easy to get discouraged.  With this lab, I made a point to follow the instructions given in the read me. I found the first 3 to be very straightforward and didn't have an issue with them.

-First I had to create nested resource routes to show all songs for an artist (/artists/1/songs) and individual songs for that artist (/artists/1/songs/1). Restrict the nested songs routes to index and show actions only.
```
Rails.application.routes.draw do
  resources :artists do
    resources :songs, only: [:index, :show]
  end

  resources :songs
end
```

-Next was to update the artists index view to use the new nested resource route URL helper to link to the index of all songs by that artist. Most of this code was already there. I just needed to make a link using the new nested path.
```
<h1>Artists</h1>
<ul>
  <% @artists.each do |artist| %>
    <li><%= link_to artist.name, artist_songs_path(artist) %></li>
  <% end %>
</ul>
```


-Then update the artists show view to list each song for that artist, and use the new nested resource route helper to link each song to its corresponding show page. I just had to change the path on this requirement also.
```
<h1><%= @artist.name %></h1>
<ul>
  <% @artist.songs.each do |song| %>
    <li><%= link_to song.title, artist_song_path(@artist, song) %></li>
  <% end %>
</ul>
```




I felt pretty good at this point since I was moving right along with the lab. I then got to the next requirement & things started to slow down. The next three steps were to update the Songs Controller for index & show. I first tried to do everything to index at once and found that didn't work at all. I then broke it down by requirement and listed everything out and eventually got the tests to pass.

-The next step was to update the songs_controller to allow the songs#index and songs#show actions to handle a valid song for the artist.
This method will look for an artist by id if an artist is in the params and then assign @songs to that artist's songs. If there is no artist in the params, it will assign @song to Song.all.

```
def index
    if params[:artist_id]
      @artist = Artist.find_by(id: params[:artist_id])
      @songs = @artist.songs
    else
      @songs = Song.all
    end
  end

```



-Then in the songs#index action, if the artist can't be found, redirect to the index of artists, and set a flash[:alert] of "Artist not found."  I added this code into the index method in order to give an error message incase the artist is not found and redirect it to the index of artists. 

```
if @artist.nil?
        flash[:alert] = "Artist not found"
        redirect_to artists_path
      else
        @songs = @artist.songs
      end
```


		
The final songs index method looked like this:
			
```
def index
    if params[:artist_id]
      @artist = Artist.find_by(id: params[:artist_id])
      if @artist.nil?
        flash[:alert] = "Artist not found"
        redirect_to artists_path
      else
        @songs = @artist.songs
      end
    else
      @songs = Song.all
    end
 end


```			 


-Last, in the songs#show action, if the song can't be found for a given artist, redirect to the index of the artist's songs and set a flash[:alert] of "Song not found." This method also checks to see if the params have an artist and then finds it by id if it does and assigns @artist to the artist. It then assigns @song to the artist's song that matches the songs id. If the song doesn't exist, it gives an error message and redirects it to the artist's list of songs. If there is no artist in the params, it will assign @song to the song it finds by id.

```
def show
    if params[:artist_id]
      @artist = Artist.find_by_id(params[:artist_id])
      @song = @artist.songs.find_by_id(params[:id])
      if @song.nil?
        flash[:alert] = "Song not found"
        redirect_to artist_songs_path(@artist)
      end
    else
      @song = Song.find(params[:id])
    end
  end
```
I was so glad to get this done. The lab was really challenging and it helped a lot to just try to follow it step by step.




