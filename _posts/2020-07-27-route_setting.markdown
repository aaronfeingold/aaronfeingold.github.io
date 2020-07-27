---
layout: post
title:      "Route Setting"
date:       2020-07-27 01:39:05 -0400
permalink:  route_setting
---


> "Routes rate me, not the other way around." — Andy Cairns

Working with Restful routing and CRUD with Sinatra and Active Record has been challenging for me. Enough so, I actually had one of those moments of "maybe I *am* in over my head"--which means it was worth learning. There was the feeling of: once a problem had been solved, another was then created. Which, I find, has much to do with symmetry or proportionality of change.

I have a couple tips here pertaining to this concept of editing a project. And--if you'd like to read on--about a few situations in building a simple Ruby application that I came accross, and how to fix. First, my advice:

Fiddle with it. Its like when you begin to learn the guitar and you want to immediately play like your hero. You have to fiddle with things and see what random variations look and sound like. And in so doing, that is where you develop your own style. See, I was eventually able to predict the effects of one change, and track how that would play out. I slowly began to understand how routing worked, how information moved between controllers, models, and views. The routes challenged me to be precise and alert, and I approached them through piecemeal changes. With my two-steps-forward-one-step-back approach, it took a lot longer than I had expected to complete the work. Yet, it revealed many 'ah-ha' moments. Although the app is ultimately far from what I had hoped it would be, it is still satisfying seeing that it functions as intended. So fiddle with things until you find your style.

Second, as more of a general tip, get at least 1 or two dry erase boards that you can put on and take off a wall. Silly tip, right? But for me, it really helped to visual the conscruction of the project, and map out the scope of how the databases will relate to one another. 

Third, be able to mess with the 'binding.pry'. Its so interesting when you can see how the data is being funneled from one form when submited, and access those params. Here is an example of where to use it with a common code form for making a new user:

```
post '/signup' do
    # binding.pry
    @user = User.new(params[:user])
    if @user.save
      session[:user_id] = @user.id
      redirect '/cocktails'
    else
      flash.now[:error] = @user.errors.full_messages
      erb :'users/new'
    end
```

The better you can understand how this info is coming in, the better you can also enhance user experience. 

Lastly, the biggest take-away from the experience is that: the process of creating a user database depends on the real-world model it represent. The world that my project attempts to simulate is the bartendering world, where service is not something you can always streamline. Sure, you can set everything for the ideal situation. Yet, you have to be able to respond to changing circumstances, and adapt your product to fit the atmosphere. It is very often an ebb-and-flow cycle when it comes to making a cocktail--you can make a hip product one week, and next week its already old news. With this in mind, I sought to design the app with same sort of feel that I would've applied to making a cocktail--not taking leaps, but a few steps forward, and then a slight step back, and repeat.
