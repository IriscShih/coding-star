---
layout: post
title: Let's Learn C++ - Next steps
description: "Welcome to C++ learning session! :)"
headline: "Let's Fire up the Engines"
categories: C++
tags: 
  - blogging
  - c++
  - start
comments: false
mathjax: null
featured: true
published: true
david: false
iris: true
---

###Introduction to Programming and C++

C++ is an object-oriented programming language. 
...
Our focus in this module will be on using pointers, and getting started with objects.

###Learn by Example #2

Our focus in this module is on obtaining more practice with **decomposition**, understanding **pointers**, and getting started with **objects & classes**. 

Work through the following examples. Write the programs yourself when asked, or do the experiments. I can't emphasize enough, just keep this in mind that the key to becoming a good programmer is practice, practice, practice!

####Example #1: More Decomposition Practice

Consider the following output from a simple game:

        Welcome to Artillery.
        You are in the middle of a war and being charged by thousands of enemies.
        You have one cannon, which you can shoot at any angle.
        You only have 10 cannonballs for this target..
        Let's begin...

        The enemy is 507 feet away!!!
        What angle? 25<
        You over shot by 445
        What angle? 15
        You over shot by 114
        What angle? 10
        You under shot by 82
        What angle? 12
        You under shot by 2
        What angle? 12.01
        You hit him!!!
        It took you 4 shots.
        You have killed 1 enemy.
        I see another one, are you ready? (Y/N) n

        You killed 1 of the enemy.
        
The Fire procedure handles the pkaying of the game. In that function, we call a random number generator to get the enemy distance, and then set up the loop to get the player's input and calculate whether or not they have hit the enemy. The guard condition on the loop is how close we hvae gotten to hit the enemy.

        In case you are a little rusty on physics, here are the calculations:

        Velocity = 200.0; // initial velocity of 200 ft/sec
        Gravity = 32.2; // gravity for distance calculation

        // in_angle is the angle the player has entered, converted to radians.
        time_in_air = (2.0 * Velocity * sin(in_angle)) / Gravity;
        distance = round((Velocity * cos(in_angle)) * time_in_air);
        
Because of the calls to cos() and sin(), you will need to include math.h.

Try writing this program - it's great practice in problem decomposition and a good review of basic C++. Remember to only do one task in each function. This is the most sophisticated program we have written thus far, so it may take you a little time to do it. 

[Click Here]() to see the solution.