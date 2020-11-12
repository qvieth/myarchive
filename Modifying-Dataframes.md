# Modifying Dataframes
- you'll learn : 
    - Adding columns to a DataFrame
    - Using lambda functions to calculate complex quantities
    - Renaming columns
<!-- vim-markdown-toc GFM -->

* [Adding a Column I](#adding-a-column-i)
* [Adding a Column II](#adding-a-column-ii)
* [Adding a Column III](#adding-a-column-iii)
* [Performing Column Operations](#performing-column-operations)
* [Reviewing Lambda Function](#reviewing-lambda-function)
* [Applying a Lambda to a Column](#applying-a-lambda-to-a-column)
* [Applying a Lambda to a Row](#applying-a-lambda-to-a-row)
* [Renaming Columns : .columns not .column](#renaming-columns--columns-not-column)
* [Renaming Columns II](#renaming-columns-ii)

<!-- vim-markdown-toc -->
## Adding a Column I
- Sometimes, we want to add a column to an existing DataFrame
- We might want to add new information or perform a calculation based on the data that we already have
- One way that we can add a new column is by giving a __list__ of the __same length__ as the existing DataFrame
- Suppose we own a hardware store called The Handy Woman and have a DataFrame containing inventory information:

| Product-ID | Product-Description | Cost-to-Manufacture | Price |
|------------|---------------------|---------------------|-------|
| 1          | 3 inch screw        | 0.50                | 0.75  |
| 2          | 2 inch nail         | 0.10                | 0.25  |
| 3          | hammer              | 3.00                | 5.50  |
| 4          | screwdriver         | 2.50                | 3.00  |

- It looks like the actual quantity of each product in our warehouse is missing!
- Let’s use the following code to add that information to our DataFrame
```python
df['Quantity'] = [100, 150, 50, 35]
```

- Our new DataFrame looks like this:

| Product ID | Product      | Description | Cost to Manufacture | Price | Quantity |
|------------|--------------|-------------|---------------------|-------|----------|
| 1          | 3 inch screw | 0.50        | 0.75                | 0.75  | 100      |
| 2          | 2 inch nail  | 0.10        | 0.25                | 0.25  | 150      |
| 3          | hammer       | 3.00        | 5.50                | 5.50  | 50       |
| 4          | screwdriver  | 2.50        | 3.00                | 3.00  | 35       |


## Adding a Column II
- We can also add a new column that is the same for all rows in the DataFrame
- Let’s return to our inventory example:

| Product-ID | Product-Description | Cost-to-Manufacture | Price |
|------------|---------------------|---------------------|-------|
| 1          | 3 inch screw        | 0.50                | 0.75  |
| 2          | 2 inch nail         | 0.10                | 0.25  |
| 3          | hammer              | 3.00                | 5.50  |
| 4          | screwdriver         | 2.50                | 3.00  |

- Suppose we know that all of our products are currently in-stock
- We can add a column that says this:
```python
df['In Stock?'] = True
```
- Now all of the rows have a column called `In Stock?` with value `True`

| Product ID | Product      | Description | Cost to Manufacture | Price | In Stock? |
|------------|--------------|-------------|---------------------|-------|-----------|
| 1          | 3 inch screw | 0.50        | 0.75                | 0.75  | True      |
| 2          | 2 inch nail  | 0.10        | 0.25                | 0.25  | True      |
| 3          | hammer       | 3.00        | 5.50                | 5.50  | True      |
| 4          | screwdriver  | 2.50        | 3.00                | 3.00  | True      |

## Adding a Column III
- Finally, you can add a new column by performing a function on the existing columns
- Maybe we want to add a column to our inventory table with the amount of sales tax that we need to charge for each item
- The following code multiplies each Price by 0.075, the sales tax for our state:
```python
df['Sales Tax'] = df.Price * 0.075
df['Margin'] = df['Price'] - df['Cost to Manufacture']
```
- Now our table has a column called Sales Tax and Margin:

| Product ID | Product      | Description | Cost to Manufacture | Price | Sales Tax | Margin |
|------------|--------------|-------------|---------------------|-------|-----------|--------|
| 1          | 3 inch screw | 0.50        | 0.75                | 0.75  | 0.06      | 0.25   |
| 2          | 2 inch nail  | 0.10        | 0.25                | 0.25  | 0.02      | 0.15   |
| 3          | hammer       | 3.00        | 5.50                | 5.50  | 0.41      | 2.5    |
| 4          | screwdriver  | 2.50        | 3.00                | 3.00  | 0.22      | 0.5    |

## Performing Column Operations
- In the previous exercise, we learned how to add columns to a DataFrame
- Often, the column that we want to add is related to existing columns, but requires a calculation more complex than multiplication or addition
- For example, imagine that we have the following table of customers.


| Name       | Email                |
|------------|----------------------|
| JOHN SMITH | john.smith@gmail.com |
| Jane Doe   | jdoe@yahoo.com       |
| joe schmo  | joeschmo@hotmail.com |
     	
- It’s a little annoying that the capitalization is different for each row
- Perhaps we’d like to make it more consistent by making all of the letters uppercase

- We can use the apply function to apply a function to every value in a particular column
- For example, this code overwrites the existing 'Name' columns by applying the function upper to every row in 'Name'
```python
from string import upper
df['Name'] = df.Name.apply(upper)
```
- The result:

| Name       | Email                |
|------------|----------------------|
| JOHN SMITH | john.smith@gmail.com |
| JANE DOE   | jdoe@yahoo.com       |
| JOE SCHMO  | joeschmo@hotmail.com |

## Reviewing Lambda Function
https://www.codecademy.com/articles/lambda-functions
- A lambda function is a way of defining a function in a single line of code
- Usually, we would assign them to a variable
- For example, the following lambda function multiplies a number by 2 and then adds 3:
```python
mylambda = lambda x: (x * 2) + 3
print(mylambda(5))

stringlambda = lambda x: x.lower()
print(stringlambda("Oh Hi Mark!"))
```
- The output:
```bash
> 13
> "oh hi mark!"
```
- lambda in a nutshell
```python
lambda x: [OUTCOME IF TRUE] if [CONDITIONAL] else [OUTCOME IF FALSE]
```

## Applying a Lambda to a Column
- In Pandas, we often use lambda functions to perform complex operations on columns
- For example, suppose that we want to create a column containing the email provider for each email address in the following table:

| Name       | Email                |
|------------|----------------------|
| JOHN SMITH | john.smith@gmail.com |
| JANE DOE   | jdoe@yahoo.com       |
| JOE SCHMO  | joeschmo@hotmail.com |

- We could use the following code by using `.apply()` with a lambda function and the string method `.split()` :
```python
df['Email Provider'] = df.Email.apply(
    lambda x: x.split('@')[-1]
    )
```
- The result would be:

| Name       | Email                | Email Provider |
|------------|----------------------|----------------|
| JOHN SMITH | john.smith@gmail.com | gmail.com      |
| JANE DOE   | jdoe@yahoo.com       | yahoo.com      |
| JOE SCHMO  | joeschmo@hotmail.com | hotmail.com    |

## Applying a Lambda to a Row
- We can also operate on multiple columns at once
- __NOTE__ : If we use `apply` without specifying a single column and add the argument `axis=1`, the input to our lambda function will be an entire row, not a column
- https://railsware.com/blog/python-for-machine-learning-pandas-axis-explained/
- To access particular values of the row, we use the syntax `row.column_name` or `row[‘column_name’]`
- Suppose we have a table representing a grocery list:

| Item         | Price | Is taxed? |
|--------------|-------|-----------|
| Apple        | 1.00  | No        |
| Milk         | 4.20  | No        |
| Paper Towels | 5.00  | Yes       |
| Light Bulbs  | 3.75  | Yes       |

- If we want to add in the price with tax for each line, we’ll need to look at two columns: `Price` and `Is taxed?`
- If `Is taxed?` is `Yes`, then we’ll want to multiply `Price` by 1.075 (for 7.5% sales tax).
- If `Is taxed?` is `No`, we’ll just have `Price` without multiplying it.
- We can create this column using a lambda function and the keyword `axis=1`:
```python
df['Price with Tax'] = df.apply(lambda row:
     row['Price'] * 1.075
     if row['Is taxed?'] == 'Yes'
     else row['Price'],
     axis=1
)
```
```python
import pandas as pd
df = pd.read_csv('employees.csv')

total_earned = lambda row: (row.hourly_wage * 40) + ((row.hourly_wage * 1.5) * (row.hours_worked - 40)) \
	if row.hours_worked > 40 \
  else row.hourly_wage * row.hours_worked
  
df['total_earned'] = df.apply(total_earned, axis = 1)
print(df)
```

## Renaming Columns : .columns not .column
- When we get our data from other sources, we often want to change the column names
- For example
    - we might want all of the column names to follow variable name rules
    - so that we can use `df.column_name` (which tab-completes) rather than `df['column_name']` (which takes up extra space)

- You can change all of the column names at once by setting the `.columns` property to a different list
- This is great when you need to change all of the column names at once
- but be careful! You can easily mislabel columns if you get the ordering wrong
- Here’s an example:
```python
df = pd.DataFrame({
    'name': ['John', 'Jane', 'Sue', 'Fred'],
    'age': [23, 29, 21, 18]
})
df.columns = ['First Name', 'Age']
```
This command edits the existing DataFrame `df.`

## Renaming Columns II
- You also can rename individual columns by using the `.rename` method
- Pass a dictionary like the one below to the `columns` keyword argument:
```python
{'old_column_name1': 'new_column_name1', 'old_column_name2': 'new_column_name2'}
```
Here’s an example:
```python
df = pd.DataFrame({
    'name': ['John', 'Jane', 'Sue', 'Fred'],
    'age': [23, 29, 21, 18]
})
df.rename(columns={
    'name': 'First Name',
    'age': 'Age'},
    inplace=True)
```
- The code above will rename `name` to `First Name` and `age` to `Age`.
- Using rename with only the columns keyword will create a new DataFrame, leaving your original DataFrame unchanged
- That’s why we also passed in the keyword argument `inplace=True`
- Using `inplace=True` lets us edit the original DataFrame
- There are several reasons why `.rename` is preferable to `.columns`:
    - You can rename just one column
        - using `.columns`, you have to rename all columns
    - You can be specific about which column names are getting changed (with `.column` you can accidentally switch column names if you’re not careful)

- __NOTE__: If you misspell one of the original column names, this command won’t fail. It just won’t change anything.
