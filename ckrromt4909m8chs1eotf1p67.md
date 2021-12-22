## Usage of the Underscore(_) in Python?

This is a continued story of my previous post [Star in Python](https://soumendrak.hashnode.dev/the-python-star).

In this article, we will know about the usage of underscore in Python.


## As a placeholder of variable

If you do not use a variable then you can name it as underscore.

``` python
>>> my_dict = {'a': 1, 'b': 2}
>>> for k, _ in my_dict.items():
...    print(f"The keys are: {k}")
The keys are: a
The keys are: b
```
Here we have not used the values of the dictionary therefore no need to assign that to a named variable, underscore we have used to denote the values of the dictionary. This is a best practice.  
Although this is not such an excellent example, hope you got the point.

## In object-oriented programming

Underscore plays a significant part in OOP.

### Private method

To define a private method `_` prefix is used.

``` python

>>> class myClass:
...    def _my_private_method(self):
...    pass

```

### Protected method

``` python
>>> class myClass:
...    def __my_protected_method(self):
...    pass

```

### Dunder method

To define in-built under methods

``` python
>>> class myClass:
...    def __init__(self):
...    pass

```

## Variable name delimiter

Under [PEP8 guideline](https://www.python.org/dev/peps/pep-0008/#method-names-and-instance-variables) variable names should be delimited with underscores.

## Access last executed result in command prompt

In the terminal or command prompt to access the last output of the operation you can use the underscore.

``` python
>>> 4 + 3
7
>>> _
7
```
`ipython` takes it to the next level with number-based access.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1640205151011/eewaoMSyA.png)

## Separate digits for readability

``` python
>>> 1_00_000
100000
>>> 3_25_50_000 == 32550000
True
```

Photo by the author.

## Further reading

- [5 usages of asterisk](https://blog.soumendrak.com/5-usages-of-an-asterisk-in-python)
- [Cool Python tricks you are not using, but you should](https://blog.soumendrak.com/cool-python-tricks-you-are-not-using-but-you-should)
- [https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value](https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value)
- [In Python, do you know double for loops with conditions in a list-comprehension?](https://blog.soumendrak.com/in-python-do-you-know-double-for-loops-with-conditions-in-a-list-comprehension)
- [Optimize your Python code](https://blog.soumendrak.com/optimize-your-python-code-d7e9752e501e)