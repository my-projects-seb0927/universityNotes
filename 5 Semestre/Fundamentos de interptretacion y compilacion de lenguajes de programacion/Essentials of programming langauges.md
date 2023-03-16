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
It's a method for specifying a set of values, *for example:* $N = \\\{0, 1, 2, ...\\\}$
