# Usage of forward slash (/) in Python

In Python, the forward-slash (/) has several different uses depending on the context in which it appears. Some of the main uses of the forward slash in Python include:

## Division
When used between two numeric values, the forward slash performs division. 
For example, 10 / 3 evaluates to 3.3333333333333335.

```python
>>> 10/3
3.3333333333333335
```

## Floor division 
When used between two numeric values, the forward slash followed by another forward slash (//) performs floor division, which rounds the result down to the nearest integer. 
For example, 10 / 3 evaluates to 3, and 10 // 3 evaluates to 3.

```python
>>> 10//3
3
```

## Paths
In strings, the forward slash is often used as a separator in file paths or URLs. 
For example:

```python
path = "C:/Users/john/Documents/file.txt"
url = "https://www.example.com/path/to/resource"
```

## Regular expressions
In regular expressions, the forward slash is often used to escape special characters. For example:

```python
import re

pattern = r"\d+/\d+/\d+"
text = "The date is 01/01/2021"
match = re.search(pattern, text)
```

Thanks for reading, you can further check:
- [5 usages of an asterisk (*) in Python](https://blog.soumendrak.com/5-usages-of-an-asterisk-in-python)
- [Usage of the Underscore(_) in Python](https://blog.soumendrak.com/usage-of-the-underscore-in-python)

Let me know what you think at any of the following places:

- 🔗 LinkedIn: https://www.linkedin.com/in/soumendrak/
- 📝 Medium: https://medium.com/@soumendrak
- 📖 Blog: https://blog.soumendrak.com/
- 🐥 Twitter: https://twitter.com/soumendrak_
- 🧑🏻‍💻 Github: https://github.com/soumendrak