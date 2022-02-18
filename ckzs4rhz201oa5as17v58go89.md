## JP Morgan & Chase interview experience

This is a part of my [job interviews series](https://blog.soumendrak.com/series/job-interview). 

## Background

- Year: September 2018
- Campus: [JPMC Office, ORR, Bengaluru](https://goo.gl/maps/3beQjwthP5QJaadCA) 
- Position: Senior Python developer
- Company: [JPMC India](https://www.jpmorgan.com/IN/en/about-us)


On the ORR (outer ring road), JPMC has a big office. It took me some time to reach the designated building. I used to stay at BTM during that time.

## First round of discussion

Before the physical discussion, I had a telephonic round.
It was delayed by 1 hour due to some availability issues.


1. Entity extraction how you did in {a client} and what were the main challenges involved.
  - Date extraction on different date formats was a challenge. I had used multiple libraries plus my own self made rule-based logic to finally make it work. 
2. `classmethod` vs `staticmethod`; where and how did you implement it?
  - You may checkout this [StackOverflow answer](https://stackoverflow.com/a/1669524/5014656).
3. `input: [1,2,3,4,5,6]` and `output: [[1,2], [3,4], [5,6]]` how can you get the output with the help of a list expression?
```python
>>> input_list = [1,2,3,4,5,6]
>>> output_list = [input_list[index:index+2] for index in range(0, len(input_list), 2)]
>>> print(output_list)
[[1, 2], [3, 4], [5, 6]]
```
4. Different types of Object-oriented programming components in Python:
  1. Inheritance
  2. Polymorphism
  3. Abstraction &
  4. Encapsulation

You may check this [GeekForGeeks page](https://www.geeksforgeeks.org/python-oops-concepts/) for more clarity.

5. What are Decorators and why do you use them?
   - [This StackOverflow answer](https://stackoverflow.com/a/1594484/5014656) is one of the best out there on decorators.
   - At that time, I had used the `timing` decorator to get the execution time of a function/method. For a complex case where I had used `lru_cache` with a timeout limit, check out [this article](https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value).

6. What is a Context manager? When to use Decorator and Context manager?
[This is](https://stackoverflow.com/a/50823556/5014656) one of the best answers out there by [Martijn Pieters](https://stackoverflow.com/users/100297/martijn-pieters.)

> They are completely separate concepts and should not be seen in the same light.

> A decorator lets you augment or replace a function or a class when it is defined. This is far broader than just executing things before or after a function call. Sure, your specific decorator lets you do something just before and after a function call, provided no exception is raised, or you explicitly handle exceptions. But you could also use a decorator to add an attribute to the function object or to update some kind of registry. Or to return something entirely different and ignore the original function. Or to produce a wrapper that manipulates the arguments passed in, or the return value of the original function. A context manager can't do any of those things.

> A context manager on the other hand lets you abstract away [try: ... finally: constructs](https://docs.python.org/3/reference/compound_stmts.html#the-try-statement), in that no matter how the block exits, you get to execute some more code at the end of the block. Even if the block raises an exception, or uses return to exit a function, the context manager `__exit__` method is still going to be called, regardless. A context manager can even suppress any exceptions raised in the block.

> The two concepts are otherwise not related at all. Use decorators when you require to do something to or with functions or classes when they are defined. Use context managers when you want to clean up or take other actions after a block ends.

## Second round of discussion

This was a physical interview. Three, Four people came and started interviewing me. Initially felt a bit nervous about watching so many people. Usually 1 or 2 interviewers I used to face. Anyway, I adapted to the situation calmed myself as needed.

- Balanced bracket
  - This problem is the same as this Leetcode problem called [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/?ref=soumendrak)
- Write a program (pseudocode) to find out the number of vowels in a string
  - same as [this problem with solution](https://www.geeksforgeeks.org/python-count-display-vowels-string/?ref=soumendrak)
- Find out the minimum number in a function without using any compare or max/min operator
  - Check [this](https://stackoverflow.com/a/15150820/5014656) out
- Inside a dictionary, a list is there as a value if I delete the original list, will it affect the dictionary
  - No, the dictionary uses a hash table and keeps its own copy.
  - Therefore, by deleting the original list will not change the value in the dictionary.
- What is GIL and How GIL impacts multi-threading in Python?
  - Check [this article](https://www.guru99.com/python-multithreading-gil-example.html/?ref=soumendrak) for details.
- How is multi-threading separate from multi-processing?
  - Check [this](https://towardsdatascience.com/multithreading-vs-multiprocessing-in-python-3afeb73e105f/?ref=soumendrak) out.
- Run time and compile-time polymorphism; which one is there in Python; give one example of Polymorphism
  - I was unable to answer this. But, you can. Check [this](https://softwareengineering.stackexchange.com/a/335724/183752) out.
- Method overloading and overriding in Polymorphism

![Screenshot 2022-02-18 at 12.59.37 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645169404113/CIGc4UcVo.png)
source: [GeekForGeeks](https://www.geeksforgeeks.org/difference-between-method-overloading-and-method-overriding-in-python/?ref=soumendrak)

- Shallow copying with example
  - There are two types of copy, Shallow and Deepcopy.
For more check out this [RealPython article](https://realpython.com/copying-python-objects/?ref=soumendrak):

  > Making a shallow copy of an object won’t clone child objects. Therefore, the copy is not fully independent of the original.
  >  A deep copy of an object will recursively clone child objects. The clone is fully independent of the original, but creating a deep copy is slower.
  >  You can copy arbitrary objects (including custom classes) with the copy module.

- Design Patterns used in Python
  - This is a very good website for [Design patterns in Python](https://python-patterns.guide/?ref=soumendrak).

- Convert a string to a list without a list() or list expression
  - I could not recall at that time.
  - You can check [this article](https://www.pythonpool.com/convert-string-to-list-python/?ref=soumendrak) on 7 Powerful ways to Convert string to list in Python.

## Result

Not selected for next round. I have been escorted back to the ground floor by one of the interviewers.

## Opinion

- I should have done more programming practice. My pseudocode was not up to the mark.
- 4 interviewers were a bit heavy 😀
- Got to know where was I lacked the skills.
- When I was in COBOL/Mainframe technology during the initial phase of my career, JPMC was one of my dream companies to work on. Anyway, not with Python anymore. I started preparing hard for my next interviews.

I have appeared in 20+ interviews so far. You can check out my [job interview series](https://blog.soumendrak.com/series/job-interview) for the rest of the interviews experiences.

Let me know if you have any further questions. Thank You.
  
Cover pic by [Ravi Shankar](https://www.google.com/maps/contrib/100742079036785929554/photos/@12.6759627,76.7846841,9z/data=!3m1!4b1!4m3!8m2!3m1!1e1)