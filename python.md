# python

## Contents

- [python](#python)
- [basics](#basics)
    - [list](#basics#list)
    - [variables & function](#basics#variables & function)
        - [function scope](#basics#variables & function#function scope)
- [class](#class)
    - [property](#class#property)
    - [method](#class#method)
    - [object](#class#object)
        - [attribute = class varibles + instance variables](#class#object#attribute = class varibles + instance variables)
        - [add grade function](#class#object#add grade function)
- [modules](#modules)
    - [random , datetime](#modules#random , datetime)
    - [matplotlib](#modules#matplotlib)
    - [pypi, pipenv, virtual environment, requests library](#modules#pypi, pipenv, virtual environment, requests library)
- [work with files](#work with files)
    - [with](#work with files#with)
    - [csv : comma-seperate values](#work with files#csv : comma-seperate values)
    - [json](#work with files#json)

# basics

## list
- list comprehension : create a new list based on an available list or range
```python
list_comprehension = [i+1 for i in range(3)]
```
- `sorted` vs `.sort()`
- `list[-2:]`

## variables & function
- pass
### function scope
- If a variable is defined inside of a function, it will not be accessible __outside__ of the function. 

# class
- instantiation

## property
- property is attribute
- __but__ attribute is __not__ property

## method
- the first argument of a method : the instance of the object itself, we refer to it as _self_
- Methods always have at least this one argument _self_
```python
class Dog:
  dog_time_dilation = 7

  def time_explanation(self):
    print("Dogs experience {} years for every 1 human year.".format(self.dog_time_dilation))

pipi_pitbull = Dog()
pipi_pitbull.time_explanation()
# Prints "Dogs experience 7 years for every 1 human year."
```

```python
class Circle:
  pi = 3.14
  def area(self, radius):
    return Circle.pi * radius ** 2
  
circle = Circle()
pizza_area = circle.area(12 / 2)
teaching_table_area = circle.area(36 / 2)
round_room_area = circle.area(11460 / 2)
```

## object
### attribute = class varibles + instance variables
- object : __attributes__ = class variables + instance variables
- class : __property__
- hasattr(object,"attribute") : has attributes
- getattr(object,"attribute",default) : default value given if does not exist(this is optional)
```python
# this is instance variables
class test :
    pass
a=test()
a.instance_variables = 'sushi'
```
```python
# this is also instance variables but with constructor
class SearchEngineEntry:
  def __init__(self, url):
    self.url = url
codecademy = SearchEngineEntry("www.codecademy.com")
wikipedia = SearchEngineEntry("www.wikipedia.org")

print(codecademy.url)
# prints "www.codecademy.com"

print(wikipedia.url)
# prints "www.wikipedia.org"
```

### add grade function
if type(grade) is Grade

```python
def add_grade(self, grade):
    if type(grade) is Grade:
      self.grades.append(grade)
```

# modules
- [modules](https://docs.python.org/3/tutorial/modules.html)
- A module is a collection of Python declarations intended broadly to be used as a tool
- Modules are also often referred to as “libraries” or “packages” — a package is really a directory that holds a collection of modules
```python
from module_name import object_name
```
- a library will include a lot of code that you don’t need that may slow down your program or conflict with existing code
- Because of this, it makes sense to only import what you need
## random , datetime
- `random.choice()` which takes a list as an argument and returns a number from the list
- `random.randint()` which takes two numbers as arguments and generates a random number between the two numbers you passed in
- strftime(),strptime()
- 

## matplotlib
- `from matplotlib import pyplot as plt`, `plt.plot(num1,num2)`,`plt.show`
- what is __plot__?
- Using a package manager (like conda or pip3), you can install any modules available on the Python Package Index.

## pypi, pipenv, virtual environment, requests library
# work with files
- Learn Python: Files
- you will learn :
    - __Open__ up file objects using open() and with.
    - __Read__ a file’s __full contents__ using Python’s .read() method.
    - __Read__ a file __line-by-line__ using .readline() and .readlines()
    - __Create__ new files by opening them in write-mode.
    - __Append__ to a file non-destructively by opening a file in append-mode.
    - Apply all of the above to different types of data-carrying files including __CSV__ and __JSON__!
You have all the skills necessary to __read__, __write__, and __update__ files programmatically, a very useful skill in the Python universe!

## with
- We’ve been opening these files with this with block so far, but it seems a little weird that we can only use our file variable in the indented block
- Why is that? The `with` keyword invokes something called a __context manager__ for the file that we’re calling `open()` on
- This __context manager__ takes care of opening the file when we call open() and then closing the file after we leave the indented block
- Why is closing the file so complicated? Well, most other aspects of our code deal with things that Python itself controls
- All the variables you create: integers, lists, dictionaries — these are all Python objects, and __Python knows how to clean them up when it’s done with them__
- Since your files exist outside your Python script, we need to tell Python when we’re done with them so that it can close the connection to that file
- Leaving a file connection open unnecessarily can affect performance or impact other programs on your computer that might be trying to access that file
- The with syntax replaces older ways to access files where you need to call .close() on the file object manually
- We can still open up a file and append to it with the old syntax, as long as we remember to close the file connection afterwards
```python
fun_cities_file = open('fun_cities.txt', 'a')

# We can now append a line to "fun_cities".
fun_cities_file.write("Montréal")

# But we need to remember to close the file
fun_cities_file.close()
```
## csv : comma-seperate values
- first row of the CSV file doesn’t represent any data, just the labels of the data that’s present in the rest of the file
- we call all files with a list of different values a CSV file
- then use different delimiters (like a comma or tab) to indicate where the different values start and stop
- let’s say we had an address book
- __Since addresses usually use commas in them__, we’ll need to use a different delimiter for our information
- Since none of our data has semicolons (;) in them, we can use those
- __list comprehension__
```python
access_log = [{'time': '08:39:37', 'limit': 844404, 'address': '1.227.124.181'}, {'time': '13:13:35', 'limit': 543871, 'address': '198.51.139.193'}, {'time': '19:40:45', 'limit': 3021, 'address': '172.1.254.208'}, {'time': '18:57:16', 'limit': 67031769, 'address': '172.58.247.219'}, {'time': '21:17:13', 'limit': 9083, 'address': '124.144.20.113'}, {'time': '23:34:17', 'limit': 65913, 'address': '203.236.149.220'}, {'time': '13:58:05', 'limit': 1541474, 'address': '192.52.206.76'}, {'time': '10:52:00', 'limit': 11465607, 'address': '104.47.149.93'}, {'time': '14:56:12', 'limit': 109, 'address': '192.31.185.7'}, {'time': '18:56:35', 'limit': 6207, 'address': '2.228.164.197'}]
fields = ['time', 'address', 'limit']

# write to csv
import csv

with open('logger.csv', 'w') as logger_csv:
  log_writer = csv.DictWriter(logger_csv, fieldnames=fields)
  log_writer.writeheader()
  for line in access_log:
    log_writer.writerow(line)
```
## json

comeback do portfolio project later
