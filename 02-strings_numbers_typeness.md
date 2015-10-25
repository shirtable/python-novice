Strings, numbers, and typeness
==============================
In this lesson we are going to look more closely at strings and numbers in Python. In so doing we are going to encounter the concept of "type." We will also encounter Python's conception of object-oriented programming.


Concepts
--------
* Strings
* Numbers (int, float)
* Type
* Python and Object-Oriented Programming (OOP)


Strings
-------
So far we've seen what happens when we `print` strings, but strings have much more functionality.


Print multiple strings
----------------------
```python
beginning = "2"
end = "Chainz"
print beginning, end
>>> 2 Chainz
```

Combine (concatenate) strings
-----------------------------
```python
rapper = beginning + end
print rapper
>>> 2Chainz
```

Note that there's no space between `2` and `Chainz`. When combining strings as shown above, Python simply sticks the beginning of the second string to the end of the first string. To get a space, you would have to explicitly add it.

```python
rapper = beginning + " " + end
print rapper
>>> 2 Chainz
```

So you see that the `rapper` variable is made up of the string from `beginning`, a string containing a single space character, and the string from `end`.


Some string functionality
-------------------------
```python
# Print all uppercase string.
print rapper.upper()
>>> 2 CHAINZ

# Print all lowercase string.
print rapper.lower()
>>> 2 chainz

# Count the number of characters in the string.
print len(rapper)
>>> 8
```


Numbers
-------
Python understands several different kinds of numbers; the two most common are integers (`int`) and floating-point (`float`). You can think of these as integers and decimals. There are good computer science reasons why these two kinds of numbers are distinct.

```python
i = 12
f_1 = 12.27
f_2 = 12.

type(i)
>>> int
type(f_1)
>>> float
type(f_2)
>>> float
```

All kinds of mathematical operations are available on numbers: addition, subtraction, multiplication, division, etc.


Typeness
--------
We've learned that we can combine two strings with the `+` operator, and that we can add two numbers (either int and/or floats) with the same `+` operator. What happens if we try to create 2 Chaniz's name with an int and string?

```python
beginning = "2"
dos = 2
end = "Chainz"

# We did this before and it should work
rapper = beginning + end
print rapper
>>> 2Chainz

# Now try with an int
rapper = dos + end
>>> TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

* Why did the first thing work?
* Why did the second thing fail?

(COMMENTS ABOUT TYPE).

Sometimes we can change the type.

```python
type(dos)
>>> int

str_dos = str(dos)
type(str_dos)
>>> str

print str_dos
>>> 2

rapper = str_dos + end
print rapper
>>> 2Chainz

# The following also works and is slightly more concise
rapper = str(dos) + end
print rapper
>>> 2Chainz

# floats can also be converted to strings
pi = 3.14
str_pi = str(pi)

type(pi)
>>> float
type(str_pi)
>>> str
```

We are able to convert ints and floats to strings because there's an unambiguous way to represent each as strings. In certain cases, we can convert strings to floats or ints.

```python
print beginning
>>> 2
type(beginning)
>>> str

int_beginning = int(beginning)
type(int_beginning)
>>> int

fl_beginning = float(beginning)
type(fl_beginning)
>>> float

str_human_body_temp = "98.6"

fl_hbt = float(str_human_body_temp)
type(fl_hbt)
>>> float

int_hbt = int(str_human_body_temp)
>>> ValueError: invalid literal for int() with base 10: '98.6'

# What about converting a float to an int?
int_hbt = int(fl_hbt)
type(int_hbt)
>>> int
print int_hbt
>>> 98
```

We just went through a number of examples and there's no need for you to memorize all of this stuff. The general principle is "type". Type, like variables, is a fundamental idea in programming. Every kind of data has a particular type. So far, we've seen three: `str`, `int`, and `float`. In certain cases, data of one type can be converted to another.

The idea of type brings us to another idea this is fundamental to Python in particular, but not necessarily other programming lanugages: the idea of object-orientation. There's a lot that can be said about OOP, but the most important things to understand are:

* An object combines data with functionality.
* Everything in Python is an object. Everything.

We've already seen some examples of the first point when we were dealing with strings:

```python
jrs = "Joshua Ryan Smith"
print jrs
>>> Joshua Ryan Smith

print jrs.upper()
>>> JOSHUA RYAN SMITH

print jrs.lower()
>>> joshua ryan smith
```

The variable `jrs` contains the string `"Joshua Ryan Smith"`. Since `jrs` is a string, it comes with some built-in functionality; two examples are the `upper` and `lower` methods which return the string in all uppercase and all lowercase, respectively. The names of all of the functionality of an object can be seen using the `dir` function.

```python
dir(jrs)
>>> ['__add__',
 '__class__',
 '__contains__',
 '__delattr__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__getitem__',
 '__getnewargs__',
 '__getslice__',
 '__gt__',
 '__hash__',
 '__init__',
 '__le__',
 '__len__',
 '__lt__',
 '__mod__',
 '__mul__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__rmod__',
 '__rmul__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 '_formatter_field_name_split',
 '_formatter_parser',
 'capitalize',
 'center',
 'count',
 'decode',
 'encode',
 'endswith',
 'expandtabs',
 'find',
 'format',
 'index',
 'isalnum',
 'isalpha',
 'isdigit',
 'islower',
 'isspace',
 'istitle',
 'isupper',
 'join',
 'ljust',
 'lower',
 'lstrip',
 'partition',
 'replace',
 'rfind',
 'rindex',
 'rjust',
 'rpartition',
 'rsplit',
 'rstrip',
 'split',
 'splitlines',
 'startswith',
 'strip',
 'swapcase',
 'title',
 'translate',
 'upper',
 'zfill']
```

In fact, the functionality to combine strings using `+` is listed if you know where to look; its the `__add__` method. This method is specially named so that the python interpreter knows to call it when it sees `+` combining two strings.
