# Seaborn
<!-- vim-markdown-toc GFM -->

* [Using Pandas For Seaborn](#using-pandas-for-seaborn)
* [Plotting Bars with Seaborn](#plotting-bars-with-seaborn)
* [Understanding Aggregates](#understanding-aggregates)
* [Plotting Aggregates](#plotting-aggregates)
* [Modifying Error Bars](#modifying-error-bars)
* [Calculating Different Aggregates](#calculating-different-aggregates)
* [Aggregating by Multiple Columns](#aggregating-by-multiple-columns)

<!-- vim-markdown-toc -->
- To review the seaborn workflow:
1. Ingest data from a CSV file to Pandas DataFrame.
```python
df = pd.read_csv('file_name.csv')
```
2. Set sns.barplot() with desired values for x, y, and set data equal to your DataFrame.
```python
sns.barplot(data=df, x='X-Values', y='Y-Values')
```
3. Set desired values for estimator and hue parameters.
```python
sns.barplot(data=df, x='X-Values', y='Y-Values', estimator=len, hue='Value')
```
4. Render the plot using plt.show().
```python
plt.show()
```
- In this lesson, you’ll learn how to use Seaborn to create bar charts for statistical analysis
- In this lesson you learned how to extend Matplotlib with Seaborn to create meaningful visualizations from data in DataFrames
- You’ve also learned how Seaborn creates aggregated charts and how to change the way aggregates and error bars are calculated
- Finally, you learned how to aggregate by multiple columns, and how the hue parameter adds a nested categorical variable to a visualization
- Seaborn is a Python data visualization library that provides simple code to create elegant visualizations for statistical exploration and insight

- Seaborn is based on Matplotlib, but improves on Matplotlib in several ways:
    - Seaborn provides a more visually appealing plotting style and concise syntax
    - Seaborn natively understands Pandas DataFrames, making it easier to plot data directly from CSVs
    - Seaborn can easily summarize Pandas DataFrames with many rows of data into aggregated charts
- If you’re unfamiliar with Pandas
    - just know that Pandas is a data analysis library for Python
    - that provides easy-to-use data structures and allows you to organize and manipulate datasets so they can be visualized
- To fully leverage the power of Seaborn, it is best to prepare your data using Pandas
- Over the next few exercises, we will explain how Seaborn relates to Pandas and how we can transform massive datasets into easily understandable graphics

## Using Pandas For Seaborn
- Throughout this lesson, you’ll use Seaborn to visualize a Pandas DataFrame
- DataFrames contain data structured into rows and columns
    - DataFrames look similar to other data tables you may be familiar with
    - but they are designed specifically to be used with Python

- You can create a DataFrame from a local CSV file (CSV files store data in a tabular format)
- To create a DataFrame from a local CSV file you would use the syntax:
```python
df = pd.read_csv('file_name.csv')
```
- The code above creates a DataFrame saved to a variable named df
- The data inside of the df DataFrame comes from the data in the local CSV file named file_name.csv.

## Plotting Bars with Seaborn
- Take a look at the file called results.csv
- You’ll plot that data soon
    - but before you plot it, take a minute to understand the context behind that data
    - which is based on a hypothetical situation we have created:
- Suppose we are analyzing data from a survey: we asked 1,000 patients at a hospital how satisfied they were with their experience
    - Their response was measured on a scale of 1 - 10, with 1 being extremely unsatisfied, and 10 being extremely satisfied
    - We have summarized that data in a CSV file called results.csv

- To plot this data using Matplotlib, you would write the following:
```python
df = pd.read_csv("results.csv")
ax = plt.subplot()
plt.bar(range(len(df)),
        df["Mean Satisfaction"])
ax.set_xticks(range(len(df)))
ax.set_xticklabels(df.Gender)
plt.xlabel("Gender")
plt.ylabel("Mean Satisfaction")
```
- That’s a lot of work for a simple bar chart! Seaborn gives us a much simpler option
- With Seaborn, you can use the sns.barplot() command to do the same thing

- The Seaborn function sns.barplot(), takes at least three keyword arguments:
    - data: a Pandas DataFrame that contains the data (in this example, data=df)
    - x: a string that tells Seaborn which column in the DataFrame contains other x-labels (in this case, x="Gender")
    - y: a string that tells Seaborn which column in the DataFrame contains the heights we want to plot for each bar (in this case y="Mean Satisfaction")

- By default, Seaborn will aggregate and plot the mean of each category
- In the next exercise you will learn more about aggregation and how Seaborn handles it
- exercise code :
```python
import seaborn as sns

# Load results.csv here:
df = pd.read_csv('results.csv')
print(df)

sns.barplot(
	data=df,
	x='Gender',
	y='Mean Satisfaction'
)

plt.show()
```
## Understanding Aggregates
- Seaborn can also calculate __aggregate statistics__ for large datasets
- To understand why this is helpful, we must first understand what __an aggregate__ is

- An aggregate statistic, or aggregate, is a __single number__ used to describe a set of data
- One example of an aggregate is the average, or mean of a data set
- There are many other aggregate statistics as well

- Suppose we have a grade book with columns student, assignment_name, and grade, as shown below


| student | assignment_name | grade |
|---------|-----------------|-------|
| Amy     | Assignment 1    | 75    |
| Amy     | Assignment 2    | 82    |
| Bob     | Assignment 1    | 99    |
| Bob     | Assignment 2    | 90    |
| Chris   | Assignment 1    | 72    |
| Chris   | Assignment 2    | 66    |
| …       | …               | …     |

- To calculate a student’s current grade in the class, we need to aggregate the grade data by student
- To do this, we’ll calculate the average of each student’s grades, resulting in the following data set:

| student | grade |
|---------|-------|
| Amy     | 78.5  |
| Bob     | 94.5  |
| Chris   | 69    |
| …       | …     |
 	
- On the other hand, we may be interested in understanding the relative difficulty of each assignment
- In this case, we would aggregate by assignment, taking the average of all student’s scores on each assignment:

| assignment_name | grade |
|-----------------|-------|
| Assignment 1    | 82    |
| Assignment 2    | 79.3  |
| …               | …     |

- In both of these cases, the function we used to aggregate our data was the average or mean, but there are many types of aggregate statistics including:
    - Median
    - Mode
    - Standard Deviation
- In Python, you can compute aggregates fairly quickly and easily using Numpy, a popular Python library for computing
- You’ll use Numpy in this exercise to compute aggregates for a DataFrame

```python
import pandas as pd
from matplotlib import pyplot as plt
import numpy as np

gradebook = pd.read_csv('gradebook.csv')
print(gradebook)

assignment1 = gradebook[gradebook.assignment_name == 'Assignment 1']
print(assignment1)

asn1_median = np.median(assignment1.grade)
print(asn1_median)
```
## Plotting Aggregates
- Recall our gradebook from the previous exercise:

| student | assignment_name | grade |
|---------|-----------------|-------|
| Amy     | Assignment 1    | 75    |
| Amy     | Assignment 2    | 82    |
| Bob     | Assignment 1    | 99    |
| Bob     | Assignment 2    | 90    |
| Chris   | Assignment 1    | 72    |
| Chris   | Assignment 2    | 66    |
| …       | …               | …     |

- Suppose this data is stored in a Pandas DataFrame called df

- The same Seaborn command that you previously learned (sns.barplot()) will plot this data in a bar plot and automatically aggregate the data:
```python
sns.barplot(data=df, x="student", y="grade")
```
- In the example above, Seaborn will aggregate grades by student, and plot the average grade for each student
- exercise code :
```python
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns

gradebook = pd.read_csv("gradebook.csv")

sns.barplot(data=gradebook, x="assignment_name", y="grade")

plt.show()
```
## Modifying Error Bars
- By default, Seaborn will place error bars on each bar when you use the barplot() function
- Error bars are the small lines that extend above and below the top of each bar
- Errors bars visually indicate the range of values that might be expected for that bar

- For example, in our assignment average example, an error bar might indicate what grade we expect an average student to receive on this assignment

- There are several different calculations that are commonly used to determine error bars

- By default, Seaborn uses something called a bootstrapped confidence interval
- Roughly speaking, this interval means that “based on this data, 95% of similar situations would have an outcome within this range”

- In our gradebook example, the confidence interval for the assignments means
    - “if we gave this assignment to many, many students,
        - we’re confident that the mean score on the assignment
        - would be within the range represented by the error bar”

- The confidence interval is a nice error bar measurement
    - because it is defined for different types of aggregate functions, such as medians and mode, in addition to means

- If you’re calculating a mean and would prefer to use standard deviation for your error bars
    - you can pass in the keyword argument ci="sd" to sns.barplot()
        - which will represent one standard deviation
- It would look like this:
```python
sns.barplot(data=gradebook, x="name", y="grade", ci="sd")
```
```python
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns

gradebook = pd.read_csv("gradebook.csv")

sns.barplot(data=gradebook, x="name", y="grade", ci="sd")
plt.show()
```
## Calculating Different Aggregates
- In most cases, we’ll want to plot the mean of our data, but sometimes, we’ll want something different:
    - If our data has many outliers, we may want to plot the median.
    - If our data is categorical, we might want to count how many times each category appears (such as in the case of survey responses).
- Seaborn is flexible and can calculate any aggregate you want
- To do so, you’ll need to use the keyword argument estimator, which accepts any function that works on a list

- For example, to calculate the median, you can pass in np.median to the estimator keyword:
```python
sns.barplot(data=df,
  x="x-values",
  y="y-values",
  estimator=np.median)
```
- Consider the data in results.csv
- To calculate the number of times a particular value appears in the Response column , we pass in len:
```python
sns.barplot(data=df,
  x="Patient ID",
  y="Response",
  estimator=len)
```
## Aggregating by Multiple Columns
- Sometimes we’ll want to aggregate our data by multiple columns to visualize nested categorical variables
- For example, consider our hospital survey data
- The mean satisfaction seems to depend on Gender, but it might also depend on another column: Age Range

- We can compare both the Gender and Age Range factors at once by using the keyword hue
```python
sns.barplot(data=df,
            x="Gender",
            y="Response",
            hue="Age Range")
```
- The hue parameter adds a nested categorical variable to the plot
- *Visualizing survey results by gender with age range nested*
- Notice that we keep the same x-labels, but we now have different color bars representing each Age Range
- We can compare two bars of the same color to see how patients with the same Age Range, but different Gender rated the survey
```python
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns

df = pd.read_csv("survey.csv")

sns.barplot(data=df,
            x="Age Range",
            y="Response",
            hue="Gender")

plt.show()
```
