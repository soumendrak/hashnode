## Cool Python tricks you are not using, but you should.

## Ternary operator

``` python
ans = z if a > b else c
```
is same as 

``` python
if a > b:
    ans = z
else:
    ans = c
```

## Short circuit

``` python
result = counter or 15
```
is same as
``` python
result = counter if counter else 15
```
is same as 
``` python
if not counter:
    result = 15
else:
    result = counter
```
## Comparison

``` python
if 3 > a > 1 < b < 5: foo()
```
instead of
``` python
if a > 1 and b > 1 and  a < 3 and  b < 5: foo()
```

## Reverse an iterable

```python
[1, 2, 3, 4][::-1] # => [4, 3, 2, 1]
```

## Unpacking

``` python
z = [1, 2, 3, 4, 5, 6]
a, *b, c = z
```
is same as

``` python
b = []
for i, val in enumerate(z):
    if i == 0:
        a = val
    elif i == len(z) - 1:
        c = val
    else:
        b.append(val)
```

### swapping two variables

``` python
a, b = b, a
# this is tuple unpacking
```

More tricks will be added soon.
The cover picture is copyrighted to the author.

## Further reading

- [Do you know all the usage of the Underscore in Python?](https://blog.soumendrak.com/do-you-know-all-the-usage-of-the-underscore-in-python)
- [5 usages of asterisk](https://blog.soumendrak.com/5-usages-of-an-asterisk-in-python)
- [Cool Python tricks you are not using, but you should](https://blog.soumendrak.com/cool-python-tricks-you-are-not-using-but-you-should)
- [https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value](https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value)
- [In Python, do you know double for loops with conditions in a list-comprehension?](https://blog.soumendrak.com/in-python-do-you-know-double-for-loops-with-conditions-in-a-list-comprehension)
- [Optimize your Python code](https://blog.soumendrak.com/optimize-your-python-code-d7e9752e501e)
