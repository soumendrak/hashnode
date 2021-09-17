## In Python, do you know double for loops with conditions in a list-comprehension?

### Single for-loop with if condition
``` python
my_list = []
for x in range(3):
    if x % 2 == 0:
        my_list.append(x)
```
In List comprehension

``` python
>>> my_list = [x for x in range(3) if x % 2 == 0]
>>> my_list
[0, 2]
```

### Single for-loop with if-else conditions

``` python
my_list = []
for x in range(3):
    if x % 2 == 0:
        my_list.append(y)
    else:
        my_list.append('odd')
```
In List comprehension

``` python
>>> my_list = [x if x % 2 == 0 else 'odd' for x in range(3)]
>>> my_list
[0, 'odd', 2]
```
### Double for-loops with if condition

``` python
my_list = []
for x in range(3):
    for y in range(x):
        if y % 2 == 0:
            my_list.append(y)
```
In List comprehension

``` python
>>> my_list = [y for x in range(3) for y in range(x) if y % 2 == 0]
>>> my_list
[0, 0]
```


### Double for-loops with if and else conditions

``` python
my_list = []
for x in range(3):
    for y in range(x):
        if y % 2 == 0:
            my_list.append(y)
        else:
            my_list.append('odd')
```
In List comprehension

``` python
>>> my_list = [y if y % 2 == 0 else 'odd' for x in range(3) for y in range(x)]
>>> my_list
[0, 0, 'odd']
```
*Disclaimer:*
Writing double for loops with if-else conditions severely affect the readability of the code. Please use at your own risk.  

<span>Photo by <a href="https://unsplash.com/@aznbokchoy?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Lucas Benjamin</a> on <a href="https://unsplash.com/s/photos/abstract?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>
