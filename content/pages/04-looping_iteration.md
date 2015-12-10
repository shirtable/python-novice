Title: Looping and iteration
Category: Lessons

One of the best things about computers is that you can instruct them to perform the same action over and over again. This repitition is commonly called "looping" and is more generally called "iteration." Iteration in Python is a fundamental building block of the language and is strongly tied to container data types.


Concepts
--------
* `for` loop
* Indentation and code blocks in Python


The Python `for` loop
=====================
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
Notice that the code block immediately following the `for` loop call is indented. This indentation serves two purposes. First, this indentation is how Python knows what is part of the body of the `for` loop: every line that is indented to the same extent is understood to be part of the `for` loop body. To write code after the `for` loop, simply write code with no indentation.

The second purpose of indentation is to promote code readability. It turns out that writing code for a machine to read and execute is much easier than writing code for another person to read. You should also note that "another person" could mean you, six months from now. Indenting code makes the code much more readable than having all the lines at the same level of indentation.

Another important aspect of indentation in Python is consistency. The Python interpreter does not care if you use spaces or tabs to indicate the body of a loop, nor does it care how many you use as long as you use the same number. People have determined that the convention is to use **four** space characters for an indentation. Please follow this convention and do not use tabs.
