# python with databases

## Contents

- [python with databases](#python with databases)
    - [Python’s SQLite API](#python with databases#Python’s SQLite API)
    - [Connecting to SQLite in Python](#python with databases#Connecting to SQLite in Python)
    - [Executing SQL Statements in Python](#python with databases#Executing SQL Statements in Python)
        - [Reading our SQL data with Python](#python with databases#Executing SQL Statements in Python#Reading our SQL data with Python)
            - [for loop](#python with databases#Executing SQL Statements in Python#Reading our SQL data with Python#for loop)
            - [fetchone()](#python with databases#Executing SQL Statements in Python#Reading our SQL data with Python#fetchone())
            - [fetchmany()](#python with databases#Executing SQL Statements in Python#Reading our SQL data with Python#fetchmany())
            - [fetchall()](#python with databases#Executing SQL Statements in Python#Reading our SQL data with Python#fetchall())
        - [other clauses](#python with databases#Executing SQL Statements in Python#other clauses)
    - [SQlite with Pandas](#python with databases#SQlite with Pandas)
    - [Takeaways](#python with databases#Takeaways)

## Python’s SQLite API
- With `DB-API 2.0`, we can __connect__ __Python to __RDBMS like PostgreSQL(psycopg2), MySQL(mysqlclient), Oracle(pyodbc), and SQLite__
- `sqlite3` __module__ allows us to __create, read, update, and delete__ the data in our __SQLite relational databases__ within __Python script__
- an Application Programmable Interface (API) is simply a way that we can __communicate__ between __different applications__
- in this case we want Python and SQLite to communicate with one another
## Connecting to SQLite in Python
- With the `sqlite3` module already included in The Python Standard Library with any version of Python 2.5 and above
- we simply need to __import__ the module like we would with any other in-house module:

- Once we have `sqlite3` imported, we will need to connect to a database
- We can connect to a new or pre-existing database with the `sqlite3.connect()` API
- imagine our __connection object__ as a cable that __connects__ our __python environment__ to our __SQLite database__

- Next we need a way to __call SQL statements__ on the data within the database
- A __cursor object__ represents a __database cursor__
- and can be used to __call statements__ to our _SQLite database_, and __return the data__ in our _python environment_

```python
# Import the SQLite3 module
import sqlite3
# This call will either connect to the database named, or create that database if it does not already exist
# Create connection to database
conn = sqlite3.connect("first.db")
# We can create a __cursor object__ by using the cursor method of the connection class:
# Create cursor object
cursor = conn.cursor()
```

- With connection and cursor instantiated, we have everything we need to __make queries__ to our SQLite database within Python 

## Executing SQL Statements in Python
- Our cursor object is able to execute statements with its execute() method
- Note : use a __triple-quoted__ to make a multi-line String
- To insert multiple values at once we can use the `executemany()` method - execute multiple commands in a single API call
- Let’s create a list of student data that follows the students table schema so that the data can be added swiftly:
```python
# Create students table
cursor.execute('''CREATE TABLE students (
                    id INTEGER PRIMARY KEY,
                    name TEXT NOT NULL,
                    email TEXT NOT NULL UNIQUE,
                    major_code INTEGER,
                    grad_date datetime,
                    grade REAL NOT NULL)''')
                    
# Add a row of data to students table
cursor.execute('''INSERT INTO students VALUES (101, 'Alex', 'alex@codeu.com', 32, '2022-05-16', 'Pass')''')

# Insert multiple values into table at once
students = [(102, 'Joe', 'joseph@codeu.com', 32, '2022-05-16', 'Pass'),
            (103, 'Stacy', 'stacy@codeu.com', 10, '2022-05-16', 'Pass'),
            (104, 'Angela', 'angela@codeu.com', 21, '2022-12-20', 'Pass'),
            (105, 'Mark', 'mark@codeu.com', 21, '2022-12-20', 'Fail'),
            (106, 'Nathan', 'nathaniel@codeu.com', 21, '2022-12-20', 'Pass')
            ]

# Insert values into the students table
# 6 question marks as placeholders represent 6 fields in the database that we will insert values into
cursor.executemany('''INSERT INTO students VALUES (?,?,?,?,?,?)''', students)

# Commit changes to database
# Ensure changes will be visible to others who may be working with our database
connection.commit()
```

### Reading our SQL data with Python
#### for loop
- To read the data within our database, we can use multiple methods
- The most simple is to use a for loop that iterates through our database and calls some SQL statement:
```python
# Iterate through all rows in students table
for row in cursor.execute("SELECT * FROM students"):
    print(row)

# Output
(101, 'Alex', 'alex@codeu.com', 32, '2022-05-16', 'Pass')
(102, 'Joe', 'joseph@codeu.com', 32, '2022-05-16', 'Pass')
(103, 'Stacy', 'stacy@codeu.com', 10, '2022-05-16', 'Pass')
(104, 'Angela', 'angela@codeu.com', 21, '2022-12-20', 'Pass')
(105, 'Mark', 'mark@codeu.com', 21, '2022-12-20', 'Fail')
(106, 'Nathan', 'nathaniel@codeu.com', 21, '2022-12-20', 'Pass')
```
- There are a number of sqlite3 methods that will __retrieve data__, these being
    - `fetchone()`
    - `fetchmany()`
    - `fetchall()`
- __Note__ : using for loops and the `fetchone()` method return __tuples__, while `fetchmany()` and `fetchall()` return __lists of tuples__

#### fetchone()
- When we simply want to return the first row that fulfills a query, we can use `fetchone():`
```python
# Return first row in students
cursor.execute("SELECT * FROM students").fetchone()
```
- Output:
```python
# Output
(101, 'Alex', 'alex@codeu.com', 32, '2022-05-16', 'Pass')
```
#### fetchmany()
- To return a specific number of rows from our database that correspond to a particular query
- we can call `fetchmany()` on our statement, and set the number of rows as a __parameter__
- Like `fetchone(),` this call will return the first rows that match our query
```python
# Return first three rows in students
cursor.execute("SELECT * FROM students").fetchmany(3)
```
- Output:
```python
# Output
[(101, 'Alex', 'alex@codeu.com', 32, '2022-05-16', 'Pass'),
 (102, 'Joe', 'joseph@codeu.com', 32, '2022-05-16', 'Pass'),
 (103, 'Stacy', 'stacy@codeu.com', 10, '2022-05-16', 'Pass')]
```
#### fetchall()
- If we want to return all rows associated with a certain SQL statement, we can call the `fetchall()` :
```python
# Return all rows in students
cursor.execute("SELECT * FROM students").fetchall()
```
- Output:
```python
# Output
[(101, 'Alex', 'alex@codeu.com', 32, '2022-05-16', 'Pass'),
 (102, 'Joe', 'joseph@codeu.com', 32, '2022-05-16', 'Pass'),
 (103, 'Stacy', 'stacy@codeu.com', 10, '2022-05-16', 'Pass'),
 (104, 'Angela', 'angela@codeu.com', 21, '2022-12-20', 'Pass'),
 (105, 'Mark', 'mark@codeu.com', 21, '2022-12-20', 'Fail'),
 (106, 'Nathan', 'nathaniel@codeu.com', 21, '2022-12-20', 'Pass')]
```
### other clauses
All of your SQLite syntax will work in Python. You can use clauses like `WHERE`, `COUNT`, etc.
```python
# Return the number of rows with a passing grade
cursor.execute("""SELECT COUNT(*) FROM students WHERE Grade = 'Pass';""").fetchone()
```
- output :
```python
# Output
(5,)
```
- Let’s say that we would like to find the average of the major codes field
- We can use Python methods `sum()` and `len()` on our result set to obtain the mean value of the field
```python
# Create a list of tuples of the major codes
major_codes = cursor.execute("SELECT major_code FROM students;").fetchall()

# Obtain the average of the tuple list by using for loops
sum = 0
for num in major_codes: 
    for i in num: 
        sum = sum + i 
average = sum / len(major_codes)

# Show average
print(average)
```
- output :
```python
# Output
22.833333333333332
```
- Working with SQLite within Python also allows us to integrate other Python libraries with our SQLite database
- This enables us to use some of the __Pandas__ functionality on our relational databases
- __Pandas__ is considered to be one of the most popular open source python libraries for data analysis

## SQlite with Pandas
- Let’s use Pandas to transform our SQLite database into a __Pandas DataFrame__
- First we will import Pandas into Python
- then call the Pandas `read_sql_query()` method
- that takes in a query and a connection as parameters and returns a DataFrame corresponding to the output of the query:
```python
# Create a new dataframe from the result set
df = pd.read_sql_query('''SELECT * from students;''', connection)

# Show new dataframe
print(df)
```

- We can create a number of DataFrames based on any query
- For instance, if we want to create a DataFrame containing only those rows
- where the major code was equal to 21, we can use the `WHERE` clause within the `read_sql_query()` method:
```python
# Create a new dataframe from the result set
df = pd.read_sql_query('''SELECT * from students WHERE major_code = 21;''', connection)

# Show new dataframe
print(df)
```
- Now that we are working with Pandas
- if we wanted to find the average of the major codes
- we could simply use the Pandas `mean()` method on the `major_code` field:
```python
# Return the average of major code
df['major_code'].mean()
```
- output :
```python
# Output
22.833333333333332
```

## Takeaways
- The `sqlite3` module within the Python Standard Library allows you to make SQLite API calls within Python
- Once you have established a connection and a cursor to a SQLite database, you are able to run queries to access data within your database
- Pandas includes methods like `read_sql_query()` that enable you to transform a SQL database into a Pandas dataframe for even more functionality
