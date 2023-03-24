---
title: "@property in Python"
seoTitle: "Python @property"
seoDescription: "Python's `@property` decorator creates class properties with controlled attribute access via getter, setter, and deleter methods"
datePublished: Sat Mar 18 2023 09:39:39 GMT+0000 (Coordinated Universal Time)
cuid: clfds2brv01gyr3nv9ft32b7v
slug: property-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678992304060/3e33f3c6-96c8-40dd-ae6d-d792d00492c9.png
tags: python, python3, property, decorators, getter-and-setter

---


1. Introduction  
    Sure! Here's an introduction to Python's `@property` decorator with code snippets:
    
    In Python, a decorator is a unique function that can modify other functions' behavior. You can think of decorators as a way to "wrap" one function with another. This can be useful for adding functionality to functions without changing their code.
    
    One built-in decorator in Python is `@property`, used with the `property()` function. Here's an example that shows how you can use `@property` to define a read-only property for a class:
    
    ```python
    class Circle:
        def __init__(self, radius):
            self._radius = radius
    
        @property
        def radius(self):
            return self._radius
    
    c = Circle(5)
    print(c.radius) # 5
    c.radius = 10 # AttributeError: can't set attribute
    ```
    
    In this example, we define a class `Circle` with a private attribute `_radius`. We then use the `@property` decorator to define a method `radius()` that returns the value of `_radius`. When we create an instance of `Circle`, we can access the value of `_radius` using the `.radius` property. However, since we haven't defined a setter method for `.radius`, trying to set its value will result in an error.
    
2. Use Cases
    
    Here's an explanation of why you should use `@property` with example usages:
    
    Using the `@property` decorator can be helpful in several ways when defining properties in a class. Here are some examples:
    
    1. **Encapsulation**: By using `@property`, you can control access to an attribute by defining getter, setter, and deleter methods. This allows you to hide the implementation details of an attribute and only expose a public interface for accessing it.
        
    
    ```python
    class Circle:
        def __init__(self, radius):
            self._radius = radius
    
        @property
        def radius(self):
            return self._radius
    
    c = Circle(5)
    print(c.radius) # 5
    ```
    
    In this example, we define a class `Circle` with a private attribute `_radius`. We then use the `@property` decorator to define a method `radius()` that returns the value of `_radius`. When we create an instance of `Circle`, we can access the value of `_radius` using the `.radius` property.
    
    1. **Validation**: You can use the setter method to validate the value being assigned to an attribute. For example, you can check if the value is within a specific range or meets certain conditions before assigning it.
        
    
    ```python
    class Circle:
        def __init__(self, radius):
            self._radius = radius
    
        @property
        def radius(self):
            return self._radius
    
        @radius.setter
        def radius(self, value):
            if value < 0:
                raise ValueError("Radius cannot be negative")
            self._radius = value
    
    c = Circle(5)
    print(c.radius) # 5
    c.radius = -1 # ValueError: Radius cannot be negative
    ```
    
    In this example, we define a class `Circle` with a private attribute `_radius`. We then use the `@property` decorator to define a method `radius()` that returns the value of `_radius`, and the `.setter` decorator to define a method `radius()` that sets the value of `_radius` .
    
    1. **Ease of use**: Using `@property` makes it easy to define properties without manually calling the `property()` function. This can make your code more readable and easier to understand.
        
    
    ```python
    class Circle:
        def __init__(self, radius):
            self._radius = radius
    
        def get_radius(self):
            return self._radius
    
        def set_radius(self, value):
            if value < 0:
                raise ValueError("Radius cannot be negative")
            self._radius = value
    
        radius = property(get_radius, set_radius)
    
    c = Circle(5)
    print(c.radius) # 5
    c.radius = -1 # ValueError: Radius cannot be negative
    ```
    
    In this example, we define a class `Circle` with a private attribute `_radius`. We then define methods `get_radius()` and `set_radius()` for getting and setting the value of `_radius`. We use the `property()` function to create a property `.radius` that uses these methods.
    
    This code achieves the same result as the previous example but is less readable and harder to understand. Using `@property` makes it easier to define properties more intuitively.
    
    Overall, using `@property` can help you write cleaner and more maintainable code when defining properties in a class.
    
3. Syntax and Examples
    
    This example shows how you can use `@property`, along with the `.setter` and `.deleter` decorators to define a property with getter, setter, and deleter methods:
    
    ```python
    class Circle:
        def __init__(self, radius):
            self._radius = radius
    
        @property
        def radius(self):
            return self._radius
    
        @radius.setter
        def radius(self, value):
            if value < 0:
                raise ValueError("Radius cannot be negative")
            self._radius = value
    
        @radius.deleter
        def radius(self):
            del self._radius
    
    c = Circle(5)
    print(c.radius) # 5
    c.radius = 10
    print(c.radius) # 10
    del c.radius
    ```
    
    In this example, we define a class `Circle` with a private attribute `_radius`. We then use the `@property` decorator to define a method `radius()` that returns the value of `_radius`. We also use the `.setter` decorator to define a method `radius()` that sets the value of `_radius`, and the `.deleter` decorator to define a method `radius()` that deletes `_radius`.
    
    When we create an instance of `Circle`, we can access and modify the value of `_radius` using the `.radius` property. We can also delete `_radius` using the `del` statement.
    
4. Conclusion
    
    Key points and benefits of using `@property`:
    
    * `@property` is a decorator that can be used to define properties in a class.
        
    * It allows you to control access to an attribute by defining getter, setter, and deleter methods.
        
    * Using `@property` can help you achieve encapsulation by hiding the implementation details of an attribute and only exposing a public interface for accessing it.
        
    * You can use the setter method to validate the value being assigned to an attribute before assigning it.
        
    * Using `@property` makes it easy to define properties without manually calling the `property()` function. This can make your code more readable and easier to understand.
        
    
    Overall, using `@property` can help you write cleaner and more maintainable code when defining properties in a class.