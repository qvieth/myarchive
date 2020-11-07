# python

<!-- vim-markdown-toc GFM -->

* [basics](#basics)
    * [list](#list)
    * [variables & function](#variables--function)
* [class](#class)
    * [property](#property)
    * [method](#method)
    * [object](#object)
        * [attribute = class varibles + instance variables](#attribute--class-varibles--instance-variables)
        * [dir() : directory listing : list element of a tree-like structure](#dir--directory-listing--list-element-of-a-tree-like-structure)
        * [if type(grade) is Grade:](#if-typegrade-is-grade)
* [modules](#modules)

<!-- vim-markdown-toc -->
## basics

### list
- `sorted` vs `.sort()`
- `list[-2:]`

### variables & function
- pass

## class
- instantiation

### property
- property is attribute
- __but__ attribute is __not__ property

### method
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

### object
#### attribute = class varibles + instance variables
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

#### dir() : directory listing : list element of a tree-like structure

#### if type(grade) is Grade:
```python
def add_grade(self, grade):
    if type(grade) is Grade:
      self.grades.append(grade)
```

## modules
https://www.codecademy.com/paths/data-science/tracks/dscp-python-fundamentals/modules/dscp-python-modules/lessons/modules-python/exercises/modules-python-intro
