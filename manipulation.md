# manipulation

<!-- vim-markdown-toc GFM -->

* [introduction to sql](#introduction-to-sql)
* [relational database](#relational-database)
* [statement](#statement)
    * [create](#create)
    * [Insert](#insert)
    * [Select](#select)
    * [Alter](#alter)
    * [Update](#update)
    * [Delete](#delete)
* [Constraints](#constraints)

<!-- vim-markdown-toc -->
## introduction to sql
- SQL, __Structured__ Query Language, is a __programming language__ designed to __manage data stored in relational databases__
- SQL operates through __simple, declarative statements__
- This keeps data accurate and secure, and helps __maintain the integrity of databases, regardless of size__
- The SQL language is widely used today across __web frameworks__ and __database applications__
- Knowing SQL gives you the __freedom to explore your data__, and the power to make better decisions
- By learning SQL, you will also learn concepts that apply to nearly every __data storage system__
- The statements covered in this course use __SQLite__ Relational Database Management System (RDBMS)
- You can also access a glossary of all the SQL commands taught in this course

## relational database
- A __relational database__ is a database that organizes information into one or more tables
- All data stored in a __relational database__ is of a certain data type
- Some of the most common data types are:
    - `INTEGER`, a positive or negative whole number
    - `TEXT`, a text string
    - `DATE`, the date formatted as YYYY-MM-DD
    - `REAL`, a decimal value

## statement
- The code below is a SQL statement
- A statement is text that the database recognizes as a valid command
- Statements always end in a semicolon `;` 
```sql
CREATE TABLE table_name (
   column_1 data_type, 
   column_2 data_type, 
   column_3 data_type
);
```
- Let’s break down the components of a statement:
    - CREATE TABLE is a __clause__
        - __Clauses__ perform specific tasks in SQL
        - By convention, __clauses__ are written in capital letters
        - __Clauses__ can also be referred to as __commands__
    - table_name refers to the name of the table that the command is applied to
    - (column_1 data_type, column_2 data_type, column_3 data_type) is a __parameter__
        - A parameter is a __list of columns, data types, or values__ that are passed to a clause as an argument
        - Here, the __parameter__ is a list of column names and the associated data type
- The structure of SQL statements vary
- The number of lines used does not matter
- A __statement__ can be written all on one line, or split up across multiple lines if it makes it easier to read
- In this course, you will become familiar with the structure of common statements

### create
- `CREATE` statements allow us to create a new table in the database
- You can use the `CREATE` statement anytime you want to create a new table from scratch
- The statement below creates a new table named celebs 
```sql
CREATE TABLE celebs (
   id INTEGER, 
   name TEXT, 
   age INTEGER
);
```
1. `CREATE TABLE` is a __clause__ that tells SQL you want to create a new table
2. `celebs` is the __name of the table__
3. `(id INTEGER, name TEXT, age INTEGER)` is a list of __parameters__ defining each column, or attribute in the table and its data type

### Insert
- The `INSERT` statement inserts a new row into a table
- You can use the `INSERT` statement when you want to add new records
- The statement below enters a record for Justin Bieber into the celebs __table__

```sql
INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 22);
```

1. `INSERT INTO` is a __clause__ that adds the specified row or rows
2. `celebs` is the __name of the table__ the row is added to
3. `(id, name, age)` is a __parameter__ identifying the columns that data will be inserted into
4. `VALUES` is a __clause__ that indicates the data being inserted
5. `(1, 'Justin Bieber', 22)` is a __parameter__ identifying the values being inserted

### Select
- `SELECT` statements are used to fetch data from a database
- In the statement below, `SELECT` returns all data in the name column of the celebs table

```sql
SELECT name FROM celebs;
```

1. `SELECT` is a __clause__ that indicates that the statement is a __query__
2. You will use `SELECT` every time you __query__ data from a database
3. `name` specifies the column to query data from
4. `FROM` celebs specifies the name of the table to query data from In this statement, data is queried from the celebs table

You can also query data from all columns in a table with SELECT.
```sql
SELECT * FROM celebs;
```
\* is a special wildcard character that we have been using
* It allows you to select every column in a table without having to name each one individually
* Here, the result set contains every column in the celebs table.

`SELECT` statements always return a new table called the __result set__

### Alter
- The ALTER TABLE statement adds a new column to a table
- You can use this command when you want to add columns to a table
- The statement below adds a new column twitter_handle to the celebs table
```sql
ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT;
```
1. `ALTER TABLE` is a __clause__ that lets you make the specified changes.
2. `celebs` is the __name of the table__ that is being changed.
3. `ADD COLUMN` is a __clause__ that lets you add a new column to a table:
4. `NULL` is a special __value__ in SQL that represents __missing__ or __unknown__ data
    - Here, the rows that existed before the column was added have NULL (∅) values for twitter_handle.

### Update
- The `UPDATE` statement edits a row in a table
- You can use the `UPDATE` statement when you want to change existing records
- The statement below updates the record with an `id` value of 4 to have the `twitter_handle` `@taylorswift13`
```sql
UPDATE celebs 
SET twitter_handle = '@taylorswift13' 
WHERE id = 4; 
```
1. `UPDATE` is a clause that edits a row in the table
2. `celebs` is the name of the table
3. `SET` is a clause that indicates the column to edit
    `twitter_handle` is the name of the column that is going to be updated
    `@taylorswift13` is the new value that is going to be inserted into the `twitter_handle` column
4. `WHERE` is a clause that indicates which row(s) to update with the new column value
    - Here the row with a `4` in the `id` column is the row that will have the `twitter_handle` updated to `@taylorswift13`

### Delete
- The DELETE FROM statement deletes one or more rows from a table
- You can use the statement when you want to delete existing records
- The statement below deletes all records in the celeb table with no twitter_handle:
```sql
DELETE FROM celebs 
WHERE twitter_handle IS NULL;
```
1. `DELETE FROM` is a __clause__ that lets you delete rows from a table
2. `celebs` is the __name__ of the table we want to delete rows from
3. `WHERE` is a __clause__ that lets you select which rows you want to delete
    - Here we want to delete all of the rows where the `twitter_handle` column `IS NULL`
5. `IS NULL` is a __condition__ in SQL that returns true when the value is `NULL` and false otherwise

## Constraints
- __Constraints__ that add information about how a column can be used are invoked after specifying the data type for a column
- They can be used to tell the database to reject inserted data that does not adhere to a certain __restriction__
- The statement below sets __constraints__ on the `celebs` table
```sql
CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, 
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);
```
1. `PRIMARY KEY` columns can be used to uniquely identify the row
    - Attempts to insert a row with an identical value to a row already in the table will result in a constraint violation
    - which will not allow you to insert the new row
2. `UNIQUE` columns have a different value for every row
    - This is similar to `PRIMARY KEY` except a table can have many different `UNIQUE` columns.
3. `NOT NULL` columns must have a value
    - Attempts to insert a row without a value for a NOT NULL column will result in a constraint violation
    - and the new row will not be inserted
4. `DEFAULT` columns take an additional argument that will be the assumed value for an inserted row
    - if the new row does not specify a value for that column
