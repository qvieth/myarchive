## Learn Seaborn: Distributions
- other lessons : seaborn styling and coloring(able to work with pallete)
Review
- In this lesson, we examined how Seaborn has several plots that can visualize __distributions__ 
- While __bar plots__ can display __basic aggregates__
    - __KDE plots, dist plots, box plots and violin plots__ can show us __distributions__ and other information
        - `KDE plot` - Kernel density estimator; shows a smoothed version of dataset. Use `sns.kdeplot()`
        - `Box plot` - A classic statistical model that shows the median, interquartile range, and outliers. Use `sns.boxplot()`
        - `Violin plot` - A combination of a KDE and a box plot. Good for showing multiple distributions at a time. Use `sns.violinplot()`

Introduction
- In this lesson, we will explore how to use Seaborn to graph multiple statistical distributions, including box plots and violin plots
- Seaborn is optimized to work with large datasets 
    - from its ability to natively interact with Pandas DataFrames
    - to __automatically calculating__ and __plotting aggregates__
        - One of the most powerful aspects of Seaborn is its ability to visualize and compare distributions
        - Distributions provide us with more information about our data — how spread out it is, its range, etc.
- Calculating and graphing distributions is integral to analyzing massive amounts of data
- We’ll look at how Seaborn allows us to move beyond the traditional distribution graphs to plots that enable us to communicate important statistical information

- [Seaborn API reference](https://seaborn.pydata.org/api.html) : 
    - In this documentation, you will learn the many elements of the Seaborn API
    - This is helpful if you wish to use Seaborn to visualize data in plots and grids 
## Plotting Distributions with Seaborn
- Standard deviation and bootstrapped confidence intervals are two measurements that can be used for: error bars
    - To change how error bars are calculated you can use the keyword ci. `ci="sd"`
    - for example would set the error bars to be calculated using standard deviation
= Jupyter
- Seaborn's strength is in visualizing statistical calculations
- Seaborn includes several plots that allow you to graph univariate distribution, including KDE plots, box plots, and violin plots
- Explore the Jupyter notebook below to get an understanding of how each plot works
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
- First, we'll read in three datasets
- In order to plot them in Seaborn, we'll combine them using NumPy's .concatenate() function into a Pandas DataFrame.
```python
n = 500
dataset1 = np.genfromtxt("dataset1.csv", delimiter=",")
dataset2 = np.genfromtxt("dataset2.csv", delimiter=",")
dataset3 = np.genfromtxt("dataset3.csv", delimiter=",")


df = pd.DataFrame({
    "label": ["set_one"] * n + ["set_two"] * n + ["set_three"] * n,
    "value": np.concatenate([dataset1, dataset2, dataset3])
})

sns.set()
```
- First, let's plot each dataset as bar charts.
```python
sns.barplot(data=df, x='label', y='value')
plt.show()
```
- We can use barplots to find out information about the mean 
    - but it doesn't give us a sense of how spread out the data is in each set
- To find out more about the distribution, we can use a KDE plot
```python
sns.kdeplot(dataset1, shade=True, label="dataset1")
sns.kdeplot(dataset2, shade=True, label="dataset2")
sns.kdeplot(dataset3, shade=True, label="dataset3")

plt.legend()
plt.show()
```
- A KDE plot will give us more information, but it's pretty difficult to read this plot
```python
sns.boxplot(data=df, x='label', y='value')
plt.show()
```
- A box plot, on the other hand, makes it easier for us to compare distributions
- It also gives us other information, like the interquartile range and any outliers
- However, we lose the ability to determine the shape of the data
```python
sns.violinplot(data=df, x="label", y="value")
plt.show()
```
- A violin plot brings together shape of the KDE plot with additional information that a box plot provides
- It's understandable why many people like this plot!

## Bar Charts Hide Information
- Before we dive into these new charts, we need to understand why we’d want to use them
- To best illustrate this idea, we need to revisit bar charts

- We previously learned that Seaborn can quickly aggregate data to plot bar charts using the mean

- Here is a bar chart that uses three different randomly generated sets of data:
```python
sns.barplot(data=df, x="label", y="value")
plt.show()
```
```image
!alt
```
- These three datasets look identical! As far as we can tell, they each have the same mean and similar confidence intervals

- We can get a lot of information from these bar charts, but we can’t get everything
- For example, what are the minimum and maximum values of these datasets? How spread out is this data?

- While we may not see this information in our bar chart, these differences might be significant and worth understanding better

## KDE Plots, Part I
- Bar plots can tell us what the mean of our dataset is, but they don’t give us any hints as to the distribution of the dataset values
- For all we know, the data could be clustered around the mean or spread out evenly across the entire range

- To find out more about each of these datasets, we’ll need to examine their distributions
- A common way of doing so is by plotting the data as a histogram, but histograms have their drawback as well

- Seaborn offers another option for graphing distributions: KDE Plots

- __KDE__ stands for __Kernel Density Estimator__
- A __KDE plot__ gives us the sense of a univariate as a curve
- A univariate dataset only has one variable and is also referred to as being one-dimensional
    - as opposed to bivariate or two-dimensional datasets which have two variables

- KDE plots are preferable to histograms
    - because depending on how you group the data into bins and the width of the bins
    - you can draw wildly different conclusions about the shape of the data
- Using a KDE plot can mitigate these issues
    - because they smooth the datasets
    - allow us to generalize over the shape of our data
    - and aren’t beholden to specific data points

## KDE Plots, Part II
- To plot a KDE in Seaborn, we use the method sns.kdeplot()

- A KDE plot takes the following arguments:
    - data - the univariate dataset being visualized, like a Pandas DataFrame, Python list, or NumPy array
    - shade - a boolean that determines whether or not the space underneath the curve is shaded

- Let’s examine the KDE plots of our three datasets:
```python
sns.kdeplot(dataset1, shade=True)
sns.kdeplot(dataset2, shade=True)
sns.kdeplot(dataset3, shade=True)
plt.legend()
plt.show()
```
```image
!alt
```
- Notice that when using a KDE we need to plot each of the original datasets separately, rather than using a combined dataframe like we did with the bar plot

- It looks like there are some big differences between the three datasets:
    - Dataset 1 is skewed left
    - Dataset 2 is normally distributed
    - Dataset 3 is bimodal (it has two peaks)

- So although all three datasets have roughly the same mean, the shapes of the KDE plots demonstrate the differences in how the values are distributed

## Box Plots, Part I
- While a KDE plot can tell us about the shape of the data, it’s cumbersome to compare multiple KDE plots at once
- They also can’t tell us other statistical information, like the values of outliers

- The box plot (also known as a box-and-whisker plot)
    - can’t tell us about how our dataset is distributed
    - like a KDE plot
- But it shows us the range of our dataset
    - gives us an idea about where a significant portion of our data lies
    - and whether or not any outliers are present

- Let’s examine how we interpret a box plot:
    - The __box__ represents the interquartile range
    - The __line__ in the middle of the box is the median
    - The __end lines__ are the first and third quartiles
    - The __diamonds__ show outliers

## Box Plots, Part II
- One advantage of the box plot over the KDE plot is that in Seaborn, it is easy to plot multiples and compare distributions

- Let’s look again at our three datasets, and how they look plotted as box plots:
```python
sns.boxplot(data=df, x='label', y='value')
plt.show()
```
```image
!alt
```
- The box plot does a good job of showing certain differences
    - the different between Dataset 1 and Dataset 2
    - however, it does not show that Dataset 3 is bimodal

- To plot a box plot in Seaborn, we use the method `sns.boxplot()`

- A box plot takes the following arguments:
    - `data` - the dataset we’re plotting, like a DataFrame, list, or an array
    - `x` - a one-dimensional set of values, like a Series, list, or array
    - `y` - a second set of one-dimensional data

- If you use a Pandas Series for the `x` and `y` values, the Series will also generate the axis labels
- For example, if you use the `value` Series as your `y` value data, Seaborn will automatically apply that name as the y-axis label

## Violin Plots, Part I
- As we saw in the previous exercises, while it’s possible to plot multiple histograms, it is not a great option for comparing distributions
- Seaborn gives us another option for comparing distributions - a violin plot
- Violin plots provide more information than box plots because instead of mapping each individual data point, we get an estimation of the dataset thanks to the KDE

- Violin plots are less familiar and trickier to read, so let’s break down the different parts:
    - There are two KDE plots that are symmetrical along the center line
    - A white dot represents the median
    - The thick black line in the center of each violin represents the interquartile range
    - The lines that extend from the center are the confidence intervals - just as we saw on the bar plots, a violin plot also displays the 95% confidence interval

## Violin Plots, Part II
- Violin Plots are a powerful graphing tool that allows you to compare multiple distributions at once
- Let’s look at how our original three data sets look like as violin plots:
```python
sns.violinplot(data=df, x="label", y="value")
plt.show()
```
```image
!alt
```

- As we can see, violin plots allow us to graph and compare multiple distributions
- It also retains the shape of the distributions, so we can easily tell that Dataset 1 is skewed left and that Dataset 3 is bimodal

- To plot a violin plot in Seaborn, use the method `sns.violinplot()`

- There are several options for passing in relevant data to the `x` and `y` parameters:
    - `data` - the dataset that we’re plotting, such as a list, DataFrame, or array
    - `x`, `y`, and `hue` - a one-dimensional set of data, such as a Series, list, or array
    - any of the parameters to the function `sns.boxplot()`
