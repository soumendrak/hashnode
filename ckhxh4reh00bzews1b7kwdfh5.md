---
title: "Python double/nested for loop list comprehension"
seoTitle: "Python double/nested for loop list comprehension with conditions"
seoDescription: "Optimize Python with list comprehension: learn nested or double for-loops, if/else conditions for efficient programming. Use at your own risk."
datePublished: Wed Nov 25 2020 13:59:00 GMT+0000 (Coordinated Universal Time)
cuid: ckhxh4reh00bzews1b7kwdfh5
slug: python-double-nested-for-loop-list-comprehension
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/StvYPDirU6o/upload/a595686144447fe354dd3bbf09b8f28c.jpeg
tags: programming-blogs, python, python3, python-beginner, python-projects

---

### Single for-loop with if condition

```python
my_list = []
for x in range(3):
    if x % 2 == 0:
        my_list.append(x)
```

In List comprehension

```python
>>> my_list = [x for x in range(3) if x % 2 == 0]
>>> my_list
[0, 2]
```

### Single for-loop with if-else conditions

```python
my_list = []
for x in range(3):
    if x % 2 == 0:
        my_list.append(y)
    else:
        my_list.append('odd')
```

In List comprehension

```python
>>> my_list = [x if x % 2 == 0 else 'odd' for x in range(3)]
>>> my_list
[0, 'odd', 2]
```

### Double for-loops with if condition

```python
my_list = []
for x in range(3):
    for y in range(x):
        if y % 2 == 0:
            my_list.append(y)
```

In List comprehension

```python
>>> my_list = [y for x in range(3) for y in range(x) if y % 2 == 0]
>>> my_list
[0, 0]
```

See how the outer for loop came first then the inner for loop

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678766499844/89d7af34-f7bf-467b-b491-35f4ea15ec56.gif align="center")

### Double for-loops with if and else conditions

```python
my_list = []
for x in range(3):
    for y in range(x):
        if y % 2 == 0:
            my_list.append(y)
        else:
            my_list.append('odd')
```

In List comprehension

```python
>>> my_list = [y if y % 2 == 0 else 'odd' for x in range(3) for y in range(x)]
>>> my_list
[0, 0, 'odd']
```

*Disclaimer:* Writing double for loops with if-else conditions severely affects the readability of the code. Please use it at your own risk.