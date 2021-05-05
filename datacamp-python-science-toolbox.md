# datacamp python science toolbox

## part 1

-   **define function**
    -   return multiple value : tuple
-   **scope** :
    -   global scope - define a the main body of a script
    -   local scope - define inside a function
    -   `global`
    -   scope searched priority:
        -   local scope
        -   enclosing functions
        -   global
        -   built-in
-   **nested function** :
    -   `nonlocal`
-   **default and flexible arguments**
    -   positional arguments - tuple
    -   keyword arguments - dict
-   **lambda functions** :
    -   `map(lambda,list)`
    -   `filter(lambda,list)`
    -   from functools import reduce
        -   `reduce(lambda,list)` - concatenate list of strings
-   **error handlings** :
    -   handle different error types

```python
def sqrt(x):
    if x<0
        `raise`ValueError('x must be non-negative')
    try x ** 0,5
```

## part 2

-   **iterators vs iterables** :
    -   iterables - multiple time
        -   lists, strings, dictionaries, file connections
        -   applying `iter()` to an iterable creates an iterator
    -   iterators - 1 time
        -   any object that has `__iter__` and `__next__`method
        -   produces next value with `next()`
    -   `*` : unpacks all elements of an iterator or iterable
    -   `enumerate(iterable,start=1)`
    -   `zip(iterable,iterable)`
    -   a popular use case in data science, big data :
        -   pulling data from a file, database or API
        -   large amount of data, too much data to hold in memory
        *   solution : load data in chunks
        -   perform the desired operation or operations on each chunks
        -   store the result, discard the chunk
        -   pandas load data in chunks
            -   `pd.read_csv(chunk_size='')`
-   **list comprehensions**
    -   create list from other list(actually iterables)
    -   2 or more `for` : nested loop
    -   [value for if]
    -   [expression output-condition `for` iteration iterable-condition]
    -   dict comprehensions {key:value `for` iterations}

```python
# Create a 5 x 5 matrix using a list of lists: matrix
matrix = [[col for col in range(5)] for row in range(5)]
```

-   **generators**
    -   every generator is iterator, but not vice versa
    -   generator functions : use `yield` instead of `return`
    -   generator syntax is similar to list comprehension
        -   except for () instead of []
        -   `next()` to yield result
    -   using python generators for streaming data
