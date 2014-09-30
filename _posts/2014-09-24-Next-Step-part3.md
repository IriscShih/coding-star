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

An open source build tool called **make** is commonly used. To learn about it, read through this **[short toturial](https://sites.google.com/site/michaelsafyan/software-engineering/how-to-write-a-makefile)**. </br>
See if you can create a dependency graph for the **Composer Database** application, and then translate into a makefile. [Here]() is my solution!

###Configuration Management Systems 

The second tool used in industrial software engineering is **Configuration Management(CM)**. This is used to manage change. Let's say Bob and Susan are both tech writers and both are working on updates to a technical manual. During a meeting, their manager assigns them each a section of the same document to update.

The technical manual is stored on a computer that both Bob and Susan can access. Without any CM tool or process in place, a number of problems could arise. 

- One possible scenario is the computer storing the document might be set up so that Bob and Susan can not both work on the manual at the same time. This would slow them down considerably.
- A more dangerous situation arises when the storage computer does allow the document to be opened by both Bob and Susan at the same time. Here is what could happen:
    - Bob opens the document on his computer and works on his section.
    - Susan opens the document on her computer and works on her section.
    - Bob completes his changes and saves the document on the storage computer.
    - Susan completes her changes and saves the document on the storage computer.
<br>![]({{ site.url }}/images/CM.png)

This illustration shows the problem that can occur if there are no controls on the singel copy of the technical manual. When Susan saves her changes, she overwirtes those made by Bob.

And this is exactly the type of situation that a CM system can control. With a CM system, both Bob and Susan "Check out" their own copy of the technical manual and work on them. When Bob checks his changes back in, the system knows that Susan has her own copy checked out. When Susan checks in her copy, the system analyzes the changes that both Bob and Susan made and creates a new version that merges the two sets of changes together. 

**CM systems** have a number of features beyond managing concurrent changes as described above. Many systems store archives of all versions of a document, from the first time it was created. In the case of a technical manual, this can be very helpful when a user has an old version of the manual and is asking a tech writer questions. A CM system would allow the tech writer to access the old version and be able to see what the user is seeing.

**CM systems** are especially useful in controlling changes made to software. Such systems are called Software Configuration Management (SCM) systems. If you consider the huge number of individual source code files in a large software engineering organization and the huge number of engineers who must make changes to them, it's clear that an SCM system is critical.

###Software Configuration Management

SCM systems are based on a simple idea: the definitive copies of your files are kept in a central repository. People check out copies of files from the repository, work on those copies, and then check them back in when they are finished. SCM systems manage and track revisions by multiple people against a single master set. 

All SCM systems provide the following essential features:

- Concurrency Management
- Versioning
- Synchronization
- Let's look at each of these features in more detail.
