---
layout: post
title:      " Is too much ever enough in Javascript?"
date:       2020-09-24 14:41:28 -0400
permalink:  is_too_much_is_never_enough_in_javascript
---


Designing a single page application with JavaScript can get very detailed. And trying to make every detail ideal might be more work than bargained for. So when do we put on the brakes? When do we tell ourselves "ok, this is fine, and it'll have to do"?

Asking myself this during my first project was pretty easy, but I bet when people become obsessed with perfection, they can lose sight of purpose. Knowing well that this project was more of a test-piece to play with and debug, first of all, it wasn't going to have every bell and whistle that I could dream up. And secondly, it wasn't as though I was tasked with dreaming up the next great algorithm.

This project uses simple AJAX via fetch calls to a Rails API, which consists of a couple models and a join table. The JS isn't wild and has just a couple listening events (either clicks or submits, nothing fancy) to give a very one dimensional experience of organizing a wine cellar. The logic used isn't complex, and mostly involves making changes to nodes by following streamlined data.

The purpose in most any project is ultimately to communicate back to whoever gave you the task that you can do what they ask for, and get it done, even if it isn't the prettiest. In the realworld, that's the client. They may not need an explanation of how it works--but it will be on you when they come crying cause things aren't acting perfect or aren't pretty enough. 

So then, when is the project nominal enough to say "I can present this to a user without worry that they'll catch a bug on the most trivial of programming logic?"

My opinion from this project is: when the user can obtain from the program what they desire without complete interruption. Minor glitches may feel imperceptible, but so long as they don't destroy the ultimate functionality, their futher debugging process can be sidelined for the next version release. 

So until then, its time push forward in understanding JS and find better ways to make my project goals happen.


