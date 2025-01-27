---
layout: default
permalink: module/4
---

# Module 4: Introduction to Pointers in C++

* First read this page then start coding module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/-MH-w9cd](https://classroom.github.com/a/-MH-w9cd)


## Overview of Pointers  

Pointers are variables that store the memory address of another variable. They are powerful but require careful handling. In this module, we’ll cover:  
1. Declaring and initializing pointers.  
2. Dereferencing pointers to access or modify the value they point to.  

---

## Exercise 1: 
### Pointer Declaration and Dereferencing  

The code for this exercise is in the `exercise1` directory in the module4 repository. Complete the program in `pointer_basics.cpp` to practice declaring and dereferencing pointers.  

 
1. Declare an integer variable and assign it a value (e.g., `int x = 42;`).  
2. Declare a pointer and initialize it with the address of the integer variable (e.g., `int* ptr = &x;`).  
3. Print the value of the variable using both:  
   - The variable itself.  
   - The pointer (by dereferencing it).  
4. Modify the value of the variable using the pointer, and print the updated value.  

When you finish the exercise, write in the README.md file:  
- How pointers are declared and initialized.  
- What happens when you dereference a pointer.  

Example output:  

```Shell  
Value of x: 42  
Value of x (via pointer): 42  
Memory address of x: 0x7ffee4bce978  
Updated value of x (via pointer): 99  
```  


---

## Exercise 2:  
### Multiple Pointers and Null Pointers  

The code for this exercise is in the `exercise2` directory in the module4 repository. Complete the program in `multi_pointers.cpp` to explore working with multiple pointers and null pointers.  


1. Declare two integer variables with different values (e.g., `int a = 10, b = 20;`).  
2. Declare two pointers, and initialize each to point to one of the integers.  
3. Print the values of both integers using the pointers.  
4. Set one pointer to `nullptr`.  
5. Attempt to dereference the `nullptr` (comment out this line after testing to avoid runtime errors).  

When you finish the exercise, write in the README.md file:   
- What happens if you attempt to dereference a `nullptr`.  

Example output:  

```Shell  
Value of a (via pointer): 10  
Value of b (via pointer): 20  
Setting one pointer to nullptr.  
Attempting to dereference a nullptr.
```  


---


