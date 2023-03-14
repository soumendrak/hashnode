---
title: "Understanding Python's Pre-Constructed Exceptions for Beginners"
datePublished: Mon Dec 26 2022 03:18:42 GMT+0000 (Coordinated Universal Time)
cuid: clc48ckkz0l0hyfnv7kmy86p4
slug: python-built-in-exceptions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671937621102/5bc48782-4e9e-4ad2-9acd-b56a5c4d8362.png
tags: python, python3, python-beginner, exceptions

---

Explore the Most Common Built-In Errors in Python – Complete with Code Examples! Python is a universal language with many powerful features, but it can also throw various errors when your code encounters an issue. Here is an overview of some of the most common built-in errors in Python, complete with code examples to illustrate how they can occur.

1. **SyntaxError**: This error is raised when the Python interpreter encounters invalid syntax in your code. For example, if you forget to close a parenthesis, you may see a SyntaxError.
    

```python
# Example of a SyntaxError

def greet(name):
  print("Hello, " + name  # missing parenthesis mark at the end

greet("John")
```

1. **TypeError**: This error is raised when you try to operate on an object of an incorrect type. For example, if you try to add a string and an integer, you will get a TypeError.
    

```python
# Example of a TypeError

a = "5"
b = 10
print(a + b)  # cannot concatenate a string and an int

------------------------------------------------------
TypeError: can only concatenate str (not "int") to str
```

1. **NameError**: This error is raised when you try to access a variable that has not been defined. For example, if you try to use a variable you forgot to assign a value to, you will get a NameError.
    

```python
# Example of a NameError

print(x)  # x has not been defined
----------------------------------
NameError: name 'x' is not defined
```

1. **IndexError**: This error is raised when you try to access a list or string using an out-of-bounds index. For example, if you try to access the fifth element of a list with only three parts, you will get an IndexError.
    

```python
# Example of an IndexError

numbers = [1, 2, 3]
print(numbers[4])  # index 4 is out of bounds for the list
----------------------------------------------------------
IndexError: list index out of range
```

1. **KeyError**: This error is raised when you try to access a dictionary using a key that does not exist in the dictionary. For example, if you try to access a value using a key that has not been added to the dictionary, you will get a KeyError.
    

```python
# Example of a KeyError

colors = {"red": "#ff0000", "green": "#00ff00"}
print(colors["blue"])  # "blue" is not a key in the dictionary
--------------------------------------------------------------
KeyError: 'blue'
```

1. **ValueError**: This error is raised when you pass a value of the wrong type to a function or method. For example, if you try to convert a string to an integer using the `int()` function and the string cannot be parsed as an integer; you will get a ValueError.
    

```python
# Example of a ValueError

age = "twenty"
int(age)  # cannot convert the string "twenty" to an int
------------------------------------------------------------
ValueError: invalid literal for int() with base 10: 'twenty'
```

Understanding and handling Python's built-in errors can help you write more reliable and robust programs. Learn about common Python errors and how to debug them for better coding.

To get the complete list of Exceptions, check out the documentation, [Built-in Exceptions — Python 3.11.1 documentation](https://docs.python.org/3/library/exceptions.html). The hierarchy of the built-in exceptions:

```python
BaseException
 ├── BaseExceptionGroup
 ├── GeneratorExit
 ├── KeyboardInterrupt
 ├── SystemExit
 └── Exception
      ├── ArithmeticError
      │    ├── FloatingPointError
      │    ├── OverflowError
      │    └── ZeroDivisionError
      ├── AssertionError
      ├── AttributeError
      ├── BufferError
      ├── EOFError
      ├── ExceptionGroup [BaseExceptionGroup]
      ├── ImportError
      │    └── ModuleNotFoundError
      ├── LookupError
      │    ├── IndexError
      │    └── KeyError
      ├── MemoryError
      ├── NameError
      │    └── UnboundLocalError
      ├── OSError
      │    ├── BlockingIOError
      │    ├── ChildProcessError
      │    ├── ConnectionError
      │    │    ├── BrokenPipeError
      │    │    ├── ConnectionAbortedError
      │    │    ├── ConnectionRefusedError
      │    │    └── ConnectionResetError
      │    ├── FileExistsError
      │    ├── FileNotFoundError
      │    ├── InterruptedError
      │    ├── IsADirectoryError
      │    ├── NotADirectoryError
      │    ├── PermissionError
      │    ├── ProcessLookupError
      │    └── TimeoutError
      ├── ReferenceError
      ├── RuntimeError
      │    ├── NotImplementedError
      │    └── RecursionError
      ├── StopAsyncIteration
      ├── StopIteration
      ├── SyntaxError
      │    └── IndentationError
      │         └── TabError
      ├── SystemError
      ├── TypeError
      ├── ValueError
      │    └── UnicodeError
      │         ├── UnicodeDecodeError
      │         ├── UnicodeEncodeError
      │         └── UnicodeTranslateError
      └── Warning
           ├── BytesWarning
           ├── DeprecationWarning
           ├── EncodingWarning
           ├── FutureWarning
           ├── ImportWarning
           ├── PendingDeprecationWarning
           ├── ResourceWarning
           ├── RuntimeWarning
           ├── SyntaxWarning
           ├── UnicodeWarning
           └── UserWarning
```