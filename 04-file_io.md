Reading from and writing to files
=================================
Oftentimes data is located in files and we need to be able to read it into a variable. Additionally, many times data is in a variable in memory and we want to write it to a file. We will learn how to do both in this lesson.

Reading data from a file
------------------------
```python
with open("input.txt", "r") as f:
    a = f.read()
```


Writing data to a file
----------------------
```python
a = "Some text"

with open("output.txt", "w") as f:
    f.write(a)
```

There are several important things to note about these examples. First, file operations have special requirements which are different from in-memory operations. Up to this point, we've created variables in memory, retrieved them, and manipulated that data. These types of operations only require the Python interpreter to interact with the computer's memory. Reading and writing to a disk requires more from the computer's OS. These special requirements explain the different construction of the read and write commands.

Lets consider the code to read data from a file. This code is organized into what's called a "code block." The code block in the `read` example is comprised of two lines; the first line is terminated by a colon, and the second line is indented with four spaces. 
