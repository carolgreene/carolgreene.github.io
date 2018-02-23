---
layout: post
title:      "Top Travel Deals-CLI Gem Project"
date:       2018-02-23 22:57:21 +0000
permalink:  top_travel_deals-cli_gem_project
---


I was really nervous about starting the CLI Gem Project so I watched all of the videos before starting. They were really helpful and I decided it was best to follow along with Avi's Daily Deal in order to get started.  The first thing I had to do was to create the repository on github.  I made the mistake of initializing it with a README so when I went to do my bundle gem in the IDE, it actually duplicated the files. I tried deleting the duplicates but they would reappear after I signed out and then back in again.  After getting help in a study group for the project, we finally got it straightened out and I was ready to go. This took way longer than I had expected and I couldn't wait to get started actually coding.

I decided that I wanted to do the project about something I was interested in. I love to travel and I like nothing better than a great deal so I decided to scrape the Top 20 Travel Deals list from Travel Zoo.  One of the best pieces of advice that Avi gave in the videos was to write the code you'd like to have and to hard code in information in order to get started on the easier parts.  That proved to be hugely helpful and I was able to pop in the easy code in my CLI & Deal classes and just hard code in the basic information that I would scrape later.  It helped me make sure my main ruby code was working and I got to see how my gem would (or would not) function!

I  moved on to the scraping and decided to just keep all of my code in the cli.rb class while I worked so I could see everything at once. I found this way easier and it helped me get a handle on how everything related to each other. I just moved the scraping methods to a separate class after I was finished. I did run into some problems scraping, initiallly getting too much information & then having trouble getting everything I needed within the same div so I could create my objects from it. This also took quite a bit longer than I expected but I learned a lot and also got a lot better at using pry!

Once I got my initial list to print, I set it up to have the user choose which trip they'd like to see more info on. It then takes the url of that page and scrapes off of that to get the detail summary.  It took me awhile to figure out exactly how to do this and I used Avi's suggestion of hardcoding in one of the trips url information to start with. I was then able to figure out what I needed to scrape and make sure everything printed correctly. Doing that helped me relax a little and I realized pretty quickly how to get the proper url's into that method.

After I completed the scraping portion I went back to the cli class to fine tune the flow. I did a lot of breaking the code and then fixing it and adjusting how it prints.  All in all, the project was actually a lot of fun to do and I learned a ton!  To anyone who's just starting it, watch all of the videos and don't be afraid to just jump in  and get started! 
