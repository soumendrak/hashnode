## Code refactoring

"Refactoring is the process of changing a software system in such a way that it does not alter the external behaviour of the code yet improves its internal structure." What does that exactly mean? I mean, we're not changing how it behaves, so the code's going to work the same way, but we're going to change the inner workings of it a little bit.
 
- We refactor to reduce the complexity to add new features into the code.
- Easy readability
- Easy to enhance and add new features to the code
- Reduce the time it takes to debug an issue
- To improve the understandability of the code for non-authors like new programmers, delivery team or support team.
- To reduce technical debts (a piece of code written in a limited time thinking to redesign it in future)

## When to stop refactoring:

- Taking too much time to refactor which is blocking other dependent applications and priority tasks
- There is limited to no ROI (Return On Investment), which is very addictive for developers.
- Refactoring is not same as redesigning the code. It is easier to start the coding from scratch than to refactor your own or somebody else's code.

### Best practices

#### Importance of test cases

- Unit test cases
- Behavioural/Acceptance cases
- IDE refactoring
- IDE reformatting
- Paired programming

#### Always take a backup before starting the refactoring

- Sometimes the new design may look worse than current
- More time and energy requirement
- Redesigning of the code needed

#### Refactor keeping the future you in mind

#### Style guide

- Use PEP8 style
- Use Pylint and use .pylintrc to configure it as per the project
- Similarly, you can use the optional static type checker mypy with mypy.ini for configuration
- Always write unit test cases pytest with pytest.ini for its configurations
- The code should be highly testable
- Use a good IDE, PyCharm recommended
- Use a code health checker deepsource, sonarlint, etc. are few which helps in finding complexities and many other things around the code
- Use an automatic code formatter like black, autopep8, sort imports, etc.
- Working in small steps and committing the code
- Working in pair or group (pair programming or mob programming)

#### Test cases

- Test cases should be readable.
- Write Explicit Tests (WET)
- Cover the boundary conditions
- Write End to end test cases.
- Start with broader tests and work towards unit testing.
- Test large class or method can by pulling small portions out of it.
- Test every possible decision tree path, i.e. conditional statements
- Different types of tests are there:
  - Deployment
  - Integration
  - Regression
  - Fuzzy
  - UT
  - Linter

### Recognizing issues in the code

#### Comments
- Meaningless comments
  - Comments repeating the same thing as the function/class/statement
- Confusing comments
- Comments used as section label
- Outdated comments
- Comments to help in organize
- Business and Developer using different nomenclature 

#### Too many conditional statements

#### Names of variables, functions or classes

- Write less character-based words, usually by removing the vowels like ctr, cty.
- Using meaningless names like x, y, I, j, process, function, class, processes_data_and_many_other_stuffs
- Giving selfish names: my_cls, our_cntry_func
- Using the built-in keyword as a variable name like id, type

#### Large code bases

- In method/function
- In class
- In a module

#### Negative logic

- Checking conditional statements for negative cases and the positive condition is on the else part.

#### Passing too many parameters on a method/function definition

#### Too many returns on a large function

#### Duplicate code

#### Code smells

#### Zombie code

- Commented code
- Unused/Uncalled code
- Unexecuted code

#### Deliberate attempt to write complex codes

- Skill show off
- Attempt to confuse. 

#### Remove clutter, complexity and cleverness.

## Common refactoring techniques

- Better code sharing
- Break parts into logical pieces
- Improve format and names
- Rename
- Move
  - Moving the right piece of code to the right place
- Extract
  - Replacing constant digits and strings with a constant variable
  - Deduplicating duplicate piece of codes
- Inline
  - Reducing code lines for readability and simplicity
- Improve formatting
- Change signature
- Replace nested conditional with a guard clause
- Push members down
- Replace magic number with symbolic constant
- Apply experience and logic

### Inside refactoring

- Prepare the software for change
- Improve the software
- Clean up the software

<span>Photo by <a href="https://unsplash.com/@omarg247?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Omar Flores</a> on <a href="https://unsplash.com/s/photos/lego?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>