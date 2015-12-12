Title: Data visualization and external modules
Category: Lessons

Now that we've done some python programming, lets do some data visualization.


Concepts
--------
* Leveraging code in modules via `import`
* `matplotlib`


`matplotlib`
============
One of the best things about Python is that it is used and developed by a huge number of people. Some of these people write code to do useful things and give the code away for free, posting it on particular sites so that you can use what they've written without writing it yourself.

The `matplotlib` package is such code; it is the go-to package for generating plots from data. Lets make a plot of number of babies vs. year.

First, we have to create a list of the number of babies each year. We can use the `babies` list of dicts from before as well as the `filter_babies` function.

```python
babies_per_year = []

# The following list is short, so we'll key it in by hand.
years = [2009, 2010, 2011, 2012, 2013]

for year in years:
    babies_for_year = filter_babies(babies, year)

    num_babies = 0
    for baby in babies_for_year:
        num_babies = num_babies + baby["count"]

    babies_per_year.append(num_babies)
```

Next, we need to initialize the matplotlib environment in the Jupyter notebook.

```
%matplotlib inline
```

This command is a Jupyter command and *not* a general Python command. It is simply to tell the Jupyter notebook to render the plots inside the notebook instead of popping open a new window contaning the plot.

Next, lets plot the data.

```python
import matplotlib.pyplot as plt

plt.plot(years, babies_per_year)
```
