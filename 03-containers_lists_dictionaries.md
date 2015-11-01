Containers: lists and dictionaries
==================================
Up to this point, we've encountered data types that hold only one piece of data. Python has several data types which can be thought of as containers of several data types. We will cover three:

* lists
* tuples
* dictionaries


Lists
-----
Lists are a Python container data type who's key feature is ordering the items they contain. 

```python
fruit = ["apple", "pineapple", "banana", "pear"]
fruit[0]
>>> apple
fruit[2]
>>> banana
```

An important thing to note is that the indexing of a python list starts at 0 instead of 1.

We can also index items from the back of the list:

```python
fruit[-1]
>>> "pear"
```

We can also take a part of the list; in Python parlance, a sub-list is called a "slice."

```python
print fruit[:2]
>>> ['apple', 'pineapple']

print fruit[2:]
>>> ['banana', 'pear']

print fruit[1:3]
>>> ['pineapple', 'banana']
```

Lists can contain data of different types.

```python
a = [1, "one"]
print a
>>> [1, 'one']
```

Lists with zero elements can be created, and lists can contain other lists (which contain other lists, which contain other lists... lists all the way down).

```python
empty = []
list_o_lists = [empty, "three", empty, 7.3]
print list_o_lists
>>> [[], 'three', [], 7.3]
```

Lists are a good container object, but their real power is that a list's elements can be changed after its been created, and elements can be added to and removed from an existing list.

```python
# Change list element after the list has been created.

# Concatenate two lists

# Append
# Extend

# Push
# Pop
```


Dictionaries
------------
Lists key feature is that the data contained in a list is ordered. If you find yourself writing code where you are placing items in a list and have to remember their place later, a list probably isn't the data structure you need.
