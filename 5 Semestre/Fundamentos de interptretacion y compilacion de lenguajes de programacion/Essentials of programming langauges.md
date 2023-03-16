# Notes from the book: *Essentials of Programming Languages*

# Contents
1. Inductive Sets of Data
    1. Recursively Specified Data
    2. Deriving Recursive Programs
    3. Auxiliary Procedures and Context Arguments
    4. Exercises
2. Data Abstraction
    1. Specifying Data via Interfaces
    2. Representation Strategies for Data Types
    3. Interfaes for Recursive Data Types
    4. A tool for Defining Recursive Data Types
    5. Abstract Syntax and Its Representation
3. Expresions
    1. Specification and Implementation Strategy
    2. LET: A Simple Language
    3. PROC: A Language with Procedures
    4. LETREC: A Language with Recursive Procedures
    5. Scoping and Binding of Variables
    6. Eliminating Variable Names
    7. Implementing Lexical Addressing
(To be continued...)

# 1. Inductive Sets of Data
- It introduces the basic programming tools for writing interpreters, checkers, and similar programs.
- It also has **recursion**.

## 1.1. Recursively Specified Data
We need to know for a procedure what arguments receives and what kind of values return.

### 1.1.1. Inductive Specification
It's a method for specifying a set of values, *for example:* $N = \\\{0, 1, 2, ...\\\}$ or like this:
**Definition 1.1.1 (top-down)** *A natural number n is in S if and only if*
1. $n = 0$, or
2. $n - 3 ∈ S$

In that definition, 0, 3, 6 make part of $S$. That can be written in the next way:
```
in-S? : N → Bool
usage: (in-S? n) = #t if n is in S, #f otherwise
(define in-S?
  (lambda (n)
    (if (zero? n) #t
      (if (>= (- n 3) 0)
         (in-S? (- n 3))
          #f))))
```
The last piece of code is **recursive**. You can understand how it works ;)

You can write it also like this:
**Definition 1.1.2 (bottom-up)** *Define the set S to be the smallest set contained in N and satisfying the following two properties:**
1. $0 ∈ S$ and
2. $if n ∈ S$, then $n+3 ∈S$

And you can write it like this (rules-of-interference):  
![Third way of writing definition](https://user-images.githubusercontent.com/83418390/225482398-6d4af9c6-7f6a-4300-a8fa-54b2eeec5d9f.png)  
It can be read as "If this then that".
This is another example using the same methods:  
![Another example](https://user-images.githubusercontent.com/83418390/225483035-0e87da42-8d24-423d-a71d-b32c542b3897.png)  
So, `(), (3 . ()), (-7 . (3 . ()))`, and so on are lists

### 1.1.2 Defining Sets using Grammars
Describing data with the last section is cumbersome. You can use **grammars** They can be used for defining sets of values. Like for example:
```
List-of-Int ::== ()
List-of-Int ::== (Int . List-of-Int)
```
