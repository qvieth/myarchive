# Summarizing Quantiative Data
- If you are interested in learning more about these topics, here are some additional resources:
    - Article:
        - [Statistics in NumPy](https://numpy.org/doc/stable/reference/routines.statistics.html?highlight=statistics)
        - [Pandas - Descriptive Statistics](https://www.tutorialspoint.com/python_pandas/python_pandas_descriptive_statistics.htm)
        - [Descriptive Statistics using Pandas and Seaborn](https://towardsdatascience.com/a-quick-guide-on-descriptive-statistics-using-pandas-and-seaborn-2aadc7395f32)
- __Statistics__ is concerned with developing and studying about data
    - with __different methods__ of : 
        1. collecting
        2. analyzing
        3. and presenting
    - Two fundamental ideas in the field of statistics are
        1. uncertainty : `Probability` is a mathematical language used to discuss uncertain events
        2. variation
- __Descriptive statistics__ describes data (for example, a chart or graph)
- while __Inferential statistics__ allows you to make predictions (“inferences”) from that data
    - with inferential statistics, you take data from __samples__ and __make a guess or draw a conclusion__ about a population 
- For example :
    - you might stand in a mall and ask a sample of 100 people if they like shopping at Sears
        - you could make a bar chart of yes or no answers (that would be __descriptive statistics__)
        - or you could use your research (and __inferential statistics__)
            - to reason that around 75-80% of the population (all shoppers in all malls) like shopping at Sears
- There are two main areas of __inferential statistics__:
    - __Estimating parameters__ : This means taking a __statistic (a fact or piece of data from a study of a large quantity of numerical data)__ from your sample data
        - for example : the sample mean and using it to say something about a population parameter (i.e. the population mean)
    - __Hypothesis tests__ : This is where you can use sample data to answer research questions
        - for example, you might be interested in knowing if a new cancer drug is effective
            - Or if breakfast helps children perform better in schools
- standard __analysis tools__ of __inferential statistics__ :
    - hypothesis testing
    - confidence intervals(CIs)
    - __regression__ analysis
<!-- vim-markdown-toc GFM -->

* [Mean](#mean)
    * [NumPy Average](#numpy-average)
* [Median](#median)
    * [NumPy Median](#numpy-median)
* [Mode](#mode)
    * [SciPy Mode](#scipy-mode)
* [Variance : the whole point of calculating variance is to get one number that describes the dataset](#variance--the-whole-point-of-calculating-variance-is-to-get-one-number-that-describes-the-dataset)
    * [Distance From Mean](#distance-from-mean)
    * [Average Distances](#average-distances)
    * [Square The Differences](#square-the-differences)
    * [Variance In NumPy](#variance-in-numpy)
    * [Variance Summary : all about how spread](#variance-summary--all-about-how-spread)
* [Standard Deviation](#standard-deviation)
    * [Standard Deviation in NumPy](#standard-deviation-in-numpy)
    * [Using Standard Deviation](#using-standard-deviation)
    * [Review](#review)
* [Histogram](#histogram)
    * [Range](#range)
    * [Bins and Count I](#bins-and-count-i)
        * [Bins](#bins)
        * [Count](#count)
    * [Numpy Histograms](#numpy-histograms)
    * [Plotting a Histogram](#plotting-a-histogram)
    * [Finding your Best Bin Size](#finding-your-best-bin-size)
* [Describe a Histogram](#describe-a-histogram)
    * [Center](#center)
    * [Spread](#spread)
    * [Skew : symmetric, right-skewed, left-skewed](#skew--symmetric-right-skewed-left-skewed)
    * [Modality : unimodal, bimodal, multimodal, uniform distribution](#modality--unimodal-bimodal-multimodal-uniform-distribution)
    * [Outliers](#outliers)
* [Quartiles, Quantiles, Interquartiles Range, Boxplot](#quartiles-quantiles-interquartiles-range-boxplot)

<!-- vim-markdown-toc -->

- __Descriptive statistics__ is a study of data analysis to __describe__, __summarize__ data in a meaningful way ,involves the calculation of various measures such as :
    - the measure of center
    - the measure of variability, percentiles
    - and also the construction of tables & graphs
- Various methods of summarizing quantitative data :
    - Calculate and interpret summary statistics for central tendency, such as mean, median, and mode
    - Calculate and interpret summary statistics for spread, such as standard deviation, variance, range, and interquartile range
    - Learn about a distribution by calculating quantiles and percentiles
    - Visually inspect and interpret a distribution of data using histograms and box plots
## Mean
- `data = [4, 6, 2, 8]`
- The total is equal to `20`, and the number of __observations__ is equal to `4`
- The __average__ or __mean__ of this dataset is equal to 5.

### NumPy Average
- The NumPy `.average()` or `.mean()` function can do the work of adding and dividing for you
- In the example below, we use `np.average()` to calculate the average of a dataset with ten values
```python
example_array = np.array([24, 16, 30, 10, 12, 28, 38, 2, 4, 36])
example_average = np.average(example_array)
print(example_average)
```
- The code above calculates the average of `example_array` and saves the value to `example_average`
- The resulting average of this array is `20`

## Median
- Say we have a dataset with the following ten numbers:
- `24, 16, 30, 10, 12, 28, 38, 2, 4, 36`
- The first step is to order these numbers from smallest to largest:
- `2, 4, 10, 12, [16, 24], 28, 30, 36, 38`
- Because this dataset has an even number of values :
    - there are __two medians__: `16` and `24` 
        - 16 has four datapoints to the left
        - 24 has four datapoints to the right
- Although you can report both values as the median, people often __average__ them
- If you averaged `16` and `24`, you could report the median as `20`
- If we added another value (say, `24`) to the dataset and sorted it, we would have:
- `2, 4, 10, 12, 16, [24], 24, 28, 30, 36, 38`
- The new median is equal to `24`, because there are 5 values to the left of it, and 5 values to the right of it

### NumPy Median
- The NumPy `.median()` function can do the work of sorting, then finding the median for you
- In the example below, we use `np.median()` to calculate the median of a dataset with ten values:
```python
example_array = np.array([24, 16, 30, 10, 12, 28, 38, 2, 4, 36, 42])
example_median = np.median(example_array)
print(example_median)
```
- The code above prints the __median__ of the dataset, `24`
- The mean of this dataset is `22`
- It’s worth noting these two values are close to one another, but not equal

## Mode
- The formal definition for the mode of a dataset is:
    - The most frequently occurring observation in the dataset
    - A dataset can have __multiple modes__ if there is __more than one value with the same maximum frequency__
- Example
    - Say we have a dataset with the following ten numbers:
        - `24, 16, 12, 10, 12, 28, 38, 12, 28, 24`
- Let’s find the frequency of each number:

| 24 | 16 | 12 | 10 | 28 | 38 |
|----|----|----|----|----|----|
| 2  | 1  | 3  | 1  | 2  | 1  |

- From the table, we can see that our mode is 12, the most frequent number in our dataset

###  SciPy Mode
- import `stats` then use `stats.mode()` to calculate the mode of a dataset with ten values:
- Example: One Mode
```python
from scipy import stats
example_array = np.array([24, 16, 12, 10, 12, 28, 38, 12, 28, 24])
example_mode = stats.mode(example_array)
```
```
>>> example_mode
ModeResult(mode=array([12]), count=array([3]))
```

- Example: Two Modes
```python
from scipy import stats
example_array = np.array([24, 16, 12, 10, 12, 24, 38, 12, 28, 24])
example_mode = stats.mode(example_array)
```
```
>>> example_mode
ModeResult(mode=array([12]), count=array([3]))
```
- If there are multiple modes, the stats.mode() function will always return the __smallest__ mode in the dataset.

## Variance : the whole point of calculating variance is to get one number that describes the dataset
- Finding the mean, median, and mode of a dataset is a good way to start getting an understanding of the general shape of your data
- However, those three descriptive statistics only tell part of the story. Consider the two datasets below:
```
dataset_one = [-4, -2, 0, 2, 4]
dataset_two = [-400, -200, 0, 200, 400]
```
- These two datasets have the same mean and median — both of those values happen to be 0
- If we only reported these two statistics, we would not be communicating any meaninful difference between these two datasets
- This is where variance comes into play
- Variance is a descriptive statistic that describes __how spread out__ the points in a __data set__ are

### Distance From Mean
- Now that you have learned the importance of describing the spread of a dataset
- let’s figure out how to mathematically compute this number
- How would you attempt to capture the spread of the data in a single number?
- Let’s start with our intuition 
- we want the __variance of a dataset__ to be a __large number__ if the data is __spread__ out, and a __small number__ if the data is __close__ together

- A lot of people may initially consider using the range of the data
- But that only considers two points in your entire dataset
- Instead, we can include every point in our calculation by finding __the difference between every data point and the mean__
- If the data is __close together__
    - then each data point will tend to be __close__ to the __mean__ and the difference will be __small__
- If the data is __spread out__
    - the difference between every data point and the __mean__ will be __larger__
- Mathematically, we can write this comparison as `difference=X−μ`
    - Where X is a single data point and the Greek letter mu is the mean. 

### Average Distances
- We now have five different values that describe how far away each point is from the mean
- That seems to be a good start in describing the spread of the data
- __But the whole point of calculating variance was to get one number that describes the dataset__
- We don’t want to report five values — we want to combine those into one __descriptive statistic__
- To do this, we’ll take the average of those five numbers
- we’ll end up with a single number that describes the average distance between our data points and the mean

### Square The Differences
- We’re almost there! We have one small problem with our equation
- Consider this very small dataset: `[-5, 5]`
- The mean of this dataset is `0`
- so when we find the difference between each point and the mean we get `-5 - 0 = -5` and `5 - 0 = 5`
- When we take the average of `-5` and `5` to get the variance, we get `0`!
- Now think about what would happen if the dataset were `[-200, 200]`
- We’d get the same result! That can’t possibly be right 
- the dataset with `200` is much more spread out than the dataset with `5`
- so the variance should be much larger!
- The problem here is with negative numbers
- Because one of our data points was `5` units below the mean and the other was `5` units above the mean, they canceled each other out!
- When calculating variance, we don’t care if a data point was above or below the mean 
- all we care about is __how far__ away it was
- To get rid of those pesky negative numbers, we’ll __square the difference__ between each data point and the mean
- Our equation for finding the difference between a data point and the mean now looks like this:
```
difference=(X−μ)**2
```
### Variance In NumPy
- Well done! You’ve calculated the variance of a data set
- The full equation for the variance is as follows:

σ2=∑i=1N(Xi−μ)2N\sigma^2 = \frac{\sum_{i=1}^{N}{(X_i -\mu)^2}}{N}σ2=N

- Let’s dissect this equation a bit.
    - Variance is usually represented by the symbol sigma squared
    - We start by taking every point in the dataset 
    - from point number `1` to point number `N` 
    - and finding the difference between that point and the mean
    - Next, we square each difference to make all differences positive
    - Finally, we average those squared differences by adding them together and dividing by __N__, the total number of points in the dataset
- All of this work can be done quickly using Python’s __NumPy__ library
- The `var()` function takes a list of numbers as a parameter and returns the variance of that dataset

import numpy as np
 
dataset = [3, 5, -2, 49, 10]
variance = np.var(dataset)

### Variance Summary : all about how spread
- You might be wondering why we need to compute the variance
- After all, by comparing histograms, it was fairly easy to tell which dataset had a larger spread
- Variance is useful because it is a measure of spread
- While we might get a general understanding of the spread by looking at a histogram
- computing the variance gives us a numerical value that helps us describe the level of confidence of our comparison
- It is also interesting to consider datasets that don’t have the same general curve

## Standard Deviation
- Variance is a tricky __statistic__ to use because its units are different from both the mean and the data itself
- For example, the mean of our NBA dataset is 77.98 inches
- Because of this, we can say someone who is 80 inches tall is about two inches taller than the average NBA player
- However, because the formula for variance includes squaring the difference between the data and the mean, the variance is measured in units squared
- This means that the variance for our NBA dataset is 13.32 inches squared

- This result is hard to interpret in context with the mean or the data because their units are different
- This is where the statistic standard deviation is useful

- Standard deviation is computed by taking the square root of the variance
- sigma is the symbol commonly used for standard deviation
- Conveniently, sigma squared is the symbol commonly used for variance:

- In Python, you can take the square root of a number using ** 0.5:
```python
num = 25
num_square_root = num ** 0.5
```
### Standard Deviation in NumPy
- There is a NumPy function dedicated to finding the standard deviation of a dataset 
- we can cut out the step of first finding the variance
- The NumPy function std() takes a dataset as a parameter and returns the standard deviation of that dataset:
```python
import numpy as np
dataset = [4, 8, 15, 16, 23, 42]
standard_deviation = np.std()
```

### Using Standard Deviation
- Now that we’re able to compute the standard deviation of a dataset, what can we do with it?
- Now that our units match, our measure of spread is easier to interpret
- By finding the number of standard deviations a data point is away from the mean, we can begin to investigate how unusual that datapoint truly is
- In fact, you can usually expect around 68% of your data to fall within one __standard deviation__ of the mean
- 95% of your data to fall within two standard deviations of the mean, and 99
- 7% of your data to fall within three standard deviations of the mean
- ![A histogram showing where the standard deviations fall]()
- If you have a data point that is over three __standard deviations__ away from the mean, that's an incredibly unusual piece of data! 

### Review
- In the last exercise you saw that Lebron James was 0.55 standard deviations above the mean of NBA player heights
- He’s taller than average, but compared to the other NBA players, he’s not absurdly tall
- However, compared to the OkCupid dating pool
- he is extremely rare! He’s almost three full standard deviations above the mean
- You’d expect only about 0.15% of people on OkCupid to be more than 3 standard deviations away from the mean
- This is the power of standard deviation
- By taking the __square root__ of the variance
- the standard deviation gives you a statistic about spread that can be easily interpreted and compared to the mean

## Histogram 
- Summarizing Your Data
    - The purpose of a histogram is to summarize data that you can use to inform a decision or __explain a distribution__
    - While a histogram is one of the most useful tools for communicating trends
    - people often use the average of a dataset to make broad claims about its underlying trends
    - While the average value of data may be useful to interpret where the data is centered, it can also be misleading
- Average grocery store time
    - Throughout this lesson, you will analyze grocery store data to understand how a histogram may be a better tool for communicating trends in your data
    - You will use this data to determine the best times for a manager to staff their store
- Let’s start by looking at our data and calculating the average time that a person will enter the grocery store

### Range
- Histograms are helpful for understanding how your data is distributed
- While the average time a customer may arrive at the grocery store is 3 pm, the manager knows 3 pm is not the busiest time of day
- Before identifying the busiest times of the day, it’s important to understand the extremes of your data: the minimum and maximum values in your dataset
- With the minimums and maximums, you can calculate the range
- The range of your data is the difference between the maximum value and the minimum value in your dataset
```
range=max(data) − min(data)
```
- Exercise Class Example
    - In the example below, we have a NumPy array with the ages of people in an exercise class
    - Before looking at the data, let’s think about what minimum, maximum, and range values are reasonable for a group of people in an exercise class:
        - The minimum cannot be below 0, because people don’t have negative ages
        - The maximum is probably lower than 122 (the oldest person ever)

- Now, let’s take a look at our data.
```python
exercise_ages = np.array([22, 27, 45, 62, 34, 52, 42, 22, 34, 26])
```
- The minimum age in `exercise_ages` is 22, the maximum age is 62, and the range is 40.
- You can use the following Python commands to verify this result:
```python
min_age = np.amin(exercise_ages) # Answer is 22
max_age = np.amax(exercise_ages) # Answer is 62
age_range = max_age - min_age
```

### Bins and Count I
- In the previous exercise, you found that the earliest transaction time is close to 0, and the latest transaction is close to 24, making your range nearly 24 hours
- Now, we have the information we need to start building our histogram
- The two key features of a histogram are bins and counts
#### Bins
- A bin is a __sub-range__ of values that falls within the range of a dataset
- In the grocery store example, a valid bin may be from 0 hours to 6 hours
- This bin includes all times from just after midnight (0) until 6 am (6)
- Additionally, all bins in a histogram must be the same width
- If the range of values in our dataset is from 0 to 24
- and the first bin in our grocery store example is from 0 to 6
- can you figure out the minimums and maximums of the other bins?
- The grocery store bins are:
    - 0 to 6 hours
    - 6 to 12 hours
    - 12 to 18 hours
    - 18 to 24 hours

#### Count
- A __count__ is the number of values that fall within a bin’s range
- For example, if 100 customers arrive at your grocery store between midnight (0) and 6 am (6)
- your count for that bin is equal to 100
- Exercise Class Example
- In the example below, we have an array with ten values in it, each representing the age of a person in an exercise class
- We want to calculate the number of students who are in their 20s, 30s, 40s, 50s, and 60s
```python
exercise_ages = np.array([20, 27, 45, 69, 34, 52, 42, 22, 34, 26])
```
- __Question__ : What is our range?
    - __Answer__ : Between 20 and 69.
- __Question__ : How many bins do we need?
    - __Answer__ : The bins are 20s, 30s, 40s, 50s, and 60s, so we need five bins, each covering ten years.
- The table below shows the number of people in each binned age group:

| 20-29 | 30-39 | 40-49 | 50-59 | 60-69 |
|-------|-------|-------|-------|-------|
| 4     | 2     | 2     | 1     | 1     |

### Numpy Histograms
- While __counting__ the number of values in a __bin__ is straightforward, it is also time-consuming
- How long do you think it would take you to count the number of values in each bin for:
    - an exercise class of 50 people?
    - a grocery store with 300 loaves of bread?
- Most of the data you will analyze with __histograms__ includes far more than ten values
- For these situations, we can use the `numpy.histogram()` function
- In the example below, we use this function to find the counts for a twenty-person exercise class
```python
exercise_ages = np.array([22, 27, 45, 62, 34, 52, 42, 22, 34, 26, 24, 65, 34, 25, 45, 23, 45, 33, 52, 55])
np.histogram(exercise_ages, range = (20, 70), bins = 5)
```

- Below, we explain each of the function’s inputs:
    - `exercise_ages` is the input array
    - `range = (20, 70)` — is the range of values we expect in our array. Range includes everything from 20, up until but not including 70.
    - `bins = 5` is the number of bins. Python will automatically calculate equally-sized bins based on the range and number of bins.
- Below, you can see the output of the `numpy.histogram()` function:
```bash
(array([7, 4, 4, 3, 2]), array([20., 30., 40., 50., 60., 70.]))
```
- The first array, `array([7, 4, 4, 3, 2])`, is the counts for each bin
- The second array, `array([20., 30., 40., 50., 60., 70.])`, includes the minimum and maximum values for each bin:
    - Bin 1: 20 to <30
    - Bin 2: 30 to <40
    - Bin 3: 40 to <50
    - Bin 4: 50 to <60
    - Bin 5: 60 to <70

### Plotting a Histogram
- At this point, you’ve learned how to find the numerical inputs to a histogram
- Thus far the __size__ of our datasets and __bins__ have produced results that we can interpret
- This becomes increasingly difficult as the number of bins in a histogram increases
- Because of this, __histograms__ are typically __viewed graphically__ :
    - with __bin__ ranges on the __x-axis__
    - and __counts__ on the __y-axis__
- The figure below shows the graphical representation of the histogram for our exercise class example from last exercise
- Notice, there are five equally-spaced bars, with each displaying a count for an age range
- Compare the graph to the table, just below it

```
!Histogram
---vs---
| 20-29 | 30-39 | 40-49 | 50-59 | 60-69 |
|-------|-------|-------|-------|-------|
| 7     | 4     | 4     | 3     | 2     |
```
- Histograms are an easy way to visualize trends in your data
- When I look at the above graph, I think
- “More people in the exercise class are in their twenties than any other decade
    - Additionally, the histogram is skewed, indicating the class is made of more younger people than older people”
- We created the plot above using the `matplotlib.pyplot` package
- We imported the package using the following code:
```python
from matplotlib import pyplot as plt
```
- We plotted the histogram with the following code
- Notice, the `range` and `bins` arguments are the same as we used in the last exercise:
```python
plt.hist(exercise_ages, range = (20, 70), bins = 5, edgecolor='black')
 
plt.title("Decade Frequency")
plt.xlabel("Ages")
plt.ylabel("Count")
 
plt.show()
```
- In the code above, we used the `plt.hist()` function to create the plot
- then added a title, x-label, and y-label before showing the graph with `plt.show()`

### Finding your Best Bin Size
- The figure below displays the graph that you created in the last exercise:
```
!Histogram
```
- This histogram is helpful for our store manager
- The last six hours of the day are the busiest — from 6 pm until midnight
- Does this mean the manager should staff their grocery store with the most employees between 6 pm and midnight?
- To the manager, this doesn’t make much sense
- The manager knows the store is busy when many people get off work, but the rush certainly doesn’t continue later than 9 pm
- The __issue__ with this histogram is that we have __too few bins__(only 4)
- When plotting a histogram, it’s essential to select bins that fully capture the trends in the underlying data
- Often, this will require some guessing and checking
- There isn’t much of a science to selecting bin size
- How many bins do you think makes sense for this example? I would try 24 because there are 24 hours in a day

## Describe a Histogram
- While many people know the functions to plot a histogram
- few spend the time to learn how to fully and concisely __communicate what it means__
- In this lesson, you will learn how to interpret a distribution using the following five features of a dataset:
    - Center
    - Spread
    - Skew
    - Modality
    - Outliers
- Throughout this lesson, we will use data from the [United States Health and Human Services Department](https://data.cms.gov/Medicare-Inpatient/Inpatient-Prospective-Payment-System-IPPS-Provider/97k6-zzx3)
- to compare the cost of the same medical procedure at over 2,000 hospitals across the country

```python
import pandas as pd 
from matplotlib import pyplot as plt
import codecademylib3_seaborn

cp_data = pd.read_csv("cp.csv") 

plt.hist(cp_data[' Average Covered Charges '], bins=20, edgecolor='black')

plt.title("Distribution of Chest Pain Treatment Cost by Hospital", fontsize = 16)
plt.xlabel("Cost ($)", fontsize = 16)
plt.ylabel("Count", fontsize = 16)

plt.show()
```

### Center
- One of the most common ways to summarize a dataset is to communicate its center
- In this lesson, we will use average and median as our measures of centrality
- The figure below shows the average and median ages of a dataset of 100 authors
- As expected, the average and median values are near the center of the distribution
```image
!title
```
- While it’s good practice to communicate both the average and median values, the average is generally more common

### Spread
- Once you’ve found the center of your data, you can shift to identifying the extremes of your dataset: the minimum and maximum values
- These values, taken with the mean and median, begin to indicate the shape of the underlying dataset
- Take the histogram below as an example:
```image
title
```
- The minimum value of this data is 18, and the maximum value is 76
- You can calculate the range using the following: `range=max−min`
- The range of this dataset is `range=76−18=58`

### Skew : symmetric, right-skewed, left-skewed
- Once you have the __center__ and __range__ of your data, you can begin to describe its shape
- The skew of a dataset is a description of the data’s symmetry
- A dataset with one prominent peak, and similar tails to the left and right is called __symmetric__
    - The median and mean of a symmetric dataset are similar
- A histogram with a tail that extends to the right is called a __right-skewed__ dataset
    - The median of this dataset is less than the mean
- A histogram with one prominent peak to the right, and a tail that extends to the left is called a __left-skewed__ dataset
    - The median of this dataset is greater than the mean

### Modality : unimodal, bimodal, multimodal, uniform distribution
- The modality describes the __number of peaks__ in a dataset
- Thus far, we have only looked at datasets with one distinct peak, known as __unimodal__
- This is the most common

- A __bimodal__ dataset has two distinct peaks

- A __multimodal__ dataset has more than two peaks
    - The histogram below displays three peaks.

- You may also see datasets with no obvious clustering
    - Datasets such as these are called __uniform distributions__

### Outliers
- An outlier is a data point that is __far__ away __from the rest__ of the dataset
- Ouliers do not have a formal definition, but are easy to determine by looking at histogram
- The histogram below shows an example of an oulier
- There is one datapoint that is much larger than the rest

- If you see an outlier in your dataset, it’s worth reporting and investigating
- This data can often __indicate an error__ in your data or an __interesting insight__

## Quartiles, Quantiles, Interquartiles Range, Boxplot
... comeback later
