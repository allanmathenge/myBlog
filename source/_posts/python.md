---
title: Python
date: 2023-010-14 18:29:30
tags:
---

#       Abstract

Python is a popular, high-level programming language.It was created by Guido van Rossum and first released in 1991. Python's design and philosophy emphasize code readability. It has some similarities to English language with Mathematics influence and an easy-to-learn syntax. Python syntax for example uses new lines to complete a command, as opposed to other programming languages which often use semicolons or parenthesis. Python is an interpreted language to mean code is executed as it is written. It is widely adopted due to its simplicity and flexibility. There are no type declarations of variables, functions or methods which make the code short and flexible. It is an excellent choice for both beginners and experienced developers. Among other uses, Python is widely used for server-side web development to connect to database systems, software development, handling big data, perfom complex mathematics and system scripting. Python also works on different platforms like Windows, Linux, Mac etc. The most recent version of Python is Python 3. In this article we will use Python 3 version to explore the key concepts in Python Programming Language.

# **Fundamentals and Overview**

Unlike other programming languages like C or JavaScript, Python does not use curly braces or other symbols to define code blocks. It uses identation. This makes Python code easy to read and understand. Another key concept in Python is the use of variables. Variables are used to store data used as reference to that data. There is no need to use declarative keywords like "var" or "int" in declaring variables. Python uses *#* to comment lines of code. Python has variety of data types, including strings, numbers(integers and floats), lists and dictionaries. Specific methods are used to manipulate and work with the different data types. Python has also a number of built-in functions. For example the "print()" is used to output data to the terminal while "math" module provide a variety of mathematical functions. Python also widely supports object-oriented programming and methods for handling errors and exceptions using "try-except". Let us dive into detailed discussion of these concepts.

# Variables

A variable is used to store values. Variables are created by assigning a value to it using "=" operator. The value of the variable can be any data type and can be used throughout the programm. For example:

    value = "y"
    _count = 0

It is important to note that variable name must start with a letter or an underscore.
You can change the value of a variable by reassigning it to a new value. For example:

    value = "z"
    _count = 10

# Data Types

In Python, data types refer to the value a variable holds. There are several built-in data-types in Python which include integers, floating-point numbers, strings etc. Let us discuss these data types:
1. *Numbers*: They include integers (e.g 1, 2, 3) and floating-point numbers (e.g 1.234, 6.123)
2. *Strings*: Enclosed in a single or double quotes, a string is sequence of characters. an example f = "Hello world!" is a string.
3. *Lists*: Written with square brackets amd separated by commas, a list is a collection of ordered changeable items. Example b = [2, 3, 4]
4. *Tuples*: Written with round brackets and separated by commas, a tuple is similar to a list but its items cannot be changed. Example t = (5, 6, 7)
5. *Dictionaries*: Written with curly braces, a dictionary is a collection of key-value pairs and separated by colons.
6. *Boolean*: Boolean data type is either True or False.
7. *None*: This is a special constant used to represnt the absence of a value or a null value.

    value = "z"
    print(type(z) == str)
    Output: True

In this example, x is a String(str) 

# Operators

For performing mathematical operations, Python supports multiple operators such as addition(+), subtraction(-), multiplication(*), division(/) and remainder(%). Here are some common operators in Python:

1. *Arithmetic operators*: They include the above named operators.
2. *Comparison operators*: They are operators that compare two values and return a Boolean. They include equal to (==), not equal to (!=), greater than (>), less than (<), greater than or equal to (>=) and less than or equal to(<=).
3. *Membership operators*: Are used to test whether a value is in a series of values in a list or a string. They include *-in-* and *-not in-*.
4. *Assignment operators*: Are used to assign value to a variable, they include =, +=, -=, *=, /= and %=.
5. *Identity operators*: Are used to compare the identity of two objects. *-is-* and *-is not-* are identity operators in python.

For example:

    x = 3
    y = 8

*Using the + operator to add x and y*

    result = x + y
    print(result) // Output: 15

*Using the < to check if x is less than y*

    result = x < y
    print(result) // Output: True

*Using the *= operator to multiply y by 4*

    result y *= x
    print(y) // Output: 24

# Conditional Statements



<script async src="https://talk.hyvor.com/embed/embed.js" type="module"></script>
<hyvor-talk-comments website-id="9342" page-id=""></hyvor-talk-comments>
