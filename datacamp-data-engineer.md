# datacamp data engineer

-   you'll learn cloud and big data tools such as
    -   AWS Boto
    -   PySpark
    -   Spark SQL
    -   and MongoDB
-   which help you
    -   create and query databases
    -   wrangle data
    -   and configure schedules to run your pipelines

## Contents

-   [datacamp data engineer](#datacamp data engineer)
    -   [writing high quality functions in python](#datacamp data engineer#writing high quality functions in python)

```python
import sqlalchemy
connection_uri = "postgresql://repl:password@localhost:5432/pagila"
db_engine = sqlalchemy.create_engine(connection_uri)

import pandas as pd
pd.read_sql("SELECT * FROM customer",db_engine)
```

```python
result = requests.get(api_url, headers=headers, params=params)
result.json()
```

-   read data from json - nested json, deep nested json
-   combining multiple datasets
-   pandas `merge()` = sql `JOIN`

## writing high quality functions in python

-   docstrings format :
    -   google style
    -   numpydoc
    -   restructuredtext
    -   epytext
-   function writing principle - DRY and Do one thing :
-   code smells
    -   repeated code and functions that do more than one thing
-   and refractoring
    -   split the big function into multiple small function
-   argument pass by assignment(mutable and immutable)
-   context manager
    -   with <context_manager>() as <name> :
    -   decorator `@contextlib.contextmanager`
-   scope :
    -   local
    -   `nonlocal`
    -   `global`
    -   built-in
-   decorator :
    -   `@functools.wraps(func)` : decorated functions maintain their metadata
    -   decorator that take arguments

## OOP

-   procedural programming :
    -   sequential viewpoint : code as sequence of steps
    -   great for data analysis and scripts
-   OOP :
    -   code as interactions of objects
    -   great for building frameworks and tools
    -   maintainable and reusable code
-   object = states + behaviors(methods)

*   class = attributes + methods :
    -   if you say :
        ```
        every customer will have a phone number and
        an email, and will be able to place and cancel orders
        ```
    -   you just defined a class
    -   everything in python is an object, every object has a class
    -   use `type()` to find the class

-   encapsulation :
    -   one of the core tenets of object oriented programming
    -   bundle data and methods that operate on that data
-   class inheritance
-   polymorphism
-   class-level data
-   multiple inheritance and mixing classes
-   `__getattr__()` , `__setattr__()`
-   abstract base classes
-   data classes(new in python 3.7)
-   design
    -   SOLID
    -   design patter : reusable solutions addressing
        -   most common problems in software design

## Introduction to Airflow python

-   workflow :
    -   set of steps to accomplish a given data engineering task :
        -   downloading files
        -   copying data
        -   filtering information
        -   writing to a database, etc
    -   of varying levels of complexity(depend on the needs of user)
    -   a term with various meaning depending on context
-   airflow is a platform to program workflow :
    -   creation
    -   scheduling
    -   monitoring
-   airflow :
    -   can implement programs from any language
    -   but workflows are written in python
    -   implements workflow as DAGs(Directed Acyclic Graphs)
    -   accessed via code, command-line, or via web interface
-   other workflow tools :
    -   luigi
    -   microsoft SSIS
    -   bash scripting
-   DAGs :
    -   in Airflow, this represents the sets of tasks that
        -   make up your workflow
    -   consists of the tasks and the dependencies between tasks
    -   created with various details about the DAG, including the name, start date, owner, etc.

```DAG code example - simple DAG definition
etl_dag = DAG(
    dag_id='etl_pipeline'
    default_args={"start_date":"2020-01-08"}
)
```

-   tasks are :
    -   instances of operators
    -   usually assigned to a variable in python

```
example_task = BashOperator(task_id='bash_example',
                            bash_command='echo "Example!"',
                            dag=dag)
```

-   task dependencies :
    -   define a given order of task completion
    -   are not required for a given workflow, but usually present in most
-   sensors :
    -   an operator that wait for a certain condition to be true
        -   creation of a file
        -   upload of a database record
        -   certain response from a web request
    -   can define how often to check for the condition to be true
    -   are assigned to task
    -   file sensor :
        -   can check for the existence of a file at a certain location
-   why sensors :
    -   uncertain when it will be true
    -   add task repetition without loop
-   executor :
    -   run tasks
    -   different executors handle running the tasks differently

# Building Data Engineering Pipelines in Python

1. ingesting Data
2. creating a data transformation pipeline with PySpark
3. testing your data pipeline - Pytest - CICD
4. managing and orchestrating workflow - Apache Airflow

-   ingesting data :
    -   data platform
    -   the process of getting data to the data lake is called ingestion
-   data lake :
    -   landing zone : raw data
    -   clean zone : clean data
    -   business zone : domain-specific data
-   build **data pipelines** :
    -   to move data from one zone to another
    -   and transform it along the way

*   if a dashboard had to be built showing a sales forecast
    -   based on the inventory of a warehouse
    -   this dashboard get its data from the **business zone**

-   singer's core concept :
    -   aim : the opensource standard for writing scripts that move data
    -   singer is a specification :
        -   data exchange format : JSON
        -   extract with taps
            -   and load with targers
                -   language independent
        -   communicate over streams :
            -   schema(metadata)
            -   state (process metadata)
            -   record (data)

```python
import singer
# Complete the JSON schema
schema = {'properties': {
    'brand': {'type': 'string'},
    'model': {'type': 'string'},
    'price': {'type': 'number'},
    'currency': {'type': 'string'},
    'quantity': {'type': 'integer', 'minimum': 1},
    'date': {'type': 'string', 'format': 'date'},
    'countrycode': {'type': 'string', 'pattern': "^[A-Z]{2}$"},
    'store_name': {'type': 'string'}}}

# Write the schema
singer.write_schema(stream_name='products',
                    schema=schema,
                    key_properties=[])
```

-   spark :
    -   engine for large-scale data processing
    -   4 libraries built on top of Spark core :
        -   Spark Sql
        -   Spark Streaming
        -   MLlib
        -   Graphx
    -   API in several languages :
        -   Java
        -   Scala
        -   Python(PySpark)
        -   R
    -   interactive analysis
    -   machine learning
    -   shouldn't be using spark when you have only little data
        -   adds overhead(cost) for small data

> PySpark DataFrames can be converted to Pandas DataFrames
> with toPandas. This collects all the data on the driver node
> and negates all the parallelism benefits of regular PySpark
> DataFrames
