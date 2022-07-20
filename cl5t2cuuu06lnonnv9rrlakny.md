## Aggregated Code timing in Python

There are many ways to get how much time a function takes in Python. Here is an easy decorator implementation to check how much time a function takes.

```python
from functools import wraps
import time


def timeit(func):
    @wraps(func)
    def timeit_wrapper(*args, **kwargs):
        start_time = time.perf_counter()
        result = func(*args, **kwargs)
        end_time = time.perf_counter()
        total_time = end_time - start_time
        print(f'Function {func.__name__}{args} {kwargs} took {total_time:.4f} seconds')
        return result
    return timeit_wrapper

@timeit
def my_func():
    # do stuff

```

This decorator can be used by decorating a function to get the time spent.
What if you want to aggregate this timing data in a timeframe, like how many times this function has been called, and what the maximum time is taken, for that, we need to use a library called [codetiming](https://github.com/realpython/codetiming).
Here is a sample use case:


```python
# pip install codetiming
# pip install humanfriendly
from codetiming import Timer
from humanfriendly import format_timespan
from loguru import logger


@Timer(name="my_func", text=lambda secs: f"my_func elapsed time: {format_timespan(secs)}")
def my_func():
    ...

def get_aggregated_timings(cls):
    timed_function = "my_func"
    logger.info(
        f"\n{timed_function} count: {Timer.timers.count(timed_function)}\n"
        f"total: {Timer.timers.total(timed_function)}\n"
        f"max: {Timer.timers.max(timed_function)}\n"
        f"min: {Timer.timers.min(timed_function)}\n"
        f"mean: {Timer.timers.mean(timed_function)}\n"
        f"standard deviation: {Timer.timers.stdev(timed_function)}\n"
        f"median: {Timer.timers.median(timed_function)}\n"
    )
    Timer.timers.clear()  # clears all the timer data

```
This will find the aggregated time spent by `my_func`. Let's go through what each one of them will log:

- _count_: Number of times the function has been called.
- _total_: Sum of all the seconds elapsed in the function
- _max_: Maximum time spent on a single flow
- _min_: Minimum time spent on a single flow
- _mean_: The average of all the time spent on that function
- _median_: The median of all elapsed time
- _stdev_: The standard deviation of all elapsed time

At the end `Timer.timers.clear()` clears the data stored In memory and starts from fresh for the next iteration.

Do you want to use an in-memory LRU cache with a timeout, you may check out this article:

%[https://blog.soumendrak.com/cache-heavy-computation-functions-with-a-timeout-value]

I post on Python programming on my Twitter handle, you can follow me [@soumendrak_](https://www.twitter.com/soumendrak_)