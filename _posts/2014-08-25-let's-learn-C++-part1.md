---
layout: post
title: Let's Learn C++ - Getting Start PartI
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

## Learn by Example

One of the best ways to learn how to program in a new language is by looking at lots and lots of example programs. The best thing to do is to copy and paste each program below into a text file and compile it. Then, try the experiments. By extending these example programs, you will gain familiarity with different aspects fo C++, and you will feel more confident when it comes time to write programs from scratch.

### Example 1 : Get Compiler Working

First of all, let's have a look at the tutorial of the instructions on compiling, [Setting up to compile c++](http://www.arachnoid.com/cpptutor/setup_unix.html), for getting start with programming in c++.

Before start with the examples, there are few things to notice regarding readibility. This refers to comments and formatting that help make programs easy to read, understand, and maintain.

- Every program we write begins with a **header comment** : providing name of the author, their contact information, a short description, and usage(if relevant).
- Add **explanatory comments**(using full sentences) : whenever the code does not document itself. (i.e. if the processing is tricky, non-obvious, interesting, or important.)
- Always use **descriptive names** : 
    - Variables are lower-case words separated by _, as in my_variable. 
    - Function names use upper-case letters to mark words, as in MyExcitingFunction(). 
    - Constants start with a "k" and use upper-case letters to mark words, as in kDaysInWeek.



Okay, let's try the following classic program to see whether your compiler works or not!

{% highlight c++ %}
// hello.cpp: Iris Shih
// Description: a program that prints the immortal saying "hello world"

#include <iostream>
using namespace std;

int main() {
 cout << "Hello World!" << endl;
 return 0;
}

{% endhighlight %}


The most important thing is to make sure you can compile and run this program. Then, we can try some more interesting experiments:

- Modify the above program to print out "Hello World!" 4 times on a line for 6 lines, where each is printed in a field of 17 spaes. (By using **for-loops** to do this.)
    - [Click here](http://www.cplusplus.com/reference/ostream/ostream/) to learn about formatting output with cout.
    - [Click here]() to see the solution. :)
- Using the program you just completed, figure out how to print out "Hello World!" left-aligned in the field of 17 spaces.(The default is usually right-aligned)
    - [Click here]() to see the solution.


### Example 2 : Try some Input

It's easy to get input from the keyboard in C++ using cin. Here is an example:

{% highlight c++ %}

// get_input.cpp: Iris Shih
// Description: Illustrate the use of cin to get input.

#include <iostream>
using namespace std;

int main() {
 int input_var = 0;
 
 // Enter the do while loop and stay there until either a non-numeric is entered, 
 // or -1 is entered. Note that cin will accept any integer, 4, 40, 400, etc.
 do {
 cout << "Enter a number (-1 = quit): ";
 
 // The following line accepts input from the keyboard into variable input_var.
 // cin returns false if an input operation fails, that is, if
 // something other than an int (the type of input_var) is entered.
 if (!(cin >> input_var)) {
 cout << "You entered a non-numeric. Exiting..." << endl;
 break;
 // exit the do while loop
 }
 if (input_var != -1) {
 cout << "You entered " << input_var << endl;
 }
 } while (input_var != -1);
 cout << "All done." << endl;
 return 0;
}

{% endhighlight %}

An experiment:

- When an input error is made, the stream "breaks," cin returns false, and the program stops. It's very important to guard against such errors as we did in the program above. 
- But what if we want to recover from the error, rather than have the program stop? There are two steps to recovering from an error:
    1. Clear the error with cin.clear().
    2. Remove the incorrect characters from the stream. One way to do this is with cin.ignore().


### Example 3 : What is the Output?

{% highlight c++%}
#include <iostream>
using namespace std;

int main (void) {
 cout << " 1\t2\t3\t4\t5\t6\t7\t8\t9" << endl << "" << endl;
 for (int c = 1; c < 10; c++) {
   cout << c << "| ";
   for (int i = 1; i < 10; i++) {
     cout << i * c << '\t';
   }
   cout << endl;
 }
 return 0;
} 
{% endhighlight %}

### Example 4 : Decomposing makes everything easier... ;)

It's time for having some fun! Let's try to write a computer game. This first one will be a bit simple, but it's a start. 

Our task is to write a program that implements a guessing game. 

- It generates a random number between 0 to 100. 
- The player must guess the secret numnber. 
- The program provides hints like "that's too high" or "that's too low" until the player finally guesses the secret number. 
    
We will work on this game in 3 steps:

1. Figure out how to generate a random number within a given range of values.
2. Create a main function that processes one guess from the player, and provides hints.
3. Add what we need to allow for multiple guesses until the player guesses the number.

This process of development is called **decomposition**, which means breaking a task into sub-tasks, each of which is easy to do.

####Step 1 : Do a Google search to see how generate a random number using C++. Try searching on "rand C++".
You can check out the solution below.


{% highlight c++ %}
// random.cpp.  Iris Shih
// Description: Illustrates how to generate a random number in C++

#include <iostream>
#include <time.h>
using namespace std;

int main () {
  int random_number;

  // Initialize random seed.
  srand (time(NULL));

  // Generate random number between 1 and 100
  random_number = rand() % 100 + 1;

  cout << "Your random number:" << random_number << endl;
}
{% endhighlight %}

####Step 2 : We need to receive an integer input from the player (with appropriate error-checking on cin), and check it against the secret number. 

Try and write this part of the game yourself before checking the solution below! :)


{% highlight c++ %}
// guess.cpp.  Iris Shih
// Description: A guessing game where the player guesses the secret number.

#include <iostream>
#include <time.h>
using namespace std;

int main () {
  int random_number, guess;

  // Initialize random seed.
  srand (time(NULL));

  // Generate random number between 1 and 100
  random_number = rand() % 100 + 1;

  cout << "Guess our number (1 to 100) ";
  if (!(cin >> guess)) {
    cout << "Please enter only numbers" << endl;
  } else {
    if (random_number < guess) cout << "The secret number is lower than " << guess << endl;
    else if (random_number > guess) cout << "The secret number is higher than" << guess << endl;
    else cout << "You guessed it: " << random_number << endl;
  }
  cout << "random: " << random_number << endl;
  return 0;
}
{% endhighlight %}


####Step 3 : Add a loop that keeps collecting guesses from the player until they finally guess the secret number. 

After completing this part of the program, you can check out the solution below. ;)

{% highlight c++ %}
// guess.cpp.  Iris Shih
// Description: A guessing game where the player guesses the secret number.

#include <iostream>
#include <time.h>
#include <cstdlib.h>
using namespace std;

int main () {
  int random_number, guess;

  // Initialize random seed.
  srand (time(NULL));

  // Generate random number between 1 and 100
  random_number = rand() % 100 + 1;

  cout << "Guess our number (1 to 100) ";
  do {
    if (!(cin >> guess)) {
      cout << "Please enter only numbers" << endl;
    } else {
      if (random_number < guess) cout << "The secret number is lower than " << guess << endl;
      else if (random_number > guess) cout << "The secret number is higher than " << guess << endl;
    }
  } while (random_number != guess);
  cout << "Congratulations!" <<  endl;
  return 0;
}
{% endhighlight %}

**Decomposition** is one of the most important skills for a programmer to learn. Being able to break a task down into manageable pieces, and then complete one at a time is critical, no matter how big or how small the project. Here are some other opportunities for you to practice decomposition.

- The **greatest common divisor** of two integers is the largest number that divides them both evenly. 
    - For example, gcd(12, 18) = 6, gcd(−4, 14) = 2. 
    - The most efficient way to compute gcd is with the **Euclidean algorithm**. 
    - Write a program with a function to compute gcd for two integers. Try doing the function without recursion first - it will help you understand how the algorithm works.
    - [Click here]() to see the solution                                                                                                            