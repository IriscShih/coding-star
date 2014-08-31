---
layout: post
title: Let's Learn C++ - Getting Start PartII
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

## Learn by Example - Part II

Welcome back, let's continue our learning and practicing session!


### Example 5 : Math Puzzles 

One of the powers of computing is being able to do a **brute-force** search for a solution to a problem.<br>
Trial and error works just fine for some problems. In fact, computers can be especially good at such problems.<br>

- **Consider this**: Horses cost $10, pigs cost $3, and rabbits are only $0.50. A farmer buys 100 animals for $100. How many of each animal did he buy?

There is a remarkably simple solution to this problem. See if you can find it before you look down for the solution. :)

----------------------------------------------
{% highlight c++ %}

// animal.cpp.  Iris Shih
// Description: Computes combinations of animals under constraints

#include <iostream>
using namespace std;

int main () {

  for (int h = 0; h < 100; h++)
    for (int p = 0; p < 100; p++)
      for (int r = 0; r < 100; r++)
        if ((h + p + r) == 100)
          if (((10 * h) + (3 * p) + (0.5 * r)) == 100)
            cout << "Found one! " << h << " horses " << p << " pigs " << r << " rabbits "  << endl;
}

{% endhighlight %}
----------------------------------------------

- Here comes another try : How many ways can you arrange 6 different books, left to right, on a shelf? (This time we will just give you the solution and let you write the program: 720.)


### Example 6 : Strings for your consideration 

What does the following program output?

-----------------------------------------------
{% highlight c++ %}
#include <iostream>
using namespace std;

int main (void) {
 string str1 = "To be or not to be, that is the question";
 string str2 = "only ";
 string str3 = str1.substr(6, 12);
 str1.insert(32, str2);
 str1.replace(str1.find("to be", 0), 5, "to jump");
 str1.erase(9, 4);
 cout << str1 << endl;
 for (int i = 0; i < str3.length(); i++)
 cout << str3[i]; cout << endl;
}
{% endhighlight %}
-------------------------------------------------

Need some help about **C++ String Class**, have a look [here](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++StringClass.html).


### Example 7 : Next steps with deconposition - Your first day on the job

You have just gotten a position as a salesperson for the ExerShoe company, specializing in high-end exercise shoes costing around $225 per pair.<br>
Your boss has given you three options for compensation, which you mush choose before you begin your first day : 

    1. Straight salary of $600 per week;
    2. A salary of $7.00 per hour plus a 10% commission on sales;
    3. No salary, but 20% commissions and $20 for each pair of shoes sold

You, being an expert C++ programmer, figure you can write a program to help decide the best choice of compensation.

- A common approach in doing decomposition for a larger program is to create a **main function** that reads like an outline to solve the problem. 
- Then, we write the functions to do each task


Here is a first pass at the **main** program:

>    GetInput(WeeklySales);<br>
     CalcMethod1(WeeklySales);<br>
     CalcMethod2(WeeklySales);<br>
     CalcMethod3(WeeklySales); 

Just have a try if you can implement each of these functions before checking out the solution. :)

----------------------------------------------
{% highlight c++ %}
// compensation.cpp, Iris Shih
// Description: A program to decide the best of three methods of compensation

#include <iostream>
using namespace std;

// constants which are used throughout the program
#define kPricePerUnit 225  // average price of a pair of shoes
#define kWeeklyWage 600    // current weekly wage - Method 1
#define kSalary 7.0        // hourly salary - Method 2
#define kHoursPerWeek 40    // number of hours worked - Method 2
#define kCommission2  0.10  // commission - Method 2
#define kCommission3 0.2    // commission - Method 3
#define kBonusPerUnit 20    // bonus  - Method 3

// A function to get the weekly sales of units
int GetInput() {
  int units;
  cout << "Enter number of units sold per week: ";
  if (!(cin >> units)) {
    cout << "Numbers only" << endl;
    return 0;
  } else {
    return units;
  }
}

// This one is easy - always the same: $600 per week
void CalcMethod1() {
  cout << "Method 1: " << kWeeklyWage << endl;
}

// Method 2: A salary of $7.00 per hour plus a 10% commission on sale
void CalcMethod2(int Sales) {
  double PerHour, TotalPay, Commission;

  PerHour = kSalary * kHoursPerWeek;
  Commission = (Sales * kPricePerUnit) * kCommission2;
  TotalPay = PerHour + Commission;
  cout << "Method 2: " << TotalPay << endl;
}

// Method 3: No salary, but 20% commissions and $20 for each pair of shoes sold
void CalcMethod3(int Sales) {
  int Extra;
  double TotalPay, Commission;

  Extra = kBonusPerUnit * Sales;
  Commission = (Sales * kPricePerUnit) * kCommission3;
  TotalPay = Extra + Commission;
  cout << "Method 3: " <<  TotalPay << endl;
}

int main() {
  int WeeklySales;    // our input variable

  WeeklySales = GetInput();
  if (WeeklySales == 0)
    return 0;
  CalcMethod1();
  CalcMethod2(WeeklySales);
  CalcMethod3(WeeklySales);
}
{% endhighlight %}
----------------------------------------------

### Example 8 : What is avaliable where?

What is the output of the following program?

----------------------------------------------
{% highlight c++ %}
// scope.cpp, Iris Shih
// Description: A program to illustrate different scopes

#include <iostream>
using namespace std;

int a = 18;
int b = 6;

int function1(int a, int b) {
 return a - b;
}

int function2() {
 int c;
 c = a + b;
 return c;
}

int main (void) {
 int b = 12;
 int c = 0;
 a = function1(b, a);
 c = function2();
 cout << "a: " << a << " b: " << b << " c: " << c << endl;
}
{% endhighlight %}
----------------------------------------------

Once you have figured out your answer, check the commented version of the code [here]().


### Example 9 : Processing Files

File processing in C++ is performed using **fstream**.<br>
To save to a file, we declare an **ofstream**, and open it using the **"out"** mode.

- Check this out in the following example:

----------------------------------------------
{% highlight c++ %}
// file.cpp, Iris Shih
// Description: An illustration of file processing
#include <fstream>
#include <iostream>
using namespace std;

int main() {
 char first_name[30], last_name[30]; int age;
 char file_name[20];
 // Collect the data.
 cout << "Enter First Name: "; cin >> first_name;
 cout << "Enter Last Name: "; cin >> last_name;
 cout << "Enter Age: "; cin >> age;
 cout << endl << "Enter the name of the file: "; cin >> file_name;

 // Create an ofstream called People, open the stream for output.
 ofstream People(file_name, ios::out);
 // Write the output to the stream.
 People << first_name << endl << last_name << endl << age << endl; return 0;
} 
{% endhighlight %}
----------------------------------------------

- Successfully create and open the file you just created? Let's see how to display your file!

----------------------------------------------
{% highlight c++ %}
// file.cpp, Iris Shih
// Description: An illustration of file processing
#include <fstream>
#include <iostream>
using namespace std;

int main() {
 char first_name[30], last_name[30]; int age;
 char file_name[20];
 // Collect the data.
 cout << "Enter First Name: "; cin >> first_name;
 cout << "Enter Last Name: "; cin >> last_name;
 cout << "Enter Age: "; cin >> age;
 cout << endl << "Enter the name of the file: "; cin >> file_name;

 // Create an ofstream called People, open the stream for output.
 ofstream People(file_name, ios::out);
 // Write the output to the stream.
 People << first_name << endl << last_name << endl << age << endl; return 0;
 // Close the stream.
  People.close();

  // Create an ifstream to read the file.
  ifstream People_in(file_name);
  People_in >> first_name >> last_name >> age;

  cout << endl << "First Name: " << first_name;
  cout << endl << "Last Name:  " << last_name;
  cout << endl << "Enter Age:  " << age;
  cout << endl;

  // Close the stream.
  People_in.close();

} 
{% endhighlight %}
----------------------------------------------

- Now see if you can modify this program to allow the user to enter many records of data using a loop. We also want to read back all the data, one record at a time. 
- [Click Here]() to see the solution!


Now, already some practices that takes you into the C++ programming world! Maybe something you would like to know, such as working life in Google as a software engineer?

> ###What it's like to be a software engineer at Google
>Read about what it's like to work at Google on [this website](http://www.google.com/about/careers/lifeatgoogle/)
