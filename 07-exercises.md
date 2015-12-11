Title: Putting everything together
Category: Lessons

At this point, we've covered many topics including:

* variables
* strings (and some string methods)
* numbers
* lists
* dictionaries
* `for` loop
* Indentation and code blocks in Python
* reading/writing files
* `if` statements
* functions

We are going to spend the remainder of this workshop working through a few examples to deal with the baby name data and create a few visualizations.


Example problems
----------------
The first exercise might be too tough for everyone to complete by themselves. We should walk through it, but the solution should be driven by suggestions from the class.

1. Create a function that reads the data from the file and create a list of dictionaries.
2. Determine the number of babies born in 2012.
3. Determine the number of female babies born in 2012.
4. Determine the number of female babies born in 2012 with a five-letter name.
5. Determine the number of babies whos name starts with the letter "J".
6. How many babies have four letter names?
7. How many female babies have names that start with "L"?
8. How many babies were born in 2010?
9. What's the ratio of male babies to female babies in 2012?
10. Determine the number of babies born each year (for data visualization in the next lesson).


Read data into list of dicts
----------------------------
```python
filename = "dat/Most_Popular_Baby_Names__2009-2013.csv"

with open(filename, "r") as f:

    # Just read the first line because we know its the column descriptions.
    cols = f.readline()
    # Strip off any whitespace that might be lurking at the end.
    cols = cols.strip()
    
    # Read everything else into a string.
    dat = f.read()
    
    # There is some whitespace lurking at the end of this string, so get rid of it.
    dat = dat.strip()

col_names = cols.split(",")
baby_lines = dat.split("\n")

babies = []

for baby_line in baby_lines:
    baby_dat = baby_line.split(",")

    baby = {"year": baby_dat[0],
        "gender": baby_dat[1],
        "name": baby_dat[2],
        "count": baby_dat[3]}

    babies.append(baby)
```
