---
layout: post
title: Let's Learn C++ - Next steps PartII
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

###Database Project

In this project, we create a fully functional C++ program that implements a simple database application. 

Our program will allow us to manage a database od composers and relevant information about them. The features of the program include:

- The ability to add a new composer
- The ability to rank a composer (i.e. indicate how much we like or dislike the composer's music)
- The ability to view all the composers in the database
- The ability to view all composers by rank

> "There are two ways of constructing a software design : One way is to make it so simple that there are obniously no deficiencies, and the other way is to make it so complicated that there are no obvious deficiencies. The first method is far more difficult." - [C.A.R. Hoare](http://en.wikipedia.org/wiki/Tony_Hoare)


Many of us learned to design and code using a **"procedural"** approach. The central question we begin with is **"What must the program do?"**. 

- We decompose the solution to a problem into tasks, each of which solves a part of the problem. 
- These tasks map to functions in our program which are called sequentially from main() or from other functions. - - This step-by-step approach is ideal for some problems we need to solve. But more often than not, our programs are not just linear sequences of tasks or events.

With an **object-oriented (OO)** approach, we start with the question **"What real-world objects am I modeling?"** 

- Instead of dividing a program into tasks as described above, we divide it into models of physical objects. 
- These physical objects have a state defined by a set of attributes, and a set of behaviors or actions that they can perform. 
- The actions might change the state of the object, or they might invoke actions of other objects. 
- The basic premise is that an object "knows" how to do things by itself. 

In OO design, we define physical objects in terms of classes and objects; attributes and behaviors. There are generally a large number of objects in an OO program. Many of these objects, however, are essentially the same. Consider the following.
![]({{ site.url }}/images/oo.png)