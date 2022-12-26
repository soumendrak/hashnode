# Python: Built-in Exceptions

Python has a number of built-in errors that can be raised when your code encounters an issue. Here is a list of some of the most common built-in errors in Python, along with code examples to illustrate how they can occur:

1. **SyntaxError**: This error is raised when the Python interpreter encounters invalid syntax in your code. For example, if you forget to close a parenthesis, you may see a SyntaxError.
    

```python
# Example of a SyntaxError

def greet(name):
  print("Hello, " + name  # missing parenthesis mark at the end

greet("John")
```

1. **TypeError**: This error is raised when you try to perform an operation on an object of an incorrect type. For example, if you try to add a string and an integer, you will get a TypeError.
    

```python
# Example of a TypeError

a = "5"
b = 10
print(a + b)  # cannot concatenate a string and an int

------------------------------------------------------
TypeError: can only concatenate str (not "int") to str
```

1. **NameError**: This error is raised when you try to access a variable that has not been defined. For example, if you try to use a variable that you forgot to assign a value to, you will get a NameError.
    

```python
# Example of a NameError

print(x)  # x has not been defined
----------------------------------
NameError: name 'x' is not defined
```

1. **IndexError**: This error is raised when you try to access a list or string using an index that is out of bounds. For example, if you try to access the fifth element of a list that only has three elements, you will get an IndexError.
    

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

1. **ValueError**: This error is raised when you pass a value of the wrong type to a function or method. For example, if you try to convert a string to an integer using the `int()` function and the string cannot be parsed as an integer, you will get a ValueError.
    

```python
# Example of a ValueError

age = "twenty"
int(age)  # cannot convert the string "twenty" to an int
------------------------------------------------------------
ValueError: invalid literal for int() with base 10: 'twenty'
```

These are just a few examples of the built-in errors that you may encounter when working with Python. It is important to understand these errors and how to handle them, as they can help you debug your code and write more robust and reliable programs.

To get the full list of Exceptions check out the documentation, [Built-in Exceptions — Python 3.11.1 documentation](https://docs.python.org/3/library/exceptions.html). The hierarchy of the built-in exceptions:

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