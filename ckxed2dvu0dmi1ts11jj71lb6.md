## Sony interview questions

This is a part of my [job interviews series](https://blog.soumendrak.com/series/job-interview). 

## Background

- Years of Experience: 4.5 years
- Relevant Python experience: 2 years
- Year: August 2016
- Campus: <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d8856.719090625493!2d77.6950257531794!3d12.92967291303898!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3bae13a90bec84b9%3A0x4c7a4c223ee2dcf3!2sSONY%20India%20Software%20Centre%20Pvt%20Ltd!5e0!3m2!1sen!2sin!4v1639751642803!5m2!1sen!2sin" width="400" height="300" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
- Position: Python developer
- Company: [Sony India Software](https://www.sonyindiasoftware.co.in/)

## Interview discussions

I have mentioned the main questions and the ladder questions around that question under it.

### First phase

1. What are `Decorators` and why do we use them?
  - [Real Python](https://realpython.com/primer-on-python-decorators/)
2. Multiprocessing and Multithreading in Python
  - ![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1639971044607/VsAxBhqPh.png) source: [Lei Mao's blog](https://leimao.github.io/blog/Python-Concurrency-High-Level/)

3. In multiprocessing, discussed parent, child relation concept.
4. How a parent will know that a process's invoker has been killed?
  - [*SIGCHLD* concept in C](https://stackoverflow.com/questions/55483202/how-can-a-parent-process-find-out-if-the-child-process-was-terminated)
5. Differences between `__repr__` and `__str__` in Python?
  > the goal of `__repr__` is to be unambiguous and `__str__` is to be readable.
    
  Checkout further good answers on [stackoverflow](https://stackoverflow.com/a/19597196/5014656)
6. How to implement stack and queue in Python?

  - Stack (LIFO)
```python
class Stack:

    def __init__(self):
        self.stack = []

    def pop(self):
        if len(self.stack) < 1:
            return None
        return self.stack.pop()

    def push(self, item):
        self.stack.append(item)

    def size(self):
        return len(self.stack)
```

  - Queue (FIFO)
```python
class Queue:

    def __init__(self):
        self.queue = []

    def enqueue(self, item):
        self.queue.append(item)

    def dequeue(self):
        if len(self.queue) < 1:
            return None
        return self.queue.pop(0)

    def size(self):
        return len(self.queue)
```
  - [reference](https://stackabuse.com/stacks-and-queues-in-python/)

7. How does Python interprets?
  - [How does Python work](https://towardsdatascience.com/how-does-python-work-6f21fd197888)
8. How to run a module if I delete its `*.py` file, but the `*.pyc` file is present?
  - Yes, we can run the `.pyc` file directly without `*.py` file.
9. How does **memory management** happen in Python?
  - [Real python blog on memory management](https://realpython.com/python-memory-management/)
10. How to know what are the attributes/methods present of a class or object?
  - using `dir`
11. Have you worked on SQLAlchemy?
12. Write a program to write:
  - 'd' in place of 'a', 
  - 'e' in place of 'b',
  ..
  ..
  ..
  - 'a' in place of 'w' with proper unit test cases.
	
### Second phase

Did not qualify. Failed in Unit test writing.

## Result

**Not qualified**

## Analysis

### What went well

What went well and I should keep doing further:

- The interview discussion went well.
- I was responding calmly with a pause after the question, framing my answer in a structured way with keywords, which the other person want to hear.

### Need improvement

What did not go well or I have not planned for and I need to improve:

- I need to improve on live coding. Though the problem was not tough, due to lack of practice on coding when someone is watching you code every letter made me nervous.
- I need to improve my Unit testing skills; learn `pytest`.

I have appeared in 20+ interviews so far. You can check out my [job interview series](https://blog.soumendrak.com/series/job-interview) for the rest of the interviews experiences.

Let me know if you have any further questions. Thank You.
