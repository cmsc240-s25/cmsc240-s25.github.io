---
layout: default  
permalink: module/16  
---

# Module 16: C++ Copy and Move Semantics

* First read this page, then start the module with the GitHub classroom link below.  
* Github Classroom Link: [https://classroom.github.com/a/Sn7O18nH](https://classroom.github.com/a/Sn7O18nH)  

---

## Learning Objectives:
- Understand the difference between copy and move semantics in C++.
- Learn how to define and use copy constructors, copy assignment operators, move constructors, and move assignment operators.
- Understand the impact of these semantics on performance and memory management.

---

## Exercise 1: Implementing Copy Constructor

Learn how copy constructors work and when they are invoked.

1. In the `exercise1` folder of your GitHub repository, edit the file `Box.cpp` and implement a copy constructor in the class `Box` with:
   - A copy constructor that performs a deep copy.
2. Review the code in the file `main.cpp`.
3. Run make.
4. Execute the program `main`.
5. Copy the output into the `README.md` file and give a brief explanation as to what happened.  


---

## Exercise 2: Copy Assignment Operator

Understand how to implement the copy assignment operator.

1. In the `exercise2` folder of your GitHub repository, edit the file `Box.cpp` and implement the copy assignment operator for the `Box` class:
   - Ensure that existing resources are cleaned up before performing a deep copy.
   - Handle self-assignment correctly.
2. Review the code in the file `main.cpp`.
3. Run make.
4. Execute the program `main`.
5. Copy the output into the `README.md` file and give a brief explanation as to what happened.  

---

## Exercise 3: Understanding Move Constructor

Explore how move constructors allow efficient resource transfer.

1. In the `exercise3` folder of your GitHub repository, edit the file `Box.cpp` and implement a move constructor to the `Box` class:
   - Transfer ownership of the dynamically allocated `int` from the source object to the target object.
   - Set the source object's pointer to `nullptr`.
2. Review the code in the file `main.cpp`.
3. Run make.
4. Execute the program `main`.
5. Copy the output into the `README.md` file and give a brief explanation as to what happened.  

---

## Exercise 4: Move Assignment Operator

Explore the move assignment operator and resource transfer.

1. In the `exercise4` folder of your GitHub repository, edit the file `Box.cpp` and implement a move assignment operator to the `Box` class:
   - Release any existing resources of the target object.
   - Transfer ownership of resources from the source object.
   - Leave the source object in a valid state.
2. Review the code in the file `main.cpp`.
3. Run make.
4. Execute the program `main`.
5. Copy the output into the `README.md` file and give a brief explanation as to what happened.  

---

