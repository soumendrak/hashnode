---
title: "__repr__ in Python"
seoTitle: "Python's __repr__ method"
datePublished: Sat Mar 25 2023 05:48:39 GMT+0000 (Coordinated Universal Time)
cuid: clfnjw89a074krknvbxwn4ica
slug: repr-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679624740604/e4167bb8-39ea-4450-a814-8b5d0e785a00.png
tags: python, python-beginner, python-advanced, repr, str

---

## Introduction

This blog post will explore the Python magic method, `__repr__`. This method is useful and even necessary to display a human-readable representation of an object. We'll start with the basics and work up to more advanced concepts.

## What is `__repr__`?

* `__repr__` is a magic method in Python that allows us to define a human-readable representation of an object.
    
* When we call the built-in `repr()` function on an object, Python looks for a `__repr__` method within that object's class definition. If it finds one, it returns the result of that method; otherwise, it provides a default representation.
    
* It's important to note the difference between `__repr__` and `__str__`: while `__repr__` is designed to provide an unambiguous representation of the object (which can ideally be used to recreate it), `__str__` is meant to return a more user-friendly string representation. We will discuss more on this.
    

## Creating a primary `__repr__` method

Let's make a simple class Person without a `__repr__` method.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
                
person = Person("Soumendra", 30)
print(person)  # Output: <__main__.Person object at 0x7f8893925df0>
```

Without `__repr__` method, the object points to the memory address.

Let's create a simple class Person with a `__repr__` method.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def __repr__(self):
        return f"{type(self).__name__}('{self.name}', {self.age})"
        
person = Person("Soumendra", 30)
print(person)  # Output: Person('Soumendra', 30)
```

* Our `__repr__` method returns a string that looks like the object's constructor, making it easy to understand and recreate the object if needed.
    
* `type(self).__name__` is a best practice to use rather than hard coding the class name.
    

## `__str__` and `__repr__`

* We use `__str__` method for more user-friendly logs for humans to read.
    
* The print statement searches for `__str__` method first in a class, otherwise it goes for `__repr__` method.
    
* For example:
    
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age
            
        def __repr__(self):
            return f"{type(self).__name__}('{self.name}', {self.age})"
    
        def __str__(self):
            return f"A {type(self).__name__} object of name, {self.name} and age, {self.age}."
            
    person = Person("Soumendra", 30)
    print(person)  # Output: A Person object of name, Soumendra and age, 30.
    print(repr(person))  # Output: Person('Soumendra', 30)
    ```
    

## How to write effective `__repr__` methods

When writing a `__repr__` method, include all relevant object attributes, and ensure the output is unambiguous. This allows other developers to quickly understand the object's state and reconstruct it if necessary.

* To reconstruct the object from the repr output, make sure to add all the constructors (`__init__`) attributes to the `__repr__` method. Therefore, it becomes easy to replicate the object. For example, in the above `Person` class example:
    
    ```python-repl
    >>> person = Person("Soumendra", 30)
    >>> person
    Person('Soumendra', 30)
    >>> new_person = eval(repr(person))
    >>> new_person
    Person('Soumendra', 30)
    ```
    
    It's easy to recreate another object of the same class.
    
* Dynamic **repr** methods: You can create dynamic `__repr__` methods using class attributes. For example:
    
    ```python
    class MyClass:
        repr_format = "MyClass({self.attribute})"
        
        def __init__(self, attribute):
            self.attribute = attribute
            
        def __repr__(self):
            return self.repr_format.format(self=self)
    ```
    
* Inheritance and **repr**: Use class inheritance to create custom `__repr__` methods that leverage the parent class's `__repr__` implementation:
    
    ```python
    class Employee(Person):
        def __init__(self, name, age, job_title):
            super().__init__(name, age)
            self.job_title = job_title
            
        def __repr__(self):
            return f"{super().__repr__()}, '{self.job_title}')"
    ```
    

## Conclusion

Understanding Python's `__repr__` method is essential for creating informative and unambiguous object representations. By implementing custom `__repr__` methods and leveraging advanced techniques, you can improve the clarity and usability of your Python code.