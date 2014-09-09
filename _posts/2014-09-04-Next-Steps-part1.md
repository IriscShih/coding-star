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

----------------------------------------------
{% highlight c++%}
In case you are a little rusty on physics, here are the calculations:

Velocity = 200.0; // initial velocity of 200 ft/sec
Gravity = 32.2; // gravity for distance calculation

// in_angle is the angle the player has entered, converted to radians.
time_in_air = (2.0 * Velocity * sin(in_angle)) / Gravity;
distance = round((Velocity * cos(in_angle)) * time_in_air);
{% endhighlight %}
----------------------------------------------

Because of the calls to cos() and sin(), you will need to include math.h.

Try writing this program - it's great practice in problem decomposition and a good review of basic C++. Remember to only do one task in each function. This is the most sophisticated program we have written thus far, so it may take you a little time to do it. 

[Click Here]() to see the solution.


####Example #2: Practice with Pointers

There are four things to remember when working with pointers:

1. Pointers are variables that hold memory addresses. 
    * As a program is executing, all variables are stored in memory, each at its own unique address or location. 
    * A pointer is a special type of variable that contains a memory address rather than a data value. 
    * Just as data is modified when a normal variable is used, the value of the address stored in a pointer is modified as a pointer variable is manipulated. 
    * Here's an example:
    
    {% highlight c++%}
    int *intptr; // Declare a pointer that holds the address of a memory location that can store an integer. Note the use of * to                   // indicate this is a pointer variable.
    intptr = new int; // Allocate memory for the integer.
    *intptr = 5; // Store 5 in the memory address stored in intptr.
    {% endhighlight %}
    
2. We usually say that a pointer **"points"** to the location it is storing (the "pointee"). So in the example above, intptr points to the pointee 5.

     

    

    


 

