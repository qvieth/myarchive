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
    -   [OOP](#datacamp data engineer#OOP)
    -   [Introduction to Airflow python](#datacamp data engineer#Introduction to Airflow python)
    -   [Building Data Engineering Pipelines in Python](#datacamp data engineer#Building Data Engineering Pipelines in Python)
    -   [test](#datacamp data engineer#test)
    -   [introduction to aws and boto in python](#datacamp data engineer#introduction to aws and boto in python)
    -   [mongodb](#datacamp data engineer#mongodb)
    -   [scala](#datacamp data engineer#scala)

## writing high quality functions in python

```python
import sqlalchemy
connection_uri = "postgresql://repl:password@localhost:5432/pagila"
db_engine = sqlalchemy.create_engine(connection_uri)

import pandas as pd
pd.read_sql("SELECT * FROM customer",db_engine)

result = requests.get(api_url, headers=headers, params=params)
result.json()
```

-   read data from json - nested json, deep nested json
-   combining multiple datasets
-   pandas `merge()` = sql `JOIN`

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
    -   created with various details about the DAG
        -   including the name, start date, owner, etc.

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

## Building Data Engineering Pipelines in Python

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

## test

-   3 kind of test : money -> time
    -   unit
    -   integration (aka service)
    -   end-to-end test - UI
-   our earlier Spark application is an ETL pipeline
    -   extract -> csv, disk, cloud, database
    -   transform -> Sql query
    -   load -> csv, disk, cloud, database
-   modern day workflow management
-   workflow :
    -   sequence of tasks
    -   scheduled to run at a time
    -   or be triggered by an event
-   workflows are typically used by data scientists and data engineers
    -   to orchestrate data processing pipelines
-   schedule with cron
    -   cron works very well,
    -   but isn't the best tool for complex workflows
    -   that we want to monitor over time
    -   modern workflow manager :
        -   luigi
        -   azkaban
        -   airflow
    -   advantage :
        -   allow us to create and visualize complex workflows
        -   monitor and log workflows
        -   scales horizontally
            -   as we get more tasks to execute, we want our tool to
            -   work with multiple machines rather than
            -   increasing the performance of one single machine
    -   central piece in an Airflow workflow is the DAG
        -   directed acyclic graph
            -   directed : there's direction between nodes
            -   acylic : no circle back
            -   graph : collection of nodes connected by edges
        -   nodes are operators
            -   each instance of which
                -   can be given a unique label, the task id
            -   operators do something like run python script
                -   or schedule tasks with a cloud provider
            -   they're triggered by a scheduler,
                -   but executed by an executor
                    -   typically a differnt process
        -   classes of operators :
            -   the airflow task :
                -   an instance of Operator class
                -   inherits from`BaseOperator`
                    -   -> must implement `execute()` method
            -   performs a specific action(delegation):
                -   `BashOperator`-> run Bash command/script
                -   `PythonOperator`-> run Python script
                -   `SparkSubmitOperator`-> submit a Spark job with a cluster

```python
from datetime import datetime
from airflow import DAG

reporting_dag = DAG(
    dag_id="publish_EMEA_sales_report",
    # Insert the cron expression
    schedule_interval="0 7 * * 1",
    start_date=datetime(2019, 11, 24),
    default_args={"owner": "sales"}
)
```

```cron
┌─── minute (0 - 59)
│ ┌─── hour (0 - 23)
│ │ ┌─── day of the month (1 - 31)
│ │ │ ┌─── month (1 - 12)
│ │ │ │ ┌─── day of the week (0 - 6) (Sunday to Saturday;
│ │ │ │ │               7 is also Sunday on some systems)
* * * * *

* is a wildcard here, meaning all allowed values for this field
Example: 30 9,21 * * 6 means every Saturday at 9:30 and again at
21:30.
```

-   what you learned :
    -   define purpose of components of data platforms
    -   write an ingestion pipeline using **Singer**
    -   create and deploy pipelines for big data in **Spark**
    -   configure automated testing using **CircleCI**
    -   manage and deploy a full data pipeline with **Airflow**

## introduction to aws and boto in python

-   to interact with aws in python, we use the boto3 library
-   create keys with IAM
-   objects and buckets in S3 work somewhat like files and folders on our desktop
-   what we've learned
-   amazon web services - the backbone of the internet
    -   decoupled and granular, they work well together or on their own
-   boto3 let us access and interact with aws using python
    -   making them an extension of your laptop

```python
s3 = boto3.client(...)
buckets = s3.list_buckets()
```

-   IAM lets us control users and access keys in AWS
-   S3
    -   you learned how to create, list and delete buckets in S3
    -   upload files into them and secure the files
-   SNS
    -   you learned how to send messages to emails and phone numbers
    -   using SNS by creating topics and subscribing users to them
-   Rekognition
    -   you learned how to find stray cats by detecting them in an
    -   image using Rekognition, and how to extract text from parking signs
-   finally, you learned how to perform sentiment analysis and detect language using AWS Comprehend
    -   as you learn more services, you will use the boto3 documentation
        -   to understand how they work and how to use them

## mongodb

-   JSON
    -   common way that web services and client code pass data
    -   the basis of MongoDB's data format

| JSON                 | Python            |
| -------------------- | ----------------- |
| Objects              | dict              |
| Arrays               | list              |
|                      |                   |
| strings              | str               |
| **numbers**          | int, float        |
| true / false         | True / False      |
| null                 | None              |
| other objects/arrays | other dict / list |

-   mongodb

    -   database
        -   collections -> like a list of dictionaries, called "documents"
            -   documents -> when a dictionary is a value within a document, that's a subdocument
                -   fields -> values in a document can be any of the types above

-   pymongo : official python driver for mongodb
-   accessing databases and collections

## scala

-   **SCALA NUDGES US TOWARDS IMMUTABILITY**

-   val(immutable) vs var(mutable)
-   9 value types - all variables have a type :
    1. [x] Double
    2. [ ] Float
    3. [ ] Long
    4. [x] Int
    5. [ ] Short
    6. [ ] Byte
    7. [x] Char -> String : sequence of Char
    8. [x] Boolean
    9. [ ] Unit
-   choosing the right type makes programs smaller and faster
-   for data-related tasks, four most common types are

```scala
val symbolAceSpades: String = "A_spades"
```

-   pros and cons of immutability :
    -   pros :
        -   your data won't be changed inadvertently
        -   your code is easier to reason about
        -   you have to write fewer tests
    -   cons :
        -   more memory required due to data copying

> because we are forced to copy our objects each time we
> want to make a change, we become much more conscious of
> HOW and WHEN we change our program's state
> With this philosophy, we receive fewer possible states
> within our programs, fewer defects, and codebases that are
> easier to maintain.

-   type inference
-   function - everything in the curly braces is called body

-   collections - mutable vs immutable :
    -   mutable
        -   `Array` are mutable
    -   immutable
        -   `List`
-   cons (`::`)
    -   **PREPENDS** a new element to the beginning of an existing `List`
        -   and returns the resulting `List`
            -   appends operation exists in Scala
            -   but it's rarely used because its not efficient
-   `Nil` : empty list

*   scala code is first compiled to java bytecodes then
    -   run on a java virtual machine
*   scala's static type system
    -   key feature of the language
    -   type :
        -   restricts the possible values to which
            -   a variable can refer
            -   or an expression can produce
            -   at run time
        -   scala value types have equivalent java primitive types
    -   compile time :
        -   when source code is translated into machine code,
            -   i.e., code that a computer can read
    -   runtime :
        -   when the program is executing commands
            -   (after compilation, if compiled)

-   static type(type are checked before runtime)
    -   pros :
        -   increase perfomance at runtime
        -   prove the absence of common type-related bugs
        -   safe refractoring
    -   cons :
        -   takes time to check types(delay before execution)
        -   code is verbose(code is longer/more annoying to write)
        -   the language is not flexible(one strict way of composing a type)
            -   -> scala fix this with type inference
-   dynamic type systems(types are checked during execution)

-   control structure :
    -   a block of programming that analyses variables and chooses
    -   a direction in which to go based on given parameters
    -   the term flow control details the direction the program takes
    -   (which way program control "flows")
    -   `if` / `else`

```scala
// this's point value
val hand = 24

// if this hand busts, print to output
if (hand > 24) {
    println("This hand busts!")
}
```

-   writing `while` loops is a feature of a style of
    -   programming called **imperative style**
    -   which isn't the scala PREFERED style
    -   One command at a time
    -   Iterate with loops
    -   Mutate shared state (e.g., mutating variables out of scope)

```scala
// define counter variable
var i = 0

// initialize array with each player's hand
var hands = Array(17,24,21)

// loop through hands and see if each busts
while (i< hands.length) {
    println(bust(hands(i)))
    i += 1
}
```

-   `foreach` and the **functional style**
    -   scala was designed functional-first
    -   functions are first-class values
        -   operations of a program map input values to output values
        -   rather than change data in place
    -   the functional style is favored
    -   `foreach` is not a built-in control structure

```scala
// initialize array with each player's hand
var hands = Array(17,24,21)

// see if each hand busts
hands.foreach(INSERT FUNCTION HERE)
```

-   signs of style :

| imperative   | functional                                         |
| ------------ | -------------------------------------------------- |
| `var`        | `val`                                              |
| side effects | no side effects                                    |
| `Unit`       | non-`Unit` value types(`Int`, `Boolean`, `Double`) |
