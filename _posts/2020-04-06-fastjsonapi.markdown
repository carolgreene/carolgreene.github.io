---
layout: post
title:      "FastJsonapi"
date:       2020-04-07 00:19:58 +0000
permalink:  fastjsonapi
---


In order to use JavaScript for the frontend of my latest Rails project, I needed to add a serializer to it. Serialization is the process of turning data Structures into a format that can be transmitted over the network. I would be turning my data into JSON. During my time at Flatiron, I've used 2 different serializers, ActiveModel & FastJsonapi. Both of them do a good job of serializing the data, but as the name implies, FastJsonapi does it a lot faster. I also like the way it breaks down the data, so  I decided to go with the FastJsonapi.

The first thing I had to do to set it up was to add the gem in my gemfile and run bundle install.
```
gem 'fast_jsonapi'
```
This gave me access to the serializer generator so I could add the serializer for my models by running:

rails g serializer show
rails g serializer user

This created the following serializer classes for me and I added the attributes.
```
class ShowSerializer
  include FastJsonapi::ObjectSerializer
  attributes :name, :genre, :summary
end
```
```
class UserSerializer
  include FastJsonapi::ObjectSerializer
  attributes  :email, :password_digest 
end
```
Now I just had to adjust the controller so it would use the serializer to process the data.

```
def index 
    shows = Show.all
    render json: ShowSerializer.new(shows)
  end
```
```
def index 
    users = User.all 
    render json: UserSerializer.new(users) 
  end
```
Here is how the data looked for one of my shows:
```
{
data: [
{
id: "1",
type: "show",
attributes: {
name: "Breaking Bad",
genre: "drama",
summary: "High school chemistry teacher gets cancer and ends up making meth because he needs money for his treatment."
}
},
```
I adjusted the rest of the controller methods to use the serializers and I was all set.
I was ready to move to my frontend and fetch my data from the backend. The serializer made it go through the network perfectly and it was ready for me to manipulate it how ever I wanted.





