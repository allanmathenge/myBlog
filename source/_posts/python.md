---
title: Python
date: 2023-010-14 18:29:30
tags:
---

#       Abstract

Python is a popular, high-level programming language.It was created by Guido van Rossum and first released in 1991. Python's design and philosophy emphasize code readability. It has some similarities to English language with Mathematics influence and an easy-to-learn syntax. Python syntax for example uses new lines to complete a command, as opposed to other programming languages which often use semicolons or parenthesis. Python is an interpreted language to mean code is executed as it is written. It is widely adopted due to its simplicity and flexibility. There are no type declarations of variables, functions or methods which make the code short and flexible. It is an excellent choice for both beginners and experienced developers. Among other uses, Python is widely used for server-side web development to connect to database systems, software development, handling big data, perfom complex mathematics and system scripting. Python also works on different platforms like Windows, Linux, Mac etc. The most recent version of Python is Python 3. In this article we will use Python 3 version to explore the key concepts in Python Programming Language.

# **Fundamentals and Overview**

Unlike other programming languages like C or JavaScript, Python does not use curly braces or other symbols to define code blocks. It uses identation. This makes Python code easy to read and understand. Another key concept in Python is the use of variables. Variables are used to store data used as reference to that data. There is no need to use declarative keywords like "var" or "int" in declaring variables. Python uses **'#'** to comment lines of code. There are a variety of data types in Python including strings, numbers(integers and floats), lists and dictionaries. Specific methods are used to manipulate and work with the different data types. Python has also a number of built-in functions. For example the "print()" is used to output data to the terminal while "math" module provides a variety of mathematical functions. Also, Python widely supports object-oriented programming and methods for handling errors and exceptions using "try-except". Let us dive into detailed discussion of these concepts.

## Variables

A variable is used to store values. Variables are created by assigning a value to it using "=" operator. The value of the variable can be any data type and can be used throughout the programm. For example:

    value = "y"
    _count = 0

It is important to note that variable name must start with a letter or an underscore.
You can change the value of a variable by reassigning it to a new value. For example:

    value = "z"
    _count = 10

## Data Types

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
    // Output: True

In this example, x is a String(str) 

## Operators

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
    print(result) // Output: 11

*Using the < to check if x is less than y*

    result = x < y
    print(result) // Output: True

*Using the '*=' operator to multiply y by x*

    result y *= x
    print(y) // Output: 24

## Conditional Statements

Conditional statements are used to execute code depending on different conditions. *if-else* is the most common type of conditional statement. It works in the following syntax:

    if condition:
    # code is executed if the condition is true
    else:
    # code is executed if the condition is false

The condition in the if statement is Boolean (evaluates True or False). If true, the code in the if block is executed, if not, the code in the else block is executed.

    p = 4
    if p > 0:
    print("p is positive")
    else:
    print("p is negative")

p > 0 evaluates true so the output is "p is positive".

*-elif-* statement which is the short for `else if` allows you to check multiple conditions.

    p = 4
    if p > 4:
    print("p is positive")
    elif p == 0:
    print("p is zero")
    else:
    print("p is negative")

Note that the 'condition' in the if statement can be comparison operators, logical or function calls that return a Boolean value.

## Loops

There are two types of loops in Python: `for` and `while` loops which allow you to execute repeatedly a block of code.

1. ### *For loops*: 
Are used to iterate over a sequence of items and execute a block of code for each item. For example:

    numbers = [1, 2, 3, 4, 5]
    for x in numbers:
    print(x) // output: 1, 2, 3, 4, 5

In this example, the for loop will iterate over the list and print each number in the list.

2. ### *While loops*: 
Are used to execute a block of code repeatedly given a certain condition is true. For example:

    x = 0
    while x < 5:
    print(x)
    x += 1 //Output: 0 1 2 3 4

The loop will execute as long as the '*x < 5*' is true. It will print 0 1 2 3 4 until it x becomes 5, and the condition evaluates to false. Ensure that the loop finally evaluates to false, otherwise, the loop will run indefinitely causing an infinite loop.
The `break` and `continue` statements are used to control the flow of the loop. `break` is used to exit the loop while `continue` is used to skip the iteration and move to the next iteration.

## Functions

Refer to a block of code that can be reused throughout a program. They are usually useful for breaking down complex programs into smaller more manageable blocks. The following is a basic syntax of a function:

    def fun_name(parameters):
        # Block of code to be executed

The fun_name is the name of the function. `parameters` are input values that are passed to the function. The code inside the function is executed when the function is called.

    def greetings(name):
    print("👋Hello" + name + ".")
    greetings("Allan") // Output: 👋Hello Allan.

The function `greetings` takes one parameter 'name'. When the function is called it prints the string "👋Hello" followed by the 'name' parameter "Allan".
The '*return*' statement in a function is used to return a value. It allows you to return a value to the calling function.

    def sum(x, y):
    return x + y
    product = sum(4, 5)
    print(product)

The 'sum' function takes in two parameters *'x and y'* and return the result of adding them together. The function is called with the values 4 and 5 and the returned value is stored in the '*product*' variable.

Another important concept is; functions can have default parameters. These default parameters are used when the caller does not provide it a value. For example:

    def greetings(name, greet = "Hello")
    print(greet + name +".")
    greetings("Allan")

The 'greetings' function has one mandatory parameter 'name' and one optional parameter 'greet' with "Hello" value. When the function is called without providing a value for the 'greet' parameter, the value "Hello" is used as default.

# Classes and Objects

In Python, classes are templates for creating objects. It defines the data and methods that object of that class will have. The objects created from the same class have common characteristics and behaviours. **Object-oriented programming (OOP)** is a programming paradigm based on the idea that, software systems can be designed and constructed by modeling real-world entities and their interactions as objects. OOP provides a way to structure and organize code that is reusable, maintainable and scalable.

The `class` keyword is used to define a class, followed by the class name and a colon. The body is idented and contains the data and methods. For example:

    class Vehicle:
        def __init__(self, make, model)
        self.make = make
        self.model = model
        def moves(self)
            print(f"The {self.make} moves along.")
    my_car = Vehicle("Cadillac", "model 3")
    my_car.moves() // Output: The Cadillac Model 3 moves along.

In this example, the 'Vehicle' class has two data attributes 'make' and 'model 3' and one method (behaviour) that prints the make of the Vehicle. To create an object, use the class name followed by parentheses - it's known as instantiation. The data object is initialized with make as "Cadillac" and model as "model 3".

### Inheritance
Classes can also inherit from other classes. Inheritance allows you to create a class that inherits the data and behaviour of an existing class. You can also add new data and new behaviour of its own. The class that inherits from another class is called the **child** and the class that is inherited from is the **parent** class.

    class Airplane(Vehicle):
    def __init__(self, make, model, plane_id):
        super().__init__(make, model)
        self.plane_id = plane_id

    def moves(self):
        print(f"The {self.make} {self.model} {self.plane_id} flew along.")

    boeing = Airplane('Boeing', 'Skyhawk', 'KQ707')

The `super()` function is used as a subsititute for inherited attributes (make and model) to reduce repetition.

### Exception handling
Exception handling in Python enables you to effectively handle errors and exception situations that occur during runnin of a program. Catching and handling exceptions prevents your program from crashing. The following class component was used to define errors.

    class Handle_exceptions_raised(Exception)
        pass

    x = 2
    try:
        print(x / 0)
        raise  Handle_exceptions_raised("I am a custom exception!")
    except ZeroDivisionError:
        print("Please do not devide by zero")
    except NameError:
        print("NameError - Means something is undefined")
    except Exception as error:
        print(f"An error occurred: {error}")
    else:
        print("No Errors")
    finally:
        # Cleanup code (always excecuted)
        print("Execution complete, print with or without an error")


1. **try**: We enclose a block of code that may raise an exception. If an exception occurs, the program runs the matching `except` block. In the above example, the product of `print(x / 0)` was `undefined`. `NameError` was therefore raised as the matching exception.

2. **except**: Specify the type of exception you want to catch in the `except` block. If an exception of the specified type occurs in the `try` block, the matching code inside the `except` block is executed. In the above example, multiple exceptions were provided, but only `NameError` was evaluated as the matching `except` result of `print(x / 0)`.

3. **finally**: Is used to specify a block of code that should always be excecuted, whether an exception occured or not. It is used for excecuting cleanup functions e.g closing files.

4. **raise**: is useful when you want to raise an exceptional situation. An example:

    if an_exceptional_situation_happen:
        raise someException("An error occurred!")

Because unexpected errors are effectively handled error handling in Python make the program efficient and user friendly. 

## Higher Order Functions (HOF)

Higher-order function is a function that takes in one or more functions as arguments return another function as its result. They are an essential part of Python programming. The `map()`, `filter()` and `reduce()` are the basic building blocks of higher-order functions. `map()` and `filter()` are built-in functions, whereas `reduce()` is contained in `functools()` module.

*(i)* The `map()` function applies a given function to each item in an iterable. In the example below, the square of the iterator results are returned.

    numbers = [3, 7, 12, 18, 20, 21]

    squared_nums = map(lambda num: num * num, numbers)

    print(list(squared_nums)) // Output: [9, 49, 144, 324, 400, 441]

`lambda()` is an anonymous function. It was used to return a map object in iteration.

*(ii)* The `filter()` function filters elements from an iterable based on a its Boolean return value.

    numbers = [3, 7, 12, 18, 20, 21]

    odd_nums = filter(lambda num: num % 2 != 0, numbers)

    print(list(odd_nums)) //Output: [3, 7, 21]

*(iii)* The `reduce()` function from the `functools` module repeatedly applies a function to the elements of an iterable, accummulating result.

    from functools import reduce

    numbers = [1, 2, 3, 4, 5, 1]

    total = reduce(lambda acc, curr: acc + curr, numbers, 10)

    print(total) //Output: 26 note: the addition start at 10



# *contact author: allanmathenge2@gmail.com*

<script async src="https://talk.hyvor.com/embed/embed.js" type="module"></script>
<hyvor-talk-comments website-id="9814" page-id=""></hyvor-talk-comments>
