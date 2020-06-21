---
layout: post
title:      "Miner Keys"
date:       2020-06-21 16:06:35 -0400
permalink:  miner_keys
---


>  Q: What chord does a piano play when it falls down a mine-shaft onto a worker? A: Ab minor


Pun intended. A bit of dark, musical humor for you instrumentalists reading...

The concept of utilizing an application programming interface (API) is much like digging into the earth, as a miner would. And what we 'shovel' into our arrays is not unlike depositing ore for future, practical use. Its really quite interesting to see how programming language has developed to replicate real world scenarios into intuitively, understandable analogies. 

But see, the closest I've ever been to mining was trying to dig a hole to China at the beach when I was like 5 years old. So, what anologies best fit my current knowledge base? How can I better cement these concepts into my brain?

Well, as a life-long musician, I have come to view the building of a command line interface (CLI) much like the construction of a work of music. It is the instrument that enables us to produce our opus, our ultimate creation. Through this first project, I have found that programming is not unlike writting music. Not only does it require its own language, but, also, its own unique tools. Let's see if you can follow where I'm going with this:

The BASE URL is more like this abstract place within your own mind where you formulate the idea of the music you'd like to express. There's all this info there, but no way to get it out, so we parse it out; cut it up into something we can interpret. Then enters the chords. The chords you play are like the instance and/or class methods, and the classes we create are like our verses and chorus. They bring to life the idea of music; like when we initialize attributes, we start with nothing and fill the void with something. We weave these classes together with our environment, which is like the band, all playing their parts together. And, in music theory, this would be "call-and-response", which is when a lead singer, for instance, sings "Go tell it on the mountain" and the rest of the band replies "on the mountain" like an echo that confirms that they not only heard it, but also understanding it as well.

The anology could go on and on and on. For the purpose of a blog, that would be superflous. It is sufficive to say that in the process of creating my Pokemon api, I was able to acheive something functional through long trial and error. Although, I was not able to create the full program I wanted to. Just like when you first learn an instrument, you don't just get on and start jamming. It is really sloppy and poorly edited. But, if the pedagogy is sound, it becomes possible to track your progression, and slowly but surely connect all the concepts together, and begin to recognize patterns. 

Here is a bit of code used in the API whose pattern I am now beginning to recognize all other the place:
```

  def self.get_pokemon_details
        Pokemon.all.each do |pokemon|
            info = RestClient.get(pokemon.url)
            data = JSON.parse(info)
            pokemon.abilities = data["abilities"].map { |hash| hash["ability"]["name"] } 
            pokemon.moves = data["moves"].map { |hash| hash["move"]["name"] }
            pokemon.types = data["types"].map { |hash| hash["type"]["name"] }
       end
  end
```

At first, this made little sense to me. But now I pretty much get how the data relates to one another.

My hope from this project is that I can replicate its structure for a concept I am more interested in. I'm not saying Pokemon isn't great...just saying that I would hope to create a program next time more along the lines of what I'm best at, which is playing music.






