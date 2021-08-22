## Optimize your Python code


As Python is one of the top prerequisites to learning Machine Learning, there is a huge influx of programmers/scientists from a different background.

Writing code in Python is easy. Few lines of code and it’s working! However, Python is slower compared to other languages. There are multiple ways we can optimize to run the loops a little faster and utilize less memory.

1. Code profiling (both memory and time)

1. Cython

1. Object-oriented programming with design patterns

1. Generators

1. Context managers

1. Multiprocessing

1. Using __slots__ operator

1. Using Pythonic code

1. Preloading memory intensive operations

1. Dead code removal

1. Modularization

1. Disabling unnecessary print statements

## Code profiling

To optimize a program we need to find the bottlenecks. There are [many libraries available](https://stackoverflow.com/q/582336/5014656) to profile a code. Some of the libraries which we used are [cProfile](https://docs.python.org/2/library/profile.html), [line_profiler](https://github.com/rkern/line_profiler), [pycallgraph](https://github.com/gak/pycallgraph). Other than these we used the *%%timeit* operator in Jupyter notebook and [memory_profiler](https://pypi.org/project/memory_profiler/). Memory profiler is used to keep the RAM usage under limit.

## Cython

[Cython](http://docs.cython.org/en/latest/src/userguide/language_basics.html?highlight=annotate.html)izing the python files will make them run faster. [[Reference](https://stackoverflow.com/questions/4872715/cythonize-a-python-function-to-make-it-faster#5033066)]

## Object-oriented programming with design patterns

Though python can be used as a functional programming language. For a production level code [design patterns](https://github.com/faif/python-patterns) need to be followed for future support and enhancements. [[Reference](https://legacy.python.org/workshops/1997-10/proceedings/savikko.html)][[Reference](https://www.toptal.com/python/python-design-patterns)]

## Dead code removal

Dead codes which were written for some operation but are not being used currently increases the debugging and profiling time. These codes need to be removed first.

## [Generators](https://www.python.org/dev/peps/pep-0255/)

Python generators are one of the best things to handle large data set processing with limited memory usage during runtime. [[Reference](https://stackoverflow.com/a/231855/5014656)]

## [Context managers](http://book.pythontips.com/en/latest/context_managers.html)

Context managers allow you to allocate and release resources precisely when you want to. Opening files and closing automatically can be done with the help of these. No need to explicitly close the files.

## [Multiprocessing](https://pypi.org/project/multiprocessing/)

Multiprocessing module in python can be used to run independent processes in parallel. It can be used for utilizing the CPU of the server.

## Using __slots__ operator [[Reference](https://stackoverflow.com/a/8117194/5014656)]

* Object attributes of a class are stored in __dict__.

* Dictionaries are used for high access speed, O(1). However, in most cases __dict__ becomes 1/3rd empty.

```
from sys import getsizeof as gs
 
d_obj = {}
print(gs(d_obj)) *# print the default size*
*# 280*
 
d_obj = {k: v for k, v in enumerate(range(5))}
print(gs(d_obj)) *# default size continues till this*
*# 280*
 
d_obj = {k: v for k, v in enumerate(range(6))}
*# a new set of memory allocation begin where most of the memory are unutilized*
print(gs(d_obj))
*# 1048*
```


Details of other data types can be found below: [[Source](https://stackoverflow.com/a/30316760/5014656)]

```
Bytes  type        empty + scaling notes
24     int         NA
28     long        NA
37     str         + 1 byte per additional character
52     unicode     + 4 bytes per additional character
56     tuple       + 8 bytes per additional item
72     list        + 32 for first, 8 for each additional
232    set         sixth item increases to 744; 22nd, 2280; 86th, 8424
280    dict        sixth item increases to 1048; 22nd, 3352; 86th, 12568 *
64     class inst  has a __dict__ attr, same scaling as dict above
16     __slots__   class with slots has no dict, seems to store in 
                   mutable tuple-like structure.
120    func def    doesn't include default args and other attrs
904    class def   has a proxy __dict__ structure for class attrs
104    old class   makes sense, less stuff, has real dict though.
```


* __slots__ can be used to get rid of these free memory spaces. Here you can not add more attributes once you define __slots__. By this way, you can reduce the memory usage of the object(s).

## Using Pythonic code

There are many cases where using Pythonic codes improve the performance. Some examples are:

1. Using list/generator expressions over for loop [[Reference](https://stackoverflow.com/q/1247486/5014656)][[Reference](http://www.u.arizona.edu/~erdmann/mse350/topics/list_comprehensions.html)]

1. Using [short-circuit](https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not) operator to avoid additional if-else condition check. [[Reference](https://stackoverflow.com/a/14892812/5014656)]

1. Using Python libraries than re-inventing the wheel

1. Using local function variables instead of global variables [[Reference](https://stackoverflow.com/q/12397984/5014656)][[Reference](https://www.python-course.eu/python3_global_vs_local_variables.php)]

1. Using decorators to fetch the time taken on function level and disabling them in prod run

1. Converting numeric intensive operations to Numpy

1. Using [enumerate](https://stackoverflow.com/q/22171558/5014656) instead of maintaining a separate count for indexes

## Pre-loading memory/time intensive operations

There are memory and time intensive operations which can be done during importing the libraries before running the server. In this way, the query processing time decreases.

## Modularization

Modularization is always good. It is necessary for a maintainable code, quickly editable for ever-changing business requirements. If a function is called for more than 20 times then you each second saved multiplies that many times saved.

## Disabling print statements

A separate function is used to print the operations. However, those can be disabled during the production run in a single flag change. Now the program can [run as a service](https://nssm.cc/usage) and log files can be used for operation monitoring.

## Technology stacks for performance

* [Nginx](https://nginx.org/) for load balance between multiple servers

* [Redis](https://redis.io/) as the cache manager

* [RabbitMQ ](https://www.rabbitmq.com/)or [Apache Kafka ](https://kafka.apache.org/)for job queue management

* [CherryPy](https://github.com/cherrypy/cheroot) as WSGI server in Windows OS

* [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/) in Linux OS

* [Flask ](https://github.com/pallets/flask)for REST API development

## Conclusion

After implementing the above methods the concurrency user support has been increased more than 10 times. With implementing all the methods described here we target to increase the concurrency support by at least 100 times.

## Additional optimization tips and references:

* [Python](https://wiki.python.org/moin/PythonSpeed/PerformanceTips)

* [StackOverflow](https://stackoverflow.com/questions/7165465/optimizing-python-code)

* [Geekforgeeks](https://www.geeksforgeeks.org/optimization-tips-python-code/)

* [System design](https://github.com/donnemartin/system-design-primer)

Thank you for your time.