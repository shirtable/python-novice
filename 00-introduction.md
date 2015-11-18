Introduction
============
The goal of this workshop is to take people with very little to no programming experience to the point of understanding the basics of programming in the Python language. By the end of this class you will have written some programs and will have been exposed to the following concepts:

* typeness
    * strings
    * numbers
    * lists, tuples
    * dictionaries
* loading data from a file (csv, JSON)
* writing data to a file (csv, JSON)
* functions
* errors and exceptions
* control statments (if, etc.)
* loops
* visualization
* importing modules and libraries
* the OOP nature of python


What is programming?
====================
I like to think of programming as the following:

    Programming is a human telling a computer how to manipulate data.

I like this definition because it captures the interaction between all of the entities involved: 

* Human (noun): Its impossible to separate the human component from computing. People forget this priniciple at their own expense.
* Computer (noun): Computing wouldn't be computing without a computer.
* Data (noun): Computers operate on data.
* Telling (verb): The human tells the computer what to do.
* Manipulate (verb): The computer manipulates the data on behalf of the human.

Programming and software development are not necessarily the same things. Software development is humans collaborating on building software. Write your code to be read and understood by humans. Even if you are the only developer, you should think of yourself six months from now (and six months ago) as your collaborator.


The problem: Most popular CA baby names, 2009-2013
==================================================
The US government publishes several data sets at data.gov; an interesting one is [the most popular baby names in California from 2009 to 2013](http://catalog.data.gov/dataset/most-popular-baby-names-2009-2013). You should navigate to the site. You should also [download the csv file](https://cdph.data.ca.gov/api/views/9h3n-g3p4/rows.csv?accessType=DOWNLOAD) of the data so that you can do the exercises in this lesson.

Some questions we could answer using this data set:

* How many babies have four letter names?
* How many female babies have names that start with "L"?
* How many babies were born in 2010?
* What's the ratio of male babies to female babies in 2012?

These are the kinds of questions that one could answer with Excel and a few hours, but we are going to address them using Python. We will start small, but then build on what we've learned throughout the day.


Structure
=========
Part 1: Data
------------
* Basics
* Strings, numbers and typeness
* Containers: lists and dictionaries


Part 2: Flow
------------
* Control statements
* Looping and iteration
* Reading and writing files
