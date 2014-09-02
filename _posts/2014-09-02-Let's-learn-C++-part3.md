---
layout: post
title: Let's Learn C++ - Try More Exercises
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

The following exercises will give you more practice with basic C++. The solutions will be provided in the next post of Let's Learn C++ session. :)


###Exercise 1
The common field cricket chirps in direct proportion to the current temperature. Adding 40 to the number of time a cricket chirps in a minute, then dividing that value by 4 gives us the temperature. Write a program that takes as input the number of chirps in a minute and prints the current temperature. For example,

        Number of chirps: 120 
        The temperature is: 40.0 degrees.


###Exercise 2
Write a program that will compute your final grade for a programming course you are taking. Here is the grading scheme:

        Final grades will be based on the following:
        40% Assignments   15% Midterm Examination 
        35% Final Examination <br>
        10% Class Participation Grade 

* Your program should ask the user for the four assignment scores, the midterm, final and section grades. 
* Then, the final score is calculated and printed. 
    - To do the calculations, you average the four assignment scores together and then multiply it by 0.4 (40%). 
    - Then multiply the midterm score by 0.15, the final by 0.35 and the participation grade by 0.1. 
    -   Then you add all the results of these multiplications together.

Use functions wherever you can in this program. You can create a function to get the input by passing in as a parameter the string to be displayed in an explanatory cout. Here is an example run:

        Enter the score for the first assignment. 75
        Enter the score for the second assignment. 85
        Enter the score for the third assignment. 82
        Enter the score for the fourth assignment. 94
        Enter the score for the midterm. 81
        Enter the score for the final. 89
        Enter the score for the section grade. 100
        The final grade is: 86.9


###Exercise 3
As electronic stopwatches become cheaper and more accurate, we will no doubt be deluged with impossibly accurate measurements of time. Write a program that takes as input a time period given in seconds, and outputs the number of hours, minutes and seconds it represents. For example,

        Number of seconds: 3662
        Hours: 1
        Minutes: 1
        Seconds: 2 

**In the following, do decomposition prior to writing your program.**<br>
**Use functions wherever possible to create well-structured programs.**


###Exercise 4
Suppose we wanted to print a banner for the following:<br>
**"FREEZY BREEZE MAKES THREE TREES FREEZE"**

We want the letters to be pretty big since this is a banner:

        FFFFF
        F
        FFF
        F
        F

        EEEEE
        E
        EEE
        E
        EEEEE
        
etc.
Being a good problem decomposer, you probably noticed that rather than put all the cout's in the main function, it would be far more efficient to put them in functions. So we could have a "printE" function and a "printZ" function and so on.

Write a program with functions that creates a banner of a word or phrase with lots of repeated letters. Some possibilities:

        FREEZY BREEZE MAKES FLEAS
        SNEEZE TWEETLE BEETLE PADDLE BATTLE
        SIX SICK CHICKS KICK
        SUE SEWS SUE'S SOCKS
        BEN BENDS BIM'S BROOM 


###Exercise 5
Here is a "magic number" problem: **Ask a user to enter a three-digit number whose first digit is greater than its last.** <br>

* Your program will reverse the number, and subtract the reversal from the original number. 
* Finally, reverse the resulting number, and add it to its unreversed form. 
* Output the final result. The original number that the user enters must be of integer type (not three chars). 

Think about how to write a function that takes an integer as input and returns the reverse of that number. Example:

        input number: 901
        reverse it: 109
        subtract: 901 - 109 = 792
        reverse it: 297
        add: 297 + 792 = 1089 
 
 
###Exercise 6
The law requires that food product manufacturers place expiration dates on their products, but there is a loophole in the law: it does not require the expiration date to be in any particular form. So, it can be written in Swahili and still be legal.
Ralph Nader's third cousin, Nadine is a self-appointed Food Quality Spy. She has learned that many food product manufacturers have started encoding the product expiration dates to keep customers from knowing how old the stuff is.

But the encoding does allow grocers to figure out the expiration dates if for some reason, they want to.

One popular encoding method:

    - encode the months from Jan to Dec as 'A' through 'L'
    - encode each digit of the date as 'Q' through 'Z'
    - encode the year as 'A' through 'Z' meaning 1 through 26 which is then added to 1995.
    
Nadine found a particularly questionable loaf of bread with this date: ARZM. Write a program to determine the date.


###Exercise 7
This is a number analogy to a famous card trick. Ask the user to enter a three-digit number. 

* Think of the number as ABC (where A, B, C are the three digits of the number). 
* Now, find the remainders of the numbers formed by ABC, BCA, and CAB when divided by 11. 
* We will call these remainders X, Y, Z. 
* Add them up as X+Y, Y+Z, Z+X. 
* If any of the sums are odd, increase or decrease it by 11 (whichever operation results in a positive number less than 20; note if the sum is 9, just report this and stop the process). 
* Finally, divide each of the sums in half. The resulting digits are A, B, C. Write a program that implements this algorithm.


