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

In OO design, we define physical objects in terms of classes and objects; attributes and behaviors. There are generally a large number of objects in an OO program. Many of these objects, however, are essentially the same. Consider the following.<br><br>![]({{ site.url }}/images/oo.png)

A class is a set of general attributes and behaviors for an object, which may exist physically in the real world. In the illustration above, we have an Apple class. All apples, regardless of their type, have color and taste attributes. We have also defined a behavior whereby the Apple display its attributes.<br>![]({{site.url}}/images/oo2.png)

In this diagram, we have defined 2 objects which are of the Apple class. Each object has the same attributes and actions as the class, but the object defines the attributes for a specific type of apple. In addition, the **Display** action as the class, but the object defines the attributes for a specifiv type of apple. In addition, the **Display** action displays the attributes for that particular object, e.g. "Green" and "Sour".

An OO design consists of a set of classes, the data associated with these classes, and the set of actions the classes can perform. Wealso need to identify the ways different classes interact. This interection can be performed bu objets of a class invoking the actions of objects of other classes. For example, we could have a **AppleOutputer** class that outputs the color and taste of an array of Apple objects, by calling the **Display()** method of each Apple object.

**Here are the steps we perform in doing OO design:**

1. Identify the classes, and define in general what an object of each class stores as data and what an object can do.
2. Define the data elements of each class
3. Define the actions of each class and how some actions of one class can be implemented using actions of other related classes. 

For a large system, these steps occur iteratively at different levels of detail.

We also need a collection of **Composer objects**. 
- For this, we define a Database class which manages the individual records.
- An object of this class can add or retrieve Composer objects, and display individual ones by invoking the display action of a Composer object

Finally, we need some kind of user interface to provide interactive operations on the database. this is placeholder class, i.e. we really don't know what the user interface is going to look like yet, but we do know we will need one. Maybe it will be graphical, maybe text-based. For now, we define a placeholder which we can fill in later.

###...NEXT

Now that we have identified the classed for the composer database application, the next step is to define the attributes and actions for classes in a more complex application, we would sit down with pencil and paper or [UML](http://en.wikipedia.org/wiki/Unified_Modeling_Language) or [CRC cards](http://en.wikipedia.org/wiki/Class-responsibility-collaboration_card) or [OOD](http://en.wikipedia.org/wiki/Object-oriented_design) to map out the class hierarchy and how the objects interact.

For our composer database, we define a **Composer class** which contains the relevant data we want to store on each composer. It also contains methods for manipulating ranking, and displaying the data. 

- **Database class** : It needs some kind of structure for holding **Composer objects**. We need to be able to add a new **Composer object** to the structure, as well as retrieve a specific **Composer object**. We'd also like to display all the objects either in order of entry, or by ranking.
- **User Interface class** : Implements a menu-driven interface, with handlers that call actions in the Database class. 

If the classes are easily understood and their attributes and actions clear, as in the composer application, it's relatively easy to design the classes. But if there are any questions in your mind as to how the classes relate and interact, it's best to draw it out first, and work through the details before starting to code.

Once we have a clear picture of the design and have evaluated it (more on this soon), we define the interface for each class. We don't worry about implementation details at this point - just what are the attributes and actions, and what parts of a class' state and actions are available to other classes.

In C++, we normally do this by defining a **header file** for each class. The **Composer class** has private data members for all the data we want to store on a composer. We need **accessors (“get” methods)** and **mutators (“set” methods)**, as well as the primary actions for the class.

----------------------------------------------
{% highlight c++%}
// composer.h, Iris Shih
// Description: The class for a Composer record.
// The default ranking is 10 which is the lowest possible.
// Notice we use const in C++ instead of #define.
const int kDefaultRanking = 10;

class Composer {
 public:
 // Constructor
 Composer();
 // Here is the destructor which has the same name as the class
 // and is preceded by ~. It is called when an object is destroyed
 // either by deletion, or when the object is on the stack and
 // the method ends.
 ~Composer();

 // Accessors and Mutators
 void set_first_name(string in_first_name);
 string first_name();
 void set_last_name(string in_last_name);
 string last_name();
 void set_composer_yob(int in_composer_yob);
 int composer_yob();
 void set_composer_genre(string in_composer_genre);
 string composer_genre();
 void set_ranking(int in_ranking);
 int ranking();
 void set_fact(string in_fact);
 string fact();

 // Methods
 // This method increases a composer's rank by increment.
 void Promote(int increment);
 // This method decreases a composer's rank by decrement.
 void Demote(int decrement);
 // This method displays all the attributes of a composer.
 void Display();

 private:
 string first_name_;
 string last_name_;
 int composer_yob_; // year of birth
 string composer_genre_; // baroque, classical, romantic, etc.
 string fact_;
 int ranking_;
};
{% endhighlight %}
----------------------------------------------