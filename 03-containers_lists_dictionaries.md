Title: Containers: lists and dictionaries
Category: Lessons

Up to this point, we've encountered data types that hold only one piece of data. Python has several data types which can be thought of as containers of other data types. We will cover three:

* lists
* tuples
* dictionaries

In this lesson, we are going to simply demo some of the features of lists, then we will use what we've learned to build some functionality to analyze baby names. The key thing to know is that lists' key feature is ordering items (i.e. first item, second item, third item, etc.) whereas dictionaries' key feature is labeling items.


Concepts
--------
* Lists and tuples:
    * Key features
    * Retrieving data
    * Some useful list operations
    * Revisit string functionality
* Dicts
    * Key features
    * Setting and retrieving data
* Immutable data types


Lists
=====
Lists are a Python container data type who's key feature is ordering the items they contain. Lets take a look at the baby name data.

(execute in the Jupyter notebook to see the first 20 lines of the baby name data).

```
!head -n 20 Most_Popular_Baby_Names__2009-2013.csv
```

This data set is comprised of four columns: year, gender, name, and count. This data is ordered first by year (oldest to newest), then by count. We can construct a list of the five most popular male baby names from 2009:

```python
popular_names = ["DANIEL", "ANTHONY", "ANGEL", "JACOB", "ALEXANDR"]
print popular_names
```

How do we access individual items in the list?

```
popular_names[0]
>>> "DANIEL"
popular_names[2]
>>> "ANGEL"
```

An important thing to note is that the indexing of a python list starts at 0 instead of 1.

We can also index items from the back of the list:

```python
popular_names[-1]
>>> "ALEXANDR"
```

We can also take a part of the list; in Python parlance, a sub-list is called a "slice."

```python
print popular_names[:2]
>>> ["DANIEL", "ANTHONY"]

print popular_names[2:]
>>> ["JACOB", "ALEXANDR"]

print popular_names[1:3]
>>> ["ANTHONY", "ANGEL"]
```

Lists can contain data of different types.

```python
a = [1, "one"]
print a
>>> [1, 'one']
```

Lists with zero elements can be created, and lists can contain other lists (which contain other lists, which contain other lists... with lists all the way down).

```python
empty_list = []
list_o_lists = [empty_list, "three", empty_list, 7.3]
print list_o_lists
>>> [[], 'three', [], 7.3]
```

Lists are a good container object, but their real power is that a list's elements can be changed after its been created, and elements can be added to and removed from an existing list.

Notice that we misspelled "ALEXANDER" when we created this list. We can fix that mistake by reassigning the last element of the list.

```python
popular_names[-1] = "ALEXANDER"
print popular_names
>>> ['DANIEL', 'ANTHONY', 'ANGEL', 'JACOB', 'ALEXANDER']
```

We can also create a list of the next five most popular male baby names in 2009:

```python 
less_popular_names = ["ETHAN", "DAVID", "ANDREW", "MATTHEW", "JOSHUA"]
```

Lets paste the two lists, `popular_names` and `less_popular_names` together to make a list of the top ten most popular baby names. Accomplishing this task is simple: use the `+` operator:

```python
top_names = popular_names + less_popular_names
print top_names
>>> ['DANIEL', 'ANTHONY', 'ANGEL', 'JACOB', 'ALEXANDR', 'ETHAN', 'DAVID', 'ANDREW', 'MATTHEW', 'JOSHUA']
```

What if we wanted to append the 11th most popular name to the end of the list? We could use the `append` list method:

```python
top_names.append("CHRISTOPHER")
print top_names
>>> ['DANIEL', 'ANTHONY', 'ANGEL', 'JACOB', 'ALEXANDR', 'ETHAN', 'DAVID', 'ANDREW', 'MATTHEW', 'JOSHUA', 'CHRISTOPHER']
```

Note that when we called the `append` method, we performed an in-place modification. In other words, there was no assignment of a new variable; `append` changed the `top_names` data "in-place".

Take a moment to reflect on the types of problems for which list functionality might be useful: ordering items, combining lists using the `+` operator, and appending items to the back of a list.

(Have students name some functionality. If a dict might be more useful, say that there's an even better data structure and we'll get to it in just a moment.)


Strings revisited!
==================
There are many cases where data might be contained in a string, but a list would be a better representation, or vice-versa. Now that we've discussed lists, lets revisit strings to see some functionality for switching between the two.


`split`
-------
Consider the first line of the `Most_Popular_Baby_Names__2009-2013.csv` file; it is a string containing a comma-delimited list of column names. How would we convert this string into a list where each column name is an element?

We use the the string's `split` method.

```
column_names_line = "YEAR,GENDER,NAME,COUNT"
column_names = column_names_line.split(",")
print column_names
>>> ['YEAR', 'GENDER', 'NAME', 'COUNT']
```

With no arguments, the `split` method will split a string along any whitespace.

```
example_str = "this string is         to be     used as an example"
example_lst = exmpl_str.split()
print example_lst
>>> ['this', 'string', 'is', 'to', 'be', 'used', 'as', 'an', 'example']
```

So by using a string's `split` method we can create a list from a string.


`join`
------
What if we have a list of items and we want to construct a string? We use the `join` method of the string. Lets say we want to reconstruct the `column_names_line` string from the `column_names` list.

```
recreated_column_names_line = ",".join(column_names)
print recreated_column_names_line
>>> YEAR,GENDER,NAME,COUNT
```

The syntax might seem a little weird, but take a close look at it. We are simply using the literal string `","` and calling its `join` method. We are passing a list to the `join` method, and the `join` method is pasting together a string of all of the items of the list separated by commas.


Common pitfalls: use the right tool for the job
-----------------------------------------------
As mentioned previously, the key feature of a list is ordering items. This feature is great because there are a number of scenarios for which order is exactly what is needed. However, there are also a large number of scenarios for which data needs to be collected together, but there isn't an obvious order. If you find yourself writing code where you are placing items in a list and have to remember their place later, a list probably isn't the data structure you need -- you probably need a dictionary.


Dictionaries
============
The key feature of a Python dictionary is labeling items in the collection. Take a look at the baby name data: it is comprised of four columns. There's no order to this data, and so it doesn't make sense trying to force an arbitrary order. Instead, we could just use a Python dictionary to access each datum using its label (called a "key" in Python parlance).

Consider the first entry corresponding to the name "DANIEL". We can collect all the associated data together in a dictionary like so:

```python
baby = {"year": 2009, "gender": "male", "name": "DANIEL", "count": 3423}
print baby
>>> {'count': 3423, 'gender': ' male', 'name': 'DANIEL', 'year': 2009}
```

Note that the order in which Python prints the `baby` dictionary is not the same as the order in which we entered the data. **This is how Python does dictionaries.** The data is there, but Python won't guarantee any particular order.

To access the data in this dictionary, just call for it by name:

```python
print baby["name"]
>>> DANIEL
print baby["count"]
>>> 3423
```

We can modify the data in the dictionary if we want. Say we wanted to modify `baby` to contain the data for the second most popular name.

```python
baby["name"] = "ANTHONY"
baby["count"] = 3106
print baby
>>> {'count': 3106, 'gender': 'male', 'name': 'ANTHONY', 'year': 2009}
```


Dictionary key restrictions: mutable vs. immutable
--------------------------------------------------
You'll notice that we used strings as keys in the dictionary above. Python allows any *immutable* data type as a dictionary key. Immutable simply means that the data can't be changed once its set. Strings are immutable while lists are not. Dictionaries are also mutable. Its worth mentioning this concept but not belaboring it; for the most part you will use strings as the dictionary key.


Tuples
======
We won't spend much time at all on tuples except to say they are an immutable list. Tuples have important uses, but we won't need them in this course. However, they appear often enough that you should be aware of their existence.

Tuples are created using parentheses instead of square brackets:

```python
tup = (1, 2, 3)
print tup
>>> (1, 2, 3)
```


Exercise
========
Create a list of dictionaries containing the first five entries of the baby name data using dicts similar to the previous example.


Solution
--------
```python
b0 = {"year": 2009,
    "gender": "male",
    "name": "DANIEL",
    "count": 3423,}

b1 = {"year": 2009,
    "gender": "male",
    "name": "ANTHONY",
    "count": 3106,}

b2 = {"year": 2009,
    "gender": "male",
    "name": "ANGEL",
    "count": 3058,}

b3 = {"year": 2009,
    "gender": "male",
    "name": "JACOB",
    "count": 2978,}

b4 = {"year": 2009,
    "gender": "male",
    "name": "ALEXANDER",
    "count": 2905,}

babies = [b0, b1, b2, b3, b4]
```

What's the name of the first (not zeroth) entry in the list?

```python
print babies[1]["name"]
>>> ANTHONY
```

**DO NOT FORGET TO SAVE YOUR JUPYTER NOTEBOOK!!** We will use some of the data in the next lessons.
