---
layout: post
title:      "Refactoring Views With Helpers"
date:       2018-06-12 19:45:59 -0400
permalink:  refactoring_views_with_helpers
---


I've been struggling a bit with Rails as I've moved farther into it  There are so many things that it does, it's hard to keep everything straight, especially how everything interrelates between the different models, controllers, & views of the program.  I felt that this lab was a good exercise to help me with this.

The first thing we had to do was to write an artist_name= & artist_name  so that the artist name could be retrieved & associated to in the Song instance. 
```
def artist_name
    self.artist.name
  end

  def artist_name=(name)
    self.artist = Artist.find_or_create_by(name: name)
  end
```
We then had to move on to create the helper method in ArtistsHelper Module. The goal was to have a method that the views would call on. The method needed to take into consideration whether or not the artist name was associated with the song yet or not.
If the song had an artist name, we needed to link it to the artist's show page, if not, we needed to link it to the song's edit page to add the artist.  I had to google around quite a bit to figure this out. I tried several things and finally found that either .present? or !.blank would work. 
```
def display_artist(song)
    if song.artist.present?
      link_to song.artist_name, artist_path(song.artist)
    else
      link_to "Add Artist", edit_song_path(song)
    end
  end
```
Once I finished this, I felt that the rest of the lab was easier. All I had to do was to use the helper method in the view pages for songs/show & songs/index pages.

songs/show:
```
<h1><%= link_to @song.title, song_path(@song) %></h1>
<h3><%= display_artist @song %></h3>

<%= link_to "All Songs", songs_path %>
```
songs/index:
```
<ul>
<% @songs.each do |song| %>
  <li><%= link_to song.title, song_path(song) %></li>
  <%= display_artist(song) %>
<% end %>
</ul>
<br>
<%= link_to "Add New Song", new_song_path %>

```
Once I finished these two methods, all of my tests passed. I was really glad to get through the lab.   I know I need a lot of practice to really get a handle on Rails, but I feel that I have a better understanding of  how helper methods work & how the different parts of the program fit together. 
