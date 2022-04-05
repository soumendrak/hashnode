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
### Last element of an iterable

To fetch the last element of any iterable like list, tuple or set.

#### For list/tuple

```python
>>> zlst = ['a', 'b', 'c']
>>> zlst[-1]
'c'
>>> *_, e = zlst
# if you do not want to use the non-last elements
>>> e
'c'
>>> ztup = ('a', 'b', 'c')
>>> ztup[-1]
'c'

```

#### For set

```python
>>> my_set = {'a', 'b', 'c'}
>>> my_set[-1]
TypeError: 'set' object is not subscriptable
>>> q, w, e = my_set
>>> e
'c'
>>> *q, e = my_set
>>> e
'c'
>>> q
['a', 'b']
# q is not a set
```
More tricks will be added soon.
The cover picture is copyrighted to the author.

## Code formatting

- Use black to format your codebase.
- Have a large project, can do one at a time or one file at a time.
- Here is my favorite config I use to auto-format my code modules.

```sh
$ pip install black
$ black folder/file.py -l 120 -t py38 
reformatted folder/file.py
All done! ✨ 🍰 ✨
1 file reformatted.
```

- `-l`: I use 120 as the maximum characters I accept in a line
- `-t py38`: Python 3.8 specific custom formatting.

## Further reading

- [Do you know all the usage of the Underscore in Python?](https://blog.soumendrak.com/do-you-know-all-the-usage-of-the-underscore-in-python)
- [5 usages of asterisk](https://blog.soumendrak.com/5-usages-of-an-asterisk-in-python)
- [https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value](https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value)
- [In Python, do you know double for loops with conditions in a list-comprehension?](https://blog.soumendrak.com/in-python-do-you-know-double-for-loops-with-conditions-in-a-list-comprehension)
- [Optimize your Python code](https://blog.soumendrak.com/optimize-your-python-code-d7e9752e501e)
