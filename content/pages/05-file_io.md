Title: Reading from and writing to files
Category: Lessons

Oftentimes data is located in files and we need to be able to read it into a variable (or several variables). Conversely, data may be in variables and we want to write it to a file. This file I/O (input/output) is another fundamental principle of programming, and many operations in Python share this same pattern. We will explore reading data from and writing data to files in this lesson. Both operations will build on what we just learned about strings, lists, and iteration.


Concepts
--------
* Reading data from a file
* Writing data to a file


Reading data from a file
========================
Up to this point we've been transferring data from the baby name data to Python by copy/pasting by hand. This baby name data file is over 6MB; copying everything by hand clearly is not the way to load this data into memory. Here's the preferred way to open this file and read its contents:


```python
with open("Most_Popular_Baby_Names__2009-2013.csv", "r") as f:
    baby_data = f.readlines()
```

Before we get into the details of the `open` statement, lets see what we created for the `baby_data` variable.

```python
type(baby_data)
>>> list
```

So its a list. How long is it?

```python
print len(baby_data)
>>> 295193
```

295,193. That's a lot!

So it looks like the `readlines` function creates a list of every line in a file (which is exactly what it does).

There's a lot going on with reading data from files, so lets take each component one at a time.

First, the command to open a file is `open` and requires two arguments. The first argument is a string which indicates the file to open. In our case, that file is called `Most_Popular_Baby_Names__2009-2013.csv` and is located in the `dat` directory. Hence, `dat/Most_Popular_Baby_Names__2009-2013.csv`. The second argument tells Python how to open the file. We want to read from the file and so we pass "r" to the `open` function as the second argument.

Second, consider the overall construction; we are using the `with` keyword to open the file, assign the opened file to the variable `f`, then use the corresponding code block to perform the operations on the file. The `with` code block offers us some protection from a common set of problems: when the code in the corresponding code block exits (as a result of finishing or even as a result of raising an exception) Python automatically closes the file. Otherwise, we would have to manually close the file. There are a number of problems that can occur in this scenario that result in a corrupted file and so its best to use the `with` construction.

Finally, lets examine what's in the code block. We are calling the `readlines` method on the file object. This method reads all the lines and returns a list, where each line in the file corresponds to an item in the list. We are assigning that list to the variable `baby_data`.


Cleaning up
-----------
Lets take a look at the first few elements of the `baby_data` list variable.

```python
print baby_data[:10]
>>> ['YEAR,GENDER,NAME,COUNT\n', '2009,MALE,DANIEL,3423\n', '2009,MALE,ANTHONY,3106\n', '2009,MALE,ANGEL,3058\n', '2009,MALE,JACOB,2978\n', '2009,MALE,ALEXANDER,2905\n', '2009,MALE,ETHAN,2687\n', '2009,MALE,DAVID,2648\n', '2009,MALE,ANDREW,2605\n', '2009,MALE,MATTHEW,2435\n']
```

Each line has `\n` at the end of it. The `\n` is the "newline" character which indicates a new line. It makes sense that each line has a newline at the end of it, but we don't want this character in our data. We can use a `for` loop and the string `strip` method to get rid of it.

```python
# Initialize list into which all data will go
baby_data = []

with open("Most_Popular_Baby_Names__2009-2013.csv", "r") as f:
    for line in f:
        baby_data.append(line.strip())

# Now take a look at the first few lines
print baby_data[:10]
>>> ['YEAR,GENDER,NAME,COUNT', '2009,MALE,DANIEL,3423', '2009,MALE,ANTHONY,3106', '2009,MALE,ANGEL,3058', '2009,MALE,JACOB,2978', '2009,MALE,ALEXANDER,2905', '2009,MALE,ETHAN,2687', '2009,MALE,DAVID,2648', '2009,MALE,ANDREW,2605', '2009,MALE,MATTHEW,2435']
```

In this example, we have two code blocks: one for the `with` statement and the other associated with the `for` loop. We opened the file using the `with` statement and then iterated over all of the lines of the file using the `for` loop. For each line, we `strip`ped off the whitespace, including the newline character. We appended these stripped lines to a list.


Writing data to a file
======================
What if we wanted to extract the baby data from just the year 2011 and write it to another file? There's an easy way to do this analysis that we'll examine in the next lesson, but for now I've examined this baby data and found that the data for the year 2011 starts on line 120460 and ends on line 179044 of the file. With this information we can take a slice from the `baby_data` list and write it to a file. Lets start with the simplest possible example: just writing the column information to the new file:


```python
with open("2011_baby_data.csv", "w") as f:
    f.write(baby_data[0])
```

The construction to write data to a file is, not surprisingly, similar to reading data from a file. Lets examine the differences.

First, we open the file for writing by passing `"w"` to the `open` command. Next, we use the file's `write` method to write data to the file.

Lets check the file to see what's been written.

(Open the file in the Jupyter notebook and check it out).

Now lets write the rest of the data to the file. In order to successfully perform this write, we will need to iterate over the slice of `baby_data` and write one line at a time to the file.

```python
start_line = 120460
end_line = 179044

with open("2011_baby_data.csv", "w") as f:
    for line in baby_data[start_line:end_line]:
        f.write(line + "\n") # Spoiler! we need newlines in the file.
```


Alternative: `join` command
---------------------------
Instead of using the `for` loop, we could just construct the string we want using the `join` method and write the string to a file.

```python
data_2011 = "\n".join(baby_data[start_line:end_line])

with open("2011_baby_data.csv", "w") as f:
    f.write(data_2011)
```

(Perhaps go through ways to screw it up).


Pitfalls
--------
* Data has to be text in order to be written to files.
* If you want a newline, you have to put a newline character.
