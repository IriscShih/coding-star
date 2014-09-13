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

* **1st** : Pointers are varables that hole memory address. 
    - As a program is executing, all variablrs are stored in memory, each at its own unique address or location.
    - A pointer is a special type of variable that contains a memory address rather than a data value. Just as data is modified when a normal variable is used, the value of the address stored in a pointer is modified as a pointer variable is manipulated. 
    - Here's an example:

----------------------------------------------
        {% highlight c++%}
                int *intptr; // Declare a pointer that holds the address
         // of a memory location that can store an integer.
         // Note the use of * to indicate this is a pointer variable.

        intptr = new int; // Allocate memory for the integer.
        *intptr = 5; // Store 5 in the memory address stored in intptr.
        {% endhighlight %}
----------------------------------------------
    
* **2nd** : We usually say that a pointer "points" to the location it is storing (the "pointee"). So in the example above, intptr points to the pointee 5.<br> ![](/images/point1.png)
    - Notice the use of the "new" operator to allocate memory for our integer pointee. This is something we must do before trying to access the pointee.
    
----------------------------------------------
        {% highlight c++%}
            int *ptr; // Declare integer pointer.
        ptr = new int; // Allocate some memory for the integer.
        *ptr = 5; // Dereference to initialize the pointee.
        *ptr = *ptr + 1; // We are dereferencing ptr in order
         // to add one to the value stored
         // at the ptr address.
        {% endhighlight %}
----------------------------------------------

The * operator is used for dereferencing in C. One of the most common errors C/C++ programmers make in working with pointers is **forgetting to initialize the pointee**. This can sometimes cause a runtime crash because we are accessing a location in memory that contains unknown data. If we try and modify this data, we can cause subtle memory corruption making it a hard bug to track down.

* **3rd** : Pointer assignment between two pointers makes them point to the same pointee. 
    - So the assignment y = x; makes y point to the same pointee as x. 
    - Pointer assignment does not touch the pointee. It just changes one pointer to have the same location as another pointer. 
    - After pointer assignment, the two pointers "share" the pointee. <br> ![](/images/point2.png)
    
----------------------------------------------
{% highlight c++%}
void main() {
 int* x; // Allocate the pointers x and y
 int* y; // (but not the pointees).

 x = new int; // Allocate an int pointee and set x to point to it.

 *x = 42; // Dereference x and store 42 in its pointee

 *y = 13; // CRASH -- y does not have a pointee yet

 y = x; // Pointer assignment sets y to point to x's pointee

 *y = 13; // Dereference y to store 13 in its (shared) pointee
}

{% endhighlight %}
----------------------------------------------

Here is a trace of this code:

* Allocate two pointers x and y. Allocating the pointers does not allocate any pointees. <br>![](/images/point3.png)
* Allocate a pointee and set x to point to it. <br>![](/images/point4.png)
* Dereference x to store 42 in its pointee. This is a basic example of the dereference operation. Start at x, follow the arrow over to access its pointee.<br>![](/images/point5.png)
* Try to dereference y to store 13 in its pointee. This crashes because y does not have a pointee -- it was never assigned one.<br>![](/images/point6.png)
* Assign y = x; so that y points to x's pointee. Now x and y point to the same pointee -- they are "sharing".<br>![](/images/point7.png)
* Try to dereference y to store 13 in its pointee. This time it works, because the previous assignment gave y a pointee.<br>![](/images/point8.png)

As you can see, pictures are very help in understanding pointer usage. Here is another example.

----------------------------------------------
{% highlight c++%}
int my_int = 46; // Declare a normal integer variable.
// Set it to equal 46.

// Declare a pointer and make it point to the variable my_int
// by using the address-of operator.
int *my_pointer = &my_int;

cout << my_int << endl; // Displays 46.

*my_pointer = 107; // Derefence and modify the variable.

cout << my_int << endl; // Displays 107.
cout << *my_pointer << endl; // Also 107.
{% endhighlight %}
----------------------------------------------

Notice in this example that we never allocated memory with the "new" operator. We declared a normal integer variable and manipulated it via pointers.

In the example below, we illustrate the use of the **delete operator** which de-allocates heap memory, and how we can allocate for more complex structures. We will cover memory organization (heap and runtime stack) in the another lesson. For now, just think of the heap as a free store of memory available to running programs.

----------------------------------------------
{% highlight c++%}
int *ptr1; // Declare a pointer to int.
ptr1 = new int; // Reserve storage and point to it.

float *ptr2 = new float; // Do it all in one statement.

delete ptr1; // Free the storage.
delete ptr2;
{% endhighlight %}
----------------------------------------------

In the final example below, we show how pointers are used to **pass values by reference** to a function. This is how we modify the values of variables within a function.

----------------------------------------------
{% highlight c++%}
// Passing parameters by reference.
#include <iostream>
using namespace std;

void Duplicate(int& a, int& b, int& c) {
 a *= 2;
 b *= 2;
 c *= 2;
}

int main () {
 int x = 1, y = 3, z = 7;
 Duplicate(x, y, z);
 // The following outputs: x=2, y=6, z=14.
 cout << c"x="<< x << ", y="<< y << ", z="<< z;
 return 0;
}
{% endhighlight %}
----------------------------------------------

If we were to leave the **&'s** off the arguments in the Duplicate function definition:

* Pass the variables "by value"
    - i.e., a copy is made of the variable. Any changes made to the variable in the function modify the copy. They do not modify the original variable.
* Pass the variable "by reference"
    - In this case, we are not passing a copy of its value, we are passing the address of the variable to the function. 
    - Any modificaton that we do to the local variable actually modifies the orginal variable passed in. 
<br>    
<br>

If you are a C programmer, this is a new twist. 

* We could do the same in C by 
    - declaring **Duplicate()** as **Duplicate(int *x)**, in which case x is a pointer to an int
    - then, calling **Duplicate()** with argument **&x** (address-of **x**)
    - and, using de-referencing of **x** within **Duplicate()** (see below). 

But C++ provides a simpler way of passing values to functions by reference, even though the old "C" way of doing it still works.

----------------------------------------------
{% highlight c++%}
void Duplicate(int *a, int *b, int *c) {
  *a *= 2;
  *b *= 2;
  *c *= 2;
}

int main () {
  int x = 1, y = 3, z = 7;
  Duplicate(&x, &y, &z);
  // The following outputs: x=2, y=6, z=14.
  cout << "x=" << x << ", y=" << y << ", z=" << z;
  return 0;
}
{% endhighlight %}
----------------------------------------------

Notice with C++ references, we do not need to pass the address of a variable, nor do we need to dereference the variable inside the called function.

What does the following program output? Try to draw a picture of memory to figure it out. :)

----------------------------------------------
{% highlight c++%}
void DoIt(int &foo, int goo);

int main() {
 int *foo, *goo;
 foo = new int;
 *foo = 1;
 goo = new int;
 *goo = 3;
 *foo = *goo + 3;
 foo = goo;
 *goo = 5;
 *foo = *goo + *foo;
 DoIt(*foo, *goo);
 cout << (*foo) << endl;
}

void DoIt(int &foo, int goo) {
 foo = goo + 3;
 goo = foo + 4;
 foo = goo + 3;
 goo = foo;
} 

{% endhighlight %}
----------------------------------------------

Run the program to see whether you got the correct answer or not! ;)