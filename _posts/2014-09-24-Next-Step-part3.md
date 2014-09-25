---
layout: post
title: Let's Learn C++ - Next steps PartIII
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

##Welcome to the Real World!

In this module, we introduce two very important tools used most software engineering organizations. The first is a **build tool**, and the second is a **configuration management system**. Both of these tools are essential in inustrail software engineering, where many engineers often work on one large system. These tools help to coordinate and control changes to the code base, and provide an efficient means for compiling and linking a system from many program and header files. 

###Makefiles

The process of building a program is usually managed with a **build tool**, which **complies** and **links** the required files, in the correct order. Quite often C++ files have dependencies, for example, a function called in one program resides in another program. Or, perhaps a header file is needed by changes since the last build. This can save a lot of time in systems consisting of several hundreds or thounsands of files. 

An open source build tool called **make** is commonly used. To learn about it, read through this **[short toturial](https://sites.google.com/site/michaelsafyan/software-engineering/how-to-write-a-makefile)**.</br>
See if you can create a dependency graph for the **Composer Database** application, and then translate into a makefile. [Here]() is my solution!

