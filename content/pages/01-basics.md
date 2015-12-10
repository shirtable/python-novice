Title: The absolute basics of python
Category: Lessons

In this lesson we will learn some very basic functionality of python.

Concepts
--------
* Human-computer interaction via `print` command
* Entering python commands into the interpreter shell (or ipython notebook)
* Variables
* Code comments


Hello world!
------------
The first thing we will do is write a very simple program to print the message "Hello world!" to the screen. This program is so simple in Python it requires just a single line:

```python
print "Hello world!"
>>> Hello world!
```

This example seems trivial, but in fact it exposes a number of concepts, the details of all of which we will explore during this workshop. First, we've demonstrated that we can write code that emits a message to the user. Your computer does this all the time. Second, we've called the `print` function; this function takes an argument and prints the argument to the user's screen. The argument we passed to `print` was the string `"Hello world"`.

Lets see if we can print other things.

```python
print 4 + 2
>>> 6
print 4 * 2
>>> 8
print 4 / 2
>>> 2
```

Great! Python can do simple arithmatic as well as print text to the screen.

Its worth noting that there are two steps to what we are doing:

1. Typing code into the ipython notebook
2. Executing the code

Its important to note that when we tell the Python interpreter to execute code, Python reads each line from top to bottom and executes each.


Variables
---------
A key concept in any type of programming is the idea of a varaible. A variable is a reference to some data. Up to this point we have not been using variables, we have been using literal values of strings and numbers. For example, we've seen the literal string `"Hello world"` and the integers `2`, `4`, `6`, and `8`. With variables we can abstract functionality from literal values. 

Lets look at some examples using the baby name data. We can use the data.gov browser to preview the data, but we can only get the first 1000 lines. This file isn't too big (6.1M), but it contains 295,194 lines.

```python
first_baby_name = "Daniel"
print first_baby_name
>>> Daniel

# Number of male babies with the three most popular names
first_baby_number = 3423
second_baby_number = 3106
third_baby_number = 3058

top_three_names = first_baby_number + second_baby_number + third_baby_number
print top_three_names
>>> 9587
```

In this example, we assign values to variables. In the first part of the example, we created a variable called `first_baby_name` to hold the string `"Daniel"`. When we pass the `first_baby_name` variable to the `print` function, `print` prints the contents of that variable.

In the second part of the example, we assigned the integer `3423` to the variable `first_baby_number`, the integer `3106` to the variable `second_baby_number`, and the integer `3058` to the variable `third_baby_number`. We summed the three variables and assigned the result to the variable `top_three_names`. Again, the `print` function simply prints the contents of the `top_three_names` variable (as opposed to its name).

Once variables have been set, they can be rewritten. This behavior can be confusing and zings even the most experienced programmers from time to time. Let's look at an example.

```python
length = 4
width = 2
area = length * width
print area
>>> 8

# Change value of `length` variable.
length = 6
print length
>>> 6

# Does the value of `area` change?
print area
>>> 8
```

In the first part of the example we set the `length` variable to the value `4` but changed it to `6` in the second part of the example. The value of `area` was set before we changed the value of `length`, so it doesn't change.


Special variable names
----------------------
There are rules to naming variables.

(PICTURE OF WALTER SOBCHACK)

Variables cannot have the following names; they already mean things in Python and using them would cause massive confusion:

    False      class      finally    is         return
    None       continue   for        lambda     try
    True       def        from       nonlocal   while
    and        del        global     not        with
    as         elif       if         or         yield
    assert     else       import     pass
    break      except     in         raise

Your variable *can* include one of those names, though:

```python
try_this = "it works!"
print try_this
>>> it works!
```

Additionally, variables

* Can only contain letters, numbers, and underscores (thus no minus signs: "-").
* Cannot start with a number (but can *contain* numbers).
* Are case-sensitive.

```python
two_chainz = "no problem"
_fine_but = "leading underscores are legal, but they have a special meaning"


# The following will all raise exceptions:
2_chainz = "not ok"
wont-work = "nope."
```


Comments
--------
Comments are text in code, but which isn't executed by the Python interpreter. Comments begin with the `#` character (pound, not hashtag). As soon as the Python interpreter encouters the comment character on a line, it ignores the rest of the line. Comments are a great way to document your code as well as temporarily switch off certain lines from executing.


Conclusion
==========
We have demonstrated some basic functionality of Python by interacting with the Python interpreter via the jupyter notebook and `print` statements. We've also encountered variables.