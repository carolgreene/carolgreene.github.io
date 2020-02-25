---
layout: post
title:      "Will I remember Ruby?"
date:       2020-02-25 02:08:19 +0000
permalink:  will_i_remember_ruby
---


I was so excited when I finally graduated from the Software Engineering program. It took so long & I couldn't wait to be done. Once reality set in though, I realized that I needed to review everything to make sure that I had a good grasp of what I learned. I went back to the beginning Ruby section to look it over & was surprised at how much I'd forgotten. At that point I decided it would be fun to do a small CLI project to refresh my memory.

I settled on scraping the timeout website to get the best parks in Chicago. The first thing I realized was that I had no idea how to start a Ruby gem, I had completely forgotten! I did  a little research online & had it going in no time. 

Follow the steps below to set up a Ruby Gem:

Create the gem with bundler
*bundle gem "name of gem"*

Do you want tests?  Y or N
Do you want MIT License?  Y
Do you want Code of Conduct? Y

This will initialize the git repo

GO TO YOUR GITHUB REPOSITORY

Click New
Type in name of gem
Click create repository

IN TERMINAL

cd to your new file

type in: "git add ."      *enter*
                "git commit -m"first commit"     *enter*
								"git remote add origin "your git hub name/gem name.git"         *enter*
								"git push origin master"           *enter*
								
Now the gem is all set in GitHub.

IN BIN FILE
add file with the name of app

This next line tells the iterpreter tht everything after it will be in Ruby. I had trouble with this taking until I realized I needed to restart the app. Then the code after it changed from white to green.

#!/usr/bin/env ruby       

I entered in:  puts "Welcome"  so I could test it by running ./bin/"name of file"

I ended up getting an error message telling me "permission denied". With some research, I found that all I had to do was type in:

ls -lah to check the files. It showed that my ruby file was not executable. 

To fix that I just had to type in:  chmod +x"name of file"

Once that was done I ran ./bin/"name of file" and got "Welcome" back. I was ready to go!

Doing this little project sure went a ton faster than the first Ruby gem I did. By the time I finished it, everything had come back to me & I had another small project under my belt!



	
	




