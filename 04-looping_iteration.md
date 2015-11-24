Looping and iteration
=====================
One of the best things about computers is that you can instruct them to perform the same action over and over again. This repitition is commonly called "looping" and is more generally called "iteration." Iteration in Python is a fundamental building block of the language and is strongly tied to container data types.


Concepts
--------
* `for` loop
* `while` loop
* Indentation and code blocks in Python


The Python `for` loop
---------------------
One of the most basic types of Python loop is the `for` loop. In this loop, Python executes some code for each item in a container. Lets consider the first five baby names in the baby name list.

```python
baby_names = ["DANIEL", "ANTHONY", "ANGEL", "JACOB", "ALEXANDER"]

for name in baby_names:
    print name
```

The `for` loop above iterates over each item in the `baby_names` list. Each element of the list is printed. The loop terminates after it finishes with the last element of the list.

The `for` loop above consists of two components: the `for` loop call and the `for` loop body. In order of appearance, the call consists of the `for` command, a variable used to store an element of the list, the `in` command and the list over which the iteration will be executed. The body consists of any arbitrary code. In this case, we are just printing the element of the list.

Simply printing items in a list isn't terribly useful. We could use a `for` loop with a list to determine the total number of babies with the top five names.

```python
baby_numbers = [3423, 3106, 3058, 2978, 2905]

total_baby_numbers = 0

for baby_number in baby_numbers:
    total_baby_numbers = total_baby_numbers + baby_number

print total_baby_numbers
>>> 15470
```

So far we've applied `for` loops to iterate over lists. Many other container types are iterable. Here's a slightly contrived example to demonstrate: consider a dictionary containing data corresponding to the first entry in the baby name data table.

```python
baby_entry = {"year": 2009, "gender": "MALE", "name": "DANIEL", "count":  3423}

for item in baby_entry:
    print item
```

So executing a `for` loop over a dictionary simply iterates over the keys of the dictionary in arbitrary order (because there's no order to a Python dictionary).

Lets look at one more example. One way of structuring the baby name data would be as a list of dictionaries. In fact, this structure is generally pretty useful and can be found in many cases. (NOTE: We should have an example where we structure this data in this way.)


Indentation
-----------
Here we need to talk about not just practical, but philosophical as well.
