---
date: 2025-09-11T21:53
tags: []
---


### Partial Object Oriented Language

It is language that support Object Oriented programming Principle and also allow for non-object-oriented programming style/ programming construct such as using functions outside classes or having primitive types that are not objects..

Meanwhile

### Complete Object Oriented Language

A complete (or pure) object-oriented (OOP) language requires everything to be an object, including primitive data types..


For Example C++, java, python, scala, Ruby, etc....

## Why C++ is Partial Object Oriented Language

Just like a normal Object Oriented Language have essential feature like **Inheritance**, **Polymorphism** and **Encapsulation**. **But C++ some reasons:**

1. Main Function Outside the Class: In **C++**, you can use Functions, with Class, or Variable. So, here creation of class becomes **optional** and we can write code without using class.
```c++
#include <bits/stdc++.h>

using namespace std;

int main()

{
    cout << "Hello World";
    return 0;

}
```

2. **Concept of Global variable :** We can declare a variable globally, which can be accessible from anywhere and hence, it does not provides complete privacy to the data as no one can be restricted to access and modify those data and so, it provides encapsulation partially..

3. **Availability of Friend function:** A class can access private and protected members of other class in which it is declared as friend.
