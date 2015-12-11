Title: Controlling program flow and functions
Category: Lessons

Oftentimes, your program will have to execute different behaviors depending on some condition. In this lesson, we will learn about `if` statemments to perform different actions depending on what year the babies were born.


Concepts
--------
* `if` statements
* Encapsulating functionality using functions


Making a decision: the `if` statement
=====================================
In the last example, we wrote the 2011 baby data to a file based on the fact I told you that lines 120460 to 179044 were the 2011 data. Can't the computer do this kind of thing for us? Using an `if` statement, it can.

Lets rework that last example by creating a variable called `babies_2011` that contains a list of the baby data from 2011.

```python
babies_2011 = []

for baby_datum in baby_data:
    if baby_datum.startswith("2011"):
        babies_2011.append(baby_datum)
```

Using the `elif` statement, we can select from more than a single choice. Lets say we wanted to create lists of the 2011 babies *and* the 2012 names. The example is nearly identical.

```python
babies_2011 = []
babies_2012 = []

for baby_datum in baby_data:
    if baby_datum.startswith("2011"):
        babies_2011.append(baby_datum)
    elif baby_datum.startswith("2012"):
        babies_2012.append(baby_datum)
```

What if we wanted to collect all of the lines that weren't from 2011 or 2012? We use the `else` statement at the end of a Python `if` sequence:

```python
babies_2011 = []
babies_2012 = []
babies_other = []

for baby_datum in baby_data:
    if baby_datum.startswith("2011"):
        babies_2011.append(baby_datum)
    elif baby_datum.startswith("2012"):
        babies_2012.append(baby_datum)
    else:
        babies_other.append(baby_datum)
```

There's no condition associated with the `else` statement since it corresponds to "everything else."


Functions
---------
We could write conditions for any of the years in which babies were born using `if` statements, but this approach quickly gets tedious -- what if we had baby name data for all years between 1900 and 2013? By writing a function, we can abstract this functionality to simply ask for the year and get the corresponding entries.

```python
def filter_year(baby_data, year):
    """
    Return a list of baby data for a given year
    """
    filtered_baby_data = []

    for baby_datum in baby_data:
        if baby_datum.startswith(year):
            filtered_baby_data.append(baby_datum)

    return filtered_baby_data

babies_2011 = filter_year(baby_data, "2011")
```

To create a function, we start with the `def` keyword followed by the function call signature. The call signature is the name of the function with any arguments the function might require. In our case, we are passing two items to the function: the `baby_data` we want to parse and the `year` on which we want to filter.

The overall structure of the function definition should look familiar: we terminate the function call signature using a colon, and we include the function's code within an indented code block. The code for this function is almost identical to what we wrote before, we've just abstracted some of the functionality with the variables that were passed to the function.

You will note that immediately following the function call signature there's some text enclosed by three double-quote characters (`"""`). This text is very special in python and is called the "docstring." Python programmers use docstrings to document the functionality of their functions. This text is not like a comment; Python actually carries the docstring around with the function. We can access docstrings from the ipython-notebook using the magic `?` following the function name.

(Demonstrate example of the `filter_year` function).

Also note the `return` statement at the bottom of the function. This statement tells python to return the specified data back to whoever called it and exit. Your function does not need a `return` statement, but you won't get any data out if you don't have it.


Better example: list of dicts
-----------------------------
Lets face it, the function above could be a lot better. Here we are constrained by the quality of our data: we are dealing with a list of strings instead of a list of dicts. On the other hand, we have the toy data `babies` which is a list of dicts containing five baby names and associated information. Lets write a more general function that can filter this data on any field.

```python
def filter_babies(babies, key, value):
    """
    Return baby data where key matches the value
    """
    filtered_babies = []
    for baby in babies:
        if baby[key] = value:
            filtered_babies.append(baby)

    return baby
```

This new function allows us to filter on any of the keys of the baby dict. The following demos won't be super interesting because of the limited amount of data we have, but hopefully you will see the value in this function over the prior function.

```python
# Find all babies born in 2011
babies_2011 = filter_babies(babies, "year", 2011)

# Find all entries with name ALEXSANDER
babies_alexandar = filter_babies(babies, "name", "ALEXANDAR")
```


One final thing that's important to talk about is data scope. The variables you create in a code block stay within that code block. Once the block ends, the data disappears unless it is `return`ed.

NEED TO TALK ABOUT GLOBAL VARIABLES HERE.
