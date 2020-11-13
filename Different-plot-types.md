# Different plot types 
<!-- vim-markdown-toc GFM -->

* [Simple Bar Chart](#simple-bar-chart)
* [Simple Bar Chart II](#simple-bar-chart-ii)
* [Side-By-Side Bars](#side-by-side-bars)
* [Stacked Bars](#stacked-bars)
* [Error Bars](#error-bars)
* [Fill Between](#fill-between)
* [Pie Chart](#pie-chart)
    * [Pie Chart Labeling](#pie-chart-labeling)
* [Histogram](#histogram)
* [Multiple Histograms](#multiple-histograms)

<!-- vim-markdown-toc -->
summary
- In helping MatplotSip visualize their data, you’ve learned a bunch of new plot types that you can use in Matplotlib. Congratulations on adding these new plotting abilities to your repertoire:
    - How to compare categories of data with bar graphs
    - Add error bars to graphs
    - Use fill_between to display shaded error on line graphs
    - Create stacked bar graphs for easier comparisons
    - Create side-by-side bar graphs
    - Create and format pie charts to compare proportional datasets
    - Analyze frequency data using histograms, including multiple histograms on the same plot
    - Normalize histograms
## Simple Bar Chart
- The plt.bar function allows you to create simple bar charts to compare multiple categories of data
- Some possible data that would be displayed with a bar chart:
    - x-axis — famous buildings, y-axis — heights
    - x-axis — different planets, y-axis — number of days in the year
    - x-axis — programming languages, y-axis — lines of code written by you
- You call plt.bar with two arguments:
    - the x-values — a list of x-positions for each bar
    - the y-values — a list of heights for each bar
- In most cases, we will want our x-values to be a list that looks like [0, 1, 2, 3 ...]
    - and has the same number of elements as our y-values list
    - We can create that list manually, but we can also use the following code:
```python
heights = [88, 225, 365, 687, 4333, 10756, 30687, 60190, 90553]
x_values = range(len(heights))
```
- The `range` function creates a list of consecutive integers (i.e., `[0, 1, 2, 3, ...]`)
- It needs an argument to tell it how many numbers should be in the list
    - For instance, `range(5)` would make a list with 5 numbers
        - We want our list to be as long as our bar heights (`heights` in this example)
        - `len(heights)` tell us how many elements are in the list `heights`


- Here is an example of how to make a bar chart using `plt.bar` to compare the number of days in a year on the different planets:
```python
days_in_year = [88, 225, 365, 687, 4333, 10756, 30687, 60190, 90553]
plt.bar(range(len(days_in_year)),
        days_in_year)
plt.show()
```

- At this point, it’s hard to tell what this represents, because it’s unclearly labeled
- We’ll fix that in later sections!

- In the instructions below, we’ll use `plt.bar` to create a chart for a fake cafe called MatplotSip
- We will be comparing the sales of different beverages on a given day

## Simple Bar Chart II
- When we create a bar chart, we want each bar to be meaningful and correspond to a category of data
- In the drinks chart from the last exercise
    - we could see that sales were different for different drink items
    - but this wasn’t very helpful to us
    - since we didn’t know which bar corresponded to which drink

- In the previous lesson, we learned how to customize the tick marks on the x-axis in three steps:
    1. Create an axes object
```python
ax = plt.subplot()
```
    2. Set the x-tick positions using a list of numbers
```python
ax.set_xticks([0, 1, 2, 3, 4, 5, 6, 7, 8])
```
    3. Set the x-tick labels using a list of strings
```python
ax.set_xticklabels(['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune', 'Pluto'])
```
    4. If your labels are particularly long, you can use the rotation keyword to rotate your labels by a specified number of degrees:
```python
ax.set_xticklabels(['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune', 'Pluto'],
    rotation=30)
```
- Note:
    - We have to set the x-ticks before we set the x-labels
        - because the default ticks won’t necessarily be one tick per bar
            - especially if we’re plotting a lot of bars
        - If we skip setting the x-ticks before the x-labels, we might end up with labels in the wrong place

- Remember from Lesson I that we can label the x-axis (`plt.xlabel`) and y-axis (`plt.ylabel`) as well
- Now, our graph is much easier to understand:
- Let’s add the appropriate labels for the chart you made in the last exercise for the coffee shop, MatplotSip.

## Side-By-Side Bars
- We can use a bar chart to compare two sets of data with the same types of axis values
- To do this, we plot two sets of bars next to each other, so that the values of each category can be compared
- For example, here is a chart with side-by-side bars for the populations of the United States and China over the age of 65 (in percentages):
```image
!population_bars
```
(data taken from [World Bank](https://data.worldbank.org/indicator/SP.POP.65UP.TO.ZS?end=2016&locations=US-CN&start=1960&view=chart))
- Some examples of data that side-by-side bars could be useful for include:
    - the populations of two countries over time
    - prices for different foods at two different restaurants
    - enrollments in different classes for males and females

- In the graph above, there are 7 sets of bars, with 2 bars in each set
- Each bar has a width of 0.8 (the default width for all bars in Matplotlib)
    - If our first blue bar is at x=0, then we want the next blue bar to be at x=2, and the next to be at x=4, etc.
    - Our first orange bar should be at x=0.8 (so that it is touching the blue bar), and the next orange bar should be at x=2.8, etc.

- This is a lot of math, but we can make Python do it for us by copying and pasting this code:
```python
# China Data (blue bars)
n = 1  # This is our first dataset (out of 2)
t = 2 # Number of datasets
d = 7 # Number of sets of bars
w = 0.8 # Width of each bar
x_values1 = [t*element + w*n for element
             in range(d)]
```
- That just generated the first set of x-values
- To generate the second set, paste the code again, but change `n` to 2, because this is the second dataset:
```python
# US Data (orange bars)
n = 2  # This is our second dataset (out of 2)
t = 2 # Number of datasets
d = 7 # Number of sets of bars
w = 0.8 # Width of each bar
x_values2 = [t*element + w*n for element
             in range(d)]
```
- Let’s examine our special code:
```python
[t*element + w*n for element in range(d)]
```
- This is called a [list comprehension](https://docs.python.org/2/tutorial/datastructures.html#list-comprehensions)
    - It’s a special way of generating a list from a formula
    - For making side-by-side bar graphs, you’ll never need to change this line
    - just paste it into your code and make sure to define n, t, d, and w correctly

- In the instructions below, we’ll experiment with side-by-side bars to compare different locations of the MatplotSip coffee empire.
```python
from matplotlib import pyplot as plt

drinks = ["cappuccino", "latte", "chai", "americano", "mocha", "espresso"]
sales1 = [91, 76, 56, 66, 52, 27]
sales2 = [65, 82, 36, 68, 38, 40]

#Paste the x_values code here
n = 1  # This is our first dataset (out of 2)
t = 2 # Number of dataset
d = 6 # Number of sets of bars
w = 0.8 # Width of each bar
store1_x = [t*element + w*n for element
             in range(d)]

plt.bar(store1_x, sales1)
#Paste the x_values code here
n = 2  # This is our second dataset (out of 2)
t = 2 # Number of dataset
d = 6 # Number of sets of bars
w = 0.8 # Width of each bar
store2_x = [t*element + w*n for element
             in range(d)]

plt.bar(store2_x, sales2)

plt.show()
```

## Stacked Bars
- If we want to compare two sets of data while preserving knowledge of the total between them
    - we can also stack the bars instead of putting them side by side
- For instance
    - if someone was plotting the hours they’ve spent on entertaining themselves with video games and books in the past week
    - and wanted to also get a feel for total hours spent on entertainment, they could create a stacked bar chart:
```image
!entertainment
```
- We do this by using the keyword bottom
- The top set of bars will have bottom set to the heights of the other set of bars
- So the first set of bars is plotted normally:
```python
video_game_hours = [1, 2, 2, 1, 2]

plt.bar(range(len(video_game_hours)),
  video_game_hours) 
```
- and the second set of bars has bottom specified:
```python
book_hours = [2, 3, 4, 2, 1]
 
plt.bar(range(len(book_hours)),
  book_hours,
  bottom=video_game_hours)
```
- This starts the `book_hours` bars at the heights of the `video_game_hours` bars
- So, for example
    - on Monday the orange bar representing hours spent reading will start at a value of `1` instead of `0`
        - because 1 hour was spent playing video games.
- Let’s try this out with the MatplotSip data from the last exercise.
```python
from matplotlib import pyplot as plt

drinks = ["cappuccino", "latte", "chai", "americano", "mocha", "espresso"]
sales1 =  [91, 76, 56, 66, 52, 27]
sales2 = [65, 82, 36, 68, 38, 40]
  
plt.bar(range(len(drinks)), sales1)
plt.bar(range(len(drinks)), sales2, bottom=sales1)

plt.legend(["Location 1", "Location 2"])

plt.show()
```

## Error Bars
- In the previous exercise, you learned to represent data as bars of different heights
- Sometimes, we need to visually communicate some sort of uncertainty in the heights of those bars
- Here are some examples:
    - The average number of students in a 3rd grade classroom is 30, but some classes have as few as 18 and others have as many as 35 students.
    - We measured that the weight of a certain fruit was 35g, but we know that our scale isn’t very precise, so the true weight of the fruit might be as much as 40g or as little as 30g.
    - The average price of a soda is $1.00, but we also want to communicate that the standard deviation is $0.20.
- To display error visually in a bar chart, we often use error bars to show where each bar could be, taking errors into account
```image
!error_bars
```
- Each of the black lines is called an error bar
- The taller the bar is, the more uncertain we are about the height of the blue bar
- The horizontal lines at the top and bottom are called caps
- They make it easier to read the error bars

- If we wanted to show an error of +/- 2, we would add the keyword `yerr=2` to our `plt.bar` command
- To make the caps wide and easy to read, we would add the keyword `capsize=10`
```python
values = [10, 13, 11, 15, 20]
yerr = 2
plt.bar(range(len(values)), values, yerr=yerr, capsize=10)
plt.show()
```
- If we want a different amount of error for each bar, we can make yerr equal to a list rather than a single number:
```python
values = [10, 13, 11, 15, 20]
yerr = [1, 3, 0.5, 2, 4]
plt.bar(range(len(values)), values, yerr=yerr, capsize=10)
plt.show()
```
- This code results in error bars of different sizes:
```imagae
variable_error
```
- Like the list of x-axis labels, Matplotlib reads this in the same order as the list of y-values
- So, the first index of your error list should correspond to
    - the first index of your y-values list
    - the second index of your error list should correspond to the second index of your y-values list, and so on

```python
from matplotlib import pyplot as plt

drinks = ["cappuccino", "latte", "chai", "americano", "mocha", "espresso"]
ounces_of_milk = [6, 9, 4, 0, 9, 0]
error = [0.6, 0.9, 0.4, 0, 0.9, 0]

# Plot the bar graph here
plt.bar(range(len(drinks)), ounces_of_milk, yerr=error, capsize=5)

plt.show()
```

## Fill Between
- We’ve learned how to display errors on bar charts using error bars
- Let’s take a look at how we might do this in an aesthetically pleasing way on line graphs
- In Matplotlib, we can use plt.fill_between to shade error
- This function takes three arguments:
    1. `x-values` — this works just like the x-values of `plt.plot`
    2. lower-bound for y-values — sets the bottom of the shared area
    3. upper-bound for y-values — sets the top of the shared area

- Generally, we use `fill_between` to create a shaded error region, and then plot the actual line over it
- We can set the `alpha` keyword to a value between 0 and 1 in the `fill_between` call for transparency so that we can see the line underneath
- Here is an example of how we would display data with an error of 2:
```python
x_values = range(10)
y_values = [10, 12, 13, 13, 15, 19, 20, 22, 23, 29]
y_lower = [8, 10, 11, 11, 13, 17, 18, 20, 21, 27]
y_upper = [12, 14, 15, 15, 17, 21, 22, 24, 25, 31]
 
plt.fill_between(x_values, y_lower, y_upper, alpha=0.2) #this is the shaded error
plt.plot(x_values, y_values) #this is the line itself
plt.show()
```
- This would give us a plot that looks like:
```image
fill_between
```
- Having to calculate `y_lower` and `y_upper` by hand is time-consuming
- If we try to just subtract 2 from `y_values`, we will get an error
```
TypeError: unsupported operand type(s) for -: 'list' and 'int'
```
- In order to correctly add or subtract from a list, we need to use list comprehension:
```python
y_lower = [i - 2 for i in y_values]
```
- This command looks at each element in `y_values` and calls the element its currently looking at `i`
- For each new `i`, it subtracts 2
- These opperations create a new list called `y_lower`

- If we wanted to add 2 to each element in `y_values`, we use this code:
```python
y_upper = [i + 2 for i in y_values]
```
- exercise code :
```python
import codecademylib
from matplotlib import pyplot as plt

months = range(12)
month_names = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]
revenue = [16000, 14000, 17500, 19500, 21500, 21500, 22000, 23000, 20000, 19500, 18000, 16500]

plt.plot(months, revenue)

ax = plt.subplot()
ax.set_xticks(months)
ax.set_xticklabels(month_names)

y_upper = [i + (i*0.10) for i in revenue]
y_lower = [i - (i*0.10) for i in revenue]

plt.fill_between(months, y_lower, y_upper, alpha=0.2)

plt.show()
```
## Pie Chart
- If we want to display elements of a data set as proportions of a whole, we can use a pie chart

- Pie charts are helpful for displaying data like:
    - Different ethnicities that make up a school district
    - Different macronutrients (carbohydrates, fat, protein) that make up a meal
    - Different responses to an online poll

- In Matplotlib, you can make a pie chart with the command plt.pie, passing in the values you want to chart:
```python
budget_data = [500, 1000, 750, 300, 100]
 
plt.pie(budget_data)
plt.show()
```
- Which would create a chart like:
```image
!budget_skew
```
- This looks weird and tilted
- When we make pie charts in Matplotlib, we almost always want to set the axes to be equal to fix this issue
- To do this, we use `plt.axis('equal')`, which results in a chart like this:
```image
!budget_no_skew
```
```python
from matplotlib import pyplot as plt

payment_method_names = ["Card Swipe", "Cash", "Apple Pay", "Other"]
payment_method_freqs = [270, 77, 32, 11]

#make your pie chart here
plt.pie(payment_method_freqs)
plt.axis('equal')

plt.show()
```
### Pie Chart Labeling
- We also want to be able to understand what each slice of the pie represents
- To do this, we can either:
    - use a legend to label each color, or
    - put labels on the chart itself.

- Method 1
```python
budget_data = [500, 1000, 750, 300, 100]
budget_categories = ['marketing', 'payroll', 'engineering', 'design', 'misc']
 
plt.pie(budget_data)
plt.legend(budget_categories)
```
- This puts the category names into a legend on the chart:
```image
!pie_legend
```
- Method 2
```python
#option 2
plt.pie(budget_data, labels=budget_categories)
```
- This puts the category names into labels next to each corresponding slice:
```image
pie_labels
```
- One other useful labeling tool for pie charts is adding the percentage of the total that each slice occupies
- Matplotlib can add this automatically with the keyword autopct
- We pass in string formatting instructions to format the labels how we want
- Some common formats are:
    - `'%0.2f'` — 2 decimal places, like `4.08`
    - `'%0.2f%%'` — 2 decimal places, but with a percent sign at the end, like `4.08%.` You need two consecutive percent signs because the first one acts as an escape character, so that the second one gets displayed on the chart.
    - `'%d%%'` — rounded to the nearest `int` and with a percent sign at the end, like `4%`

- So, a full call to `plt.pie` might look like:
```python
plt.pie(budget_data,
        labels=budget_categories,
        autopct='%0.1f%%')
```
and the resulting chart would look like:
```python
budget_chart_full
```
```python
from matplotlib import pyplot as plt

payment_method_names = ["Card Swipe", "Cash", "Apple Pay", "Other"]
payment_method_freqs = [270, 77, 32, 11]

plt.pie(payment_method_freqs, autopct="%0.1f%%")
plt.axis('equal')
plt.legend(payment_method_names)

plt.show()
```

## Histogram
- Sometimes we want to get a feel for a large dataset with many samples beyond knowing just the basic metrics of mean, median, or standard deviation
- To get more of an intuitive sense for a dataset, we can use a histogram to display all the values

- A histogram tells us how many values in a dataset fall between different sets of numbers
    - (i.e., how many numbers fall between 0 and 10? Between 10 and 20? Between 20 and 30?)
- Each of these questions represents a bin, for instance, our first bin might be between 0 and 10

- All bins in a histogram are always the same size
- The width of each bin is the distance between the minimum and maximum values of each bin
- In our example, the width of each bin would be 10

- Each bin is represented by a different rectangle whose height is the number of elements from the dataset that fall within that bin

- Here is an example:
```image
histogram
```
- To make a histogram in Matplotlib, we use the command `plt.hist`
    - `plt.hist` finds the minimum and the maximum values in your dataset and creates 10 equally-spaced bins between those values

- The histogram above, for example, was created with the following code:
```python
plt.hist(dataset) 
plt.show()
```
- If we want more than 10 bins
    - we can use the keyword bins to set how many bins we want to divide the data into
    - The keyword range selects the minimum and maximum values to plot
    - For example
        - if we wanted to take our data from the last example
        - and make a new histogram that just displayed the values from 66 to 69
        - divided into 40 bins (instead of 10), we could use this function call:
```python
plt.hist(dataset, range=(66,69), bins=40)
```
- which would result in a histogram that looks like this:
```image
histogram_range
```
- Histograms are best for showing the shape of a dataset
- For example, you might see that values are close together, or skewed to one side
- With this added intuition, we often discover other types of analysis we want to perform

## Multiple Histograms
- If we want to compare two different distributions, we can put multiple histograms on the same plot
- This could be useful, for example, in comparing the heights of a bunch of men and the heights of a bunch of women
- However, it can be hard to read two histograms on top of each other
- For example, in this histogram, we can’t see all of the blue plot, because it’s covered by the orange one:
```image
overlap_hist
```
- We have two ways we can solve a problem like this:
    1. use the keyword alpha, which can be a value between 0 and 1
        - This sets the transparency of the histogram
        - A value of 0 would make the bars entirely transparent
        - A value of 1 would make the bars completely opaque
```python
plt.hist(a, range=(55, 75), bins=20, alpha=0.5)
plt.hist(b, range=(55, 75), bins=20, alpha=0.5)
```
        - This would make both histograms visible on the plot: alpha_histograms

    2. use the keyword histtype with the argument 'step' to draw just the outline of a histogram:
```python
plt.hist(a, range=(55, 75), bins=20, histtype='step')
plt.hist(b, range=(55, 75), bins=20, histtype='step')
```
        - which results in a chart like: !step_histogram

- Another problem we face is that our histograms might have different numbers of samples, making one much bigger than the other
- We can see how this makes it difficult to compare qualitatively, by adding a dataset b with a much bigger size value:
```python
a = normal(loc=64, scale=2, size=10000)
b = normal(loc=70, scale=2, size=100000)
 
plt.hist(a, range=(55, 75), bins=20)
plt.hist(b, range=(55, 75), bins=20)
plt.show()
```
- The result is two histograms that are very difficult to compare: !different_hist

- To solve this, we can normalize our histograms using `normed=True`
- This command divides the height of each column by a constant such that the total shaded area of the histogram sums to 1
```python
a = normal(loc=64, scale=2, size=10000)
b = normal(loc=70, scale=2, size=100000)
 
plt.hist(a, range=(55, 75), bins=20, alpha=0.5, normed=True)
plt.hist(b, range=(55, 75), bins=20, alpha=0.5, normed=True)
plt.show()
```
- Now, we can more easily see the differences between the blue set and the orange set: !normalized_hist
