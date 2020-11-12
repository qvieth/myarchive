# Data cleaning with Pandas
summary
- different methods to get data into the format for analysis :
    - diagnosing the “tidiness” of the data
    - reshaping the data
    - combining multiple files
    - changing the types of values
    - dropping or filling missing values - how we deal with data that is incomplete or missing
    - manipulating strings to represent the data better

You can use these methods to transform your datasets to be clean and easy to work with!

<!-- vim-markdown-toc GFM -->

* [Diagnose the Data](#diagnose-the-data)
* [Dealing with Multiple Files](#dealing-with-multiple-files)
* [Reshaping your Data](#reshaping-your-data)
* [Dealing with Duplicates](#dealing-with-duplicates)
* [Splitting by Index](#splitting-by-index)
* [Splitting by Character](#splitting-by-character)
* [Looking at Types : df.dtypes](#looking-at-types--dfdtypes)
* [String Parsing](#string-parsing)
* [More String Parsing](#more-string-parsing)
* [Missing Values](#missing-values)
    * [Method 1: drop all of the rows with a missing value](#method-1-drop-all-of-the-rows-with-a-missing-value)
    * [Method 2: fill the missing values with the mean of the column, or with some other aggregate value](#method-2-fill-the-missing-values-with-the-mean-of-the-column-or-with-some-other-aggregate-value)

<!-- vim-markdown-toc -->
- Introduction
- A huge part of data science involves __acquiring raw data__ and __getting it into a form__ ready for analysis
- Some have estimated that :
    - data scientists spend 80% of their time __cleaning__ and __manipulating__ data
    - and only 20% of their time actually __analyzing__ it or __building models__ from it
- When we receive raw data, we have to do a number of things before we’re ready to analyze it, possibly including:
    - diagnosing the “tidiness” of the data — how much data cleaning we will have to do
    - reshaping the data — getting right rows and columns for effective analysis
    - combining multiple files
    - changing the types of values — how we fix a column where numerical values are stored as strings, for example
    - dropping or filling missing values - how we deal with data that is incomplete or missing
    - manipulating strings to represent the data better
- We will go through the techniques data scientists use to accomplish these goals
- by looking at some “unclean” datasets and trying to get them into a good, clean state


## Diagnose the Data
- We often describe data that is easy to analyze and visualize as “tidy data”
- What does it mean to have tidy data?
- __For data to be tidy__, it must have:
    - Each __variable__ as a separate __column__
    - Each __row__ as a separate __observation__
- For example, we would want to reshape a table like:

| Account    | Checkings | Savings |
|------------|-----------|---------|
| “12456543” | 8500      | 8900    |
| “12283942” | 6410      | 8020    |
| “12839485” | 78000     | 92000   |

- Into a table that looks more like:

| Account    | Account Type | Amount |
|------------|--------------|--------|
| “12456543” | “Checking”   | 8500   |
| “12456543” | “Savings”    | 8900   |
| “12283942” | “Checking”   | 6410   |
| “12283942” | “Savings”    | 8020   |
| “12839485” | “Checking”   | 78000  |
| “12839485” | “Savings”    | 920000 |
   	
- The first step of __diagnosing__ whether or not a dataset is tidy
- is using __pandas__ functions to explore and probe the dataset
- You’ve seen most of the functions we often use to diagnose a dataset for cleaning
- Some of the most useful ones are:
    - `.head()` — display the first 5 rows of the table
    - `.info()` — display a summary of the table
    - `.describe()` — display the summary statistics of the table
    - `.columns` — display the column names of the table
    - `.value_counts()` — display the distinct values for a column

## Dealing with Multiple Files
- Often, you have the same data separated out into multiple files
- Let’s say that we have a ton of files following the filename structure: `'file1.csv'`, `'file2.csv'`, `'file3.csv'`, and so on
- The power of pandas is mainly in being able to manipulate large amounts of structured data
- so we want to be able to get all of the relevant information into one table
- so that we can analyze the aggregate data
- We can combine the use of `glob`, a Python library for working with files, with pandas to organize this data better
- `glob` can open multiple files by using regex matching to get the filenames:
```python
import glob
 
files = glob.glob("file*.csv")
 
df_list = []
for filename in files:
  data = pd.read_csv(filename)
  df_list.append(data)
 
df = pd.concat(df_list)
 
print(files)
```
- This code goes through any file that starts with `'file'` and has an extension of `.csv`
- It opens each file, reads the data into a DataFrame, and then concatenates all of those DataFrames together

## Reshaping your Data
- Since we want
    - Each variable as a separate column
    - Each row as a separate __observation__
- We would want to reshape a table like:

| Account    | Checking | Savings |
|------------|----------|---------|
| “12456543” | 8500     | 8900    |
| “12283942” | 6410     | 8020    |
| “12839485” | 78000    | 92000   |

- Into a table that looks more like:

| Account    | Account Type | Amount |
|------------|--------------|--------|
| “12456543” | “Checking”   | 8500   |
| “12456543” | “Savings”    | 8900   |
| “12283942” | “Checking”   | 6410   |
| “12283942” | “Savings”    | 8020   |
| “12839485” | “Checking”   | 78000  |
| “12839485” | “Savings”    | 920000 |
 	
- We can use `pd.melt()` to do this transformation
- `.melt()` takes in a DataFrame, and the columns to unpack:
```python
pd.melt(frame=df, id_vars='name', value_vars=['Checking','Savings'], value_name="Amount", var_name="Account Type")
```
- The parameters you provide are:
    - `frame`: the DataFrame you want to melt
    - `id_vars`: the column(s) of the old DataFrame to preserve
    - `value_vars`: the column(s) of the old DataFrame that you want to turn into variables
    - `value_name`: what to call the column of the new DataFrame that stores the values
    - `var_name`: what to call the column of the new DataFrame that stores the variables
- The default names may work in certain situations, but it’s best to always have data that is self-explanatory
- Thus, we often use `.columns()` to rename the columns after melting:
```python
df.columns(["Account", "Account Type", "Amount"])
```
## Dealing with Duplicates
- Often we see duplicated rows of data in the DataFrames we are working with
- This could happen due to errors in data collection or in saving and loading the data

- To check for duplicates, we can use the pandas function `.duplicated()`, which will return a Series telling us which rows are duplicate rows
- Let’s say we have a DataFrame fruits that represents this table:

| item         | price   | calories |
|--------------|---------|----------|
| “banana”     | “$1”    | 105      |
| “apple”      | “$0.75” | 95       |
| “apple”      | “$0.75” | 95       |
| “peach”      | “$3”    | 55       |
| “peach”      | “$4”    | 55       |
| “clementine” | “$2.5”  | 35       |
     
- If we call `fruits.duplicated()`, we would get the following table:

| id | value |
|----|-------|
| 0  | False |
| 1  | False |
| 2  | True  |
| 3  | False |
| 4  | False |
| 5  | False |

- We can see that row 2, which represents an `"apple"` with price `"$0.75"` and `95` calories, is a duplicate row
- Every value in this row is the same as in another row
- We can use the pandas `.drop_duplicates()` function to remove all rows that are duplicates of another row
- If we call `fruits.drop_duplicates(),` we would get the table:

| item         | price   | calories |
|--------------|---------|----------|
| “banana”     | “$1”    | 105      |
| “apple”      | “$0.75” | 95       |
| “peach”      | “$3”    | 55       |
| “peach”      | “$4”    | 55       |
| “clementine” | “$2.5”  | 35       |

- The `"apple"` row was deleted because it was exactly the same as another row
- But the two `"peach"` rows remain because there is a difference in the price column
- If we wanted to remove every row with a duplicate value in the item column, we could specify a subset:
```python
fruits = fruits.drop_duplicates(subset=['item'])
```
- By default, this keeps the first occurrence of the duplicate:

| item         | price   | calories |
|--------------|---------|----------|
| “banana”     | “$1”    | 105      |
| “apple”      | “$0.75” | 95       |
| “peach”      | “$3”    | 55       |
| “clementine” | “$2.5”  | 35       |

- Make sure that the columns you drop duplicates from are specifically the ones where duplicates don’t belong
- You wouldn’t want to drop duplicates with the price column as a subset, for example, because it’s okay if multiple items cost the same amount!

## Splitting by Index
- In trying to get clean data, we want to make sure each column represents one type of measurement
- Often, multiple measurements are recorded in the same column, and we want to separate these out so that we can do individual analysis on each variable
- Let’s say we have a column “birthday” with data formatted in MMDDYYYY format
- In other words, “11011993” represents a birthday of November 1, 1993
- We want to split this data into day, month, and year so that we can use these columns as separate features
- In this case, we know the exact structure of these strings
- The first two characters will always correspond to the month, the second two to the day, and the rest of the string will always correspond to year
- We can easily break the data into three separate columns by splitting the strings using .str:
```python
# Create the 'month' column
df['month'] = df.birthday.str[0:2]
 
# Create the 'day' column
df['day'] = df.birthday.str[2:4]
 
# Create the 'year' column
df['year'] = df.birthday.str[4:]
```
- The first command takes the first two characters of each value in the `birthday` column and puts it into a `month` column
- The second command takes the second two characters of each value in the `birthday` column and puts it into a `day` column
- The third command takes the rest of each value in the `birthday` column and puts it into a `year` column
- This would transform a table like:

| id   | birthday   |
|------|------------|
| 1011 | “12241989” |
| 1112 | “10311966” |
| 1113 | “01052011” |

- into a table like:


| id   | birthday   | month | day  | year   |
|------|------------|-------|------|--------|
| 1011 | “12241989” | “12”  | “24” | “1989” |
| 1112 | “10311966” | “10”  | “31” | “1966” |
| 1113 | “01052011” | “01”  | “05” | “2011” |
	   		
- We will practice changing string columns into numerical columns (like converting "10" to 10) in a future exercise

## Splitting by Character
- Let’s say we have a column called “type” with data entries in the format `"admin_US"` or `"user_Kenya"`
- Just like we saw before, this column actually contains two types of data
- One seems to be the user type (with values like “admin” or “user”) and one seems to be the country this user is in (with values like “US” or “Kenya”)
- We can no longer just split along the first 4 characters because `admin` and `user` are of different lengths
- Instead, we know that we want to split along the `"_"`
- Using that, we can split this column into two separate, cleaner columns:
```python
# Create the 'str_split' column
df['str_split'] = df.type.str.split('_')
 
# Create the 'usertype' column
df['usertype'] = df.str_split.str.get(0)
 
# Create the 'country' column
df['country'] = df.str_split.str.get(1)
```
- This would transform a table like:

| id   | type           |
|------|----------------|
| 1011 | “user_Kenya”   |
| 1112 | “admin_US”     |
| 1113 | “moderator_UK” |
 	
- into a table like:

| id   | type           | country | usertype    |
|------|----------------|---------|-------------|
| 1011 | “user_Kenya”   | “Kenya” | “user”      |
| 1112 | “admin_US”     | “US”    | “admin”     |
| 1113 | “moderator_UK” | “UK”    | “moderator” |
	  	
## Looking at Types : df.dtypes
- Each column of a DataFrame can hold items of the same data type or dtype
- The dtypes that pandas uses are: float, int, bool, datetime, timedelta, category and object
- Often, we want to convert between types so that we can do better analysis
- If a numerical category like `"num_users"` is stored as a Series of `objects` instead of `ints`
- for example, it makes it more difficult to do something like make a line graph of users over time
- To see the types of each column of a DataFrame, we can use:
```python
print(df.dtypes)
```
- For a DataFrame like this:

| item         | price   | calories |
|--------------|---------|----------|
| “banana”     | “$1”    | 105      |
| “apple”      | “$0.75” | 95       |
| “peach”      | “$3”    | 55       |
| “clementine” | “$2.5”  | 35       |

- the `.dtypes` attribute would be:

```
item        object
price       object
calories     int64
dtype: object
```
- We can see that the `dtype` of the `dtypes` attribute itself is an `object`! 
- It is a `Series` object, which you have already worked with
- Series objects compose all DataFrames

- We can see that the `price` column is made up of `object`s, which will probably make our analysis of price more difficult
- We’ll look at how to convert columns into numeric values in the next few exercises

## String Parsing
- Sometimes we need to __modify strings__ in our DataFrames to help us transform them into more meaningful metrics
- For example, in our fruits table from before:


| item         | price   | calories |
|--------------|---------|----------|
| “banana”     | “$1”    | 105      |
| “apple”      | “$0.75” | 95       |
| “peach”      | “$3”    | 55       |
| “peach”      | “$4”    | 55       |
| “clementine” | “$2.5”  | 35       |

- We can see that the `'price'` column is actually composed of strings representing dollar amounts
- This column could be much better represented in floats
- so that we could take the mean, calculate other aggregate statistics
- or compare different fruits to one another in terms of price

- First, we can use what we know of __regex__ to get rid of all of the dollar signs:
```python
fruit.price = fruit['price'].replace('[\$,]', '', regex=True)
```
- Then, we can use the pandas function `.to_numeric()` to convert strings containing numerical values to integers or floats:
```python
fruit.price = pd.to_numeric(fruit.price)
```
- Now, we have a DataFrame that looks like:

| item         | price | calories |
|--------------|-------|----------|
| “banana”     | 1     | 105      |
| “apple”      | 0.75  | 95       |
| “peach”      | 3     | 55       |
| “peach”      | 4     | 55       |
| “clementine” | 2.5   | 35       |

## More String Parsing
- Sometimes we want to do analysis on numbers that are hidden within string values
- We can use regex to extract this numerical data from the strings they are trapped in
- Suppose we had this DataFrame `df` representing a workout regimen:


| date       | exerciseDescription       |
|------------|---------------------------|
| 10/18/2018 | “lunges - 30 reps”        |
| 10/18/2018 | “squats - 20 reps”        |
| 10/18/2018 | “deadlifts - 25 reps”     |
| 10/18/2018 | “jumping jacks - 30 reps" |
| 10/19/2018 | “lunges - 40 reps”        |
| 10/19/2018 | “chest flyes - 15 reps”   |
| …          | …                         |
  
- It would be helpful to separate out data like `"30 lunges"` into 2 columns with the number of reps, `"30"`, and the type of exercise, `"lunges"`
- Then, we could compare the increase in the number of lunges done over time, for example :
    - To extract the numbers from the string we can use pandas’ `.str.split()` function:
```python
split_df = df['exerciseDescription'].str.split('(\d+)', expand=True)
```
- which would result in this DataFrame split_df:

| * * | 0                  | 1    | 2      |
|-----|--------------------|------|--------|
| 0   | “lunges - “        | “30” | “reps” |
| 1   | “squats - “        | “20” | “reps” |
| 2   | “deadlifts - “     | “25” | “reps” |
| 3   | “jumping jacks - “ | “30” | “reps” |
| 4   | “lunges - “        | “40” | “reps” |
| 5   | “chest flyes - “   | “15” | “reps” |
| …   | …                  | …    | …      |

- Then, we can assign columns from this DataFrame to the original `df`:
```python
df.reps = pd.to_numeric(split_df[1])
df.exercise = split_df[2].replace('[\- ]', '', regex=True)
```

- Now, our `df` looks like this:

| date       | exerciseDescription       | reps | exercise       |
|------------|---------------------------|------|----------------|
| 10/18/2018 | “lunges - 30 reps”        | 30   | “lunges”       |
| 10/18/2018 | “squats - 20 reps”        | 20   | “squats”       |
| 10/18/2018 | “deadlifts - 25 reps”     | 25   | “deadlifts”    |
| 10/18/2018 | “jumping jacks - 30 reps” | 30   | “jumping jacks |
| 10/19/2018 | “lunges - 40 reps”        | 40   | “lunges”       |
| 10/19/2018 | “chest flyes - 15 reps”   | 15   | “chest flyes”  |
| …          | …                         | …    | …              |

## Missing Values
- We often have data with missing elements, as a result of a problem with the data collection process or errors in the way the data was stored
- The missing elements normally show up as NaN (or Not a Number) values:


| day   | bill  | tip | num_guests |
|-------|-------|-----|------------|
| “Mon” | 10.1  | 1   | 1          |
| “Mon” | 20.75 | 5.5 | 2          |
| “Tue” | 19.95 | 5.5 | NaN        |
| “Wed” | 44.10 | 15  | 3          |
| “Wed” | NaN   | 1   | 1          |

- The `num_guests` value for the 3rd row is missing, and the `bill` value for the 5th row is missing
- Some calculations we do will just skip the `NaN` values, but some calculations or visualizations we try to perform will break when a `NaN` is encountered

- Most of the time, we use one of two methods to deal with missing values
### Method 1: drop all of the rows with a missing value
- We can use `.dropna()` to do this:
```python
bill_df = bill_df.dropna()
```
- This command will result in the DataFrame without the incomplete rows:


| day   | bill  | tip | num_guests |
|-------|-------|-----|------------|
| “Mon” | 10.1  | 1   | 1          |
| “Mon” | 20.75 | 5.5 | 2          |
| “Wed” | 44.10 | 15  | 3          |

- If we wanted to remove every row with a `NaN` value in the num_guests column only, we could specify a `subset`:
```python
bill_df = bill_df.dropna(subset=['num_guests'])
```
### Method 2: fill the missing values with the mean of the column, or with some other aggregate value
- We can use `.fillna()` to do this:
```python
bill_df = bill_df.fillna(value={"bill":bill_df.bill.mean(), "num_guests":bill_df.num_guests.mean()})
```
- This command will result in the DataFrame with the respective mean of the column in the place of the original `NaN`s:

| day   | bill   | tip | num_guests |
|-------|--------|-----|------------|
| “Mon” | 10.1   | 1   | 1          |
| “Mon” | 20.75  | 5.5 | 2          |
| “Tue” | 19.95  | 5.5 | 1.75       |
| “Wed” | 44.10  | 15  | 3          |
| “Wed” | 23.725 | 1   | 1          |
     
