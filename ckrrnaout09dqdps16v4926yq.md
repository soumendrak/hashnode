## 5 usages of an asterisk (*) in Python

# Star and Python

A star can be used in many scenarios in Python. Let's start.

## 1. Star as a multiplication operator

``` python
>>> 5 * 6
30
>>> 'star' * 2
starstar
>>> ['star'] * 2
['star', 'star']
```
## 2. Stars as exponential operator

``` python
>>> 2 ** 3
8
```

## 3. Star in arguments

``` python
>>> def add_num(*args):
...     for arg in args: print(arg)
...     return f"the sum is: {sum(args)}"
... 
>>> add_num(1,2,3)
1
2
3
the sum is: 6
```
Here the star helps to unpack iterables; called as **unpacking operator**.

## 4. Stars in keyword arguments

``` python
>>> def add_num(**kwargs):
...     return f"the sum is: {sum(kwargs.values())}"
...
>>> add_num(a=1, b=2, c=3)
the sum is: 6
```
Double stars can be used to unpack a dictionary

## 5. Stars to update two dictionaries

Merging two dictionaries can be done in many ways.

``` python
>>> x = {'a': 1, 'b': 2}
>>> y = {'a': 10, 'c': 30}
>>> yy = {'aa': 10, 'c': 30}
>>> z = x | y  # Union operator introduced recently
>>> z
{'a': 10, 'b': 2, 'c': 30}
>>> x.update(y)  # in place update
# as `y` value getting updated in `x`, `a` value getting overwritten from 1 to 10.
>>> x
{'a': 10, 'b': 2, 'c': 30}
>>> z = dict(**x, **yy)
>>> z
{'a': 1, 'b': 2, 'aa': 10, 'c': 30}
# same key in two dictionaries will throw error
>>> z = dict(**x, **y)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: dict() got multiple values for keyword argument 'a'

```
## Further reading

- [Do you know all the usage of the Underscore in Python?](https://blog.soumendrak.com/do-you-know-all-the-usage-of-the-underscore-in-python)
- [Cool Python tricks you are not using, but you should](https://blog.soumendrak.com/cool-python-tricks-you-are-not-using-but-you-should)
- [https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value](https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value)
- [In Python, do you know double for loops with conditions in a list-comprehension?](https://blog.soumendrak.com/in-python-do-you-know-double-for-loops-with-conditions-in-a-list-comprehension)
- [Optimize your Python code](https://blog.soumendrak.com/optimize-your-python-code-d7e9752e501e)

Photo by <a href="https://unsplash.com/@mikekilcoyne?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Michael Kilcoyne</a> on <a href="https://unsplash.com/s/photos/star?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  