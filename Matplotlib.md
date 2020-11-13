# Matplotlib
- Matplotlib provides full control over the plot to make plot customisation easy, but what it lacks is built in support for pandas
    - Seaborn is a data visualisation library built on top of matplotlib and __closely integrated__ with pandas
- plot : To mark (a point on a graph, chart, etc).
- https://matplotlib.org/tutorials/index.html
- The pyplot module mirrors the MATLAB plotting commands closely
- Matplotlib is a Python library used to create charts and graphs
- The concepts you will learn include:
    - Creating a line graph from data
    - Changing the appearance of the line
    - Zooming in on different parts of the axis
    - Putting labels on titles and axes
    - Creating a more complex figure layout
    - Adding legends to graphs
    - Changing tick labels and positions
    - Saving what you’ve made
- matplotlib vs seaborn
    - Matplotlib: Pandas uses Matplotlib. It is a neat wrapper around Matplotlib.
    - Seaborn: Seaborn is for more specific use cases. Also, it is Matplotlib under the hood. It is specially meant for statistical plotting.
- Moving on, we’ll learn how to make different kinds of plots (beyond line graphs!) in Matplotlib and how to choose between those plots when displaying data
```python
from matplotlib import pyplot as plt
```

## Basic Line Plot
- Line graphs are helpful for visualizing how a variable changes over time
- Some possible data that would be displayed with a line graph:
    - average prices of gasoline over the past decade
    - weight of an individual over the past couple of months
    - average temperature along a line of longitude over different latitudes
- Using Matplotlib methods, the following code will create a simple line graph using .plot() and display it using .show() :
```python
x_values = [0, 1, 2, 3, 4]
y_values = [0, 1, 4, 9, 16]
plt.plot(x_values, y_values)
plt.show()
```
    - `x_values` is a variable holding a list of x-values for each point on our line graph
    - `y_values` is a variable holding a list of y-values for each point on our line graph
    - `plt` is the name we have given to the Matplotlib module we have imported at the top of the code
    - `plt.plot(x_values, y_values)` will create the line graph
    - `plt.show()` will actually display the graph

## Basic Line Plot II
- We can also have multiple line plots displayed on the same set of axes
- This can be very useful if we want to compare two datasets with the same scale and axis categories
- Matplotlib will automatically place the two lines on the same axes and give them different colors if you call plt.plot() twice
- Let’ s look at the graph we made in the last exercise to track lunch spending
    - where days is on the `x-axis` and spending (`money_spent`) is on the y-axis:
```image
!image
```
- We could add a friend’s lunch spending for comparison like this:
```python
# Days of the week:
days = [0, 1, 2, 3, 4, 5, 6]
# Your Money:
money_spent = [10, 12, 12, 10, 14, 22, 24]
# Your Friend's Money:
money_spent_2 = [11, 14, 15, 15, 22, 21, 12]
# Plot your money:
plt.plot(days, money_spent)
# Plot your friend's money:
plt.plot(days, money_spent_2)
# Display the result:
plt.show()
```
- Plot `values1` vs `values2` means that you should plot `[values2 on the x-axis]` and `[values1 on the y-axis]`
    - for example :
        - we have defined lists called time, revenue, and costs
        - plot revenue vs time
            - mean : time on x-axis, revenue on y axis
- We then get two lines on the same plot:
```image
money_spent_2
```
- By default, the first line is always blue, and the second line is always orange
- In the next exercise, we’ll learn how to customize these lines ourselves

## Linestyles
- We can specify a different color for a line by using the keyword color with either an HTML color name or a HEX code:
```python
plt.plot(days, money_spent, color='green')
plt.plot(days, money_spent_2, color='#AAAAAA')
```

- We can also make a line dotted or dashed using the keyword linestyle
```python
# Dashed:
plt.plot(x_values, y_values, linestyle='--')
# Dotted:
plt.plot(x_values, y_values, linestyle=':')
# No line:
plt.plot(x_values, y_values, linestyle='')
```
- We can also add a marker using the keyword marker:
```python
# A circle:
plt.plot(x_values, y_values, marker='o')
# A square:
plt.plot(x_values, y_values, marker='s')
# A star:
plt.plot(x_values, y_values, marker='*')
```
- To see all of the possible options, check out the [Matplotlib documentation](https://matplotlib.org/api/lines_api.html)
- Here are a couple of those values applied to our plots about lunch spending:
```python
plt.plot(days, money_spent, color='green', linestyle='--')
plt.plot(days, money_spent_2, color='#AAAAAA',  marker='o')
```

## Axis and Labels
- Sometimes, it can be helpful to __zoom__ in or out of the plot
    - especially if there is some detail we want to address
- To zoom, we can use `plt.axis()`
- We use `plt.axis()` by feeding it a list as input
    - This list should contain:
        - The minimum x-value displayed
        - The maximum x-value displayed
        - The minimum y-value displayed
        - The maximum y-value displayed

- For example
    - if we want to display a plot
    - from [`x=0` to `x=3`] and from [`y=2` to `y=5`]
    - we would call `plt.axis([0, 3, 2, 5])`
```python
x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]
plt.plot(x, y)
plt.axis([0, 3, 2, 5])
plt.show()
```

## Labeling the Axes
- Eventually, we will want to show these plots to other people to convince them of important trends in our data
- When we do that, we’ll want to make our plots look as professional as possible

-  The first step towards a professional-looking plot is adding labels to the x-axis and y-axis, and giving the plot a title

- We can label the x- and y- axes by using `plt.xlabel()` and `plt.ylabel()`
- The plot title can be set by using `plt.title()`

- All of these commands require a string, which is a set of characters in either single (`'`) or double (`"`) quotes
```
"This is a string"
'This is also a string'
 
'This is NOT a string (the quotes do not match)"
```
- For example
    - if someone has been keeping track of their happiness (on a scale out of 10)
    - throughout the day and wants to display this information with labeled axes
    - we can use the following commands:
```python
hours = [9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
happiness = [9.8, 9.9, 9.2, 8.6, 8.3, 9.0, 8.7, 9.1, 7.0, 6.4, 6.9, 7.5]
plt.plot(hours, happiness)
plt.xlabel('Time of day')
plt.ylabel('Happiness Rating (out of 10)')
plt.title('My Self-Reported Happiness While Awake')
plt.show()
```

## Subplots
- Which line of code will get the axes object of a plot and store it in a variable ax?
```python
ax = plt.subplot()
```
- Sometimes, we want to display two lines side-by-side, rather than in the same set of x- and y-axes
- When we have multiple axes in the same picture, we call __each set__ of __axes__ a __subplot__
- The picture or object that contains all of the subplots is called a __figure__

- We can have many different __subplots__ in the same __figure__, and we can lay them out in many different ways
- We can think of our `figure` as having rows and columns which contains subplots
- For instance, the following figure has six subplots split into 2 rows and 3 columns:

- We can create subplots using `.subplot()`

- The command `plt.subplot()` needs three arguments to be passed into it:
    - The number of rows of figure
    - The number of columns of figure
    - The index of the subplot we want to create

- For instance, the command `plt.subplot(2, 3, 4)` would create “Subplot 4” from the figure above
- Any `plt.plot()` that comes after `plt.subplot()` will create a line plot in the specified subplot
- For instance:
```python
# Data sets
x = [1, 2, 3, 4]
y = [1, 2, 3, 4]
 
# First Subplot
plt.subplot(1, 2, 1)
plt.plot(x, y, color='green')
plt.title('First Subplot')
 
# Second Subplot
plt.subplot(1, 2, 2)
plt.plot(x, y, color='steelblue')
plt.title('Second Subplot')
 
# Display both subplots
plt.show()
```

## Subplots Part II
- Sometimes, when we’re putting multiple subplots together
    - some elements can __overlap__ and make the figure unreadable:
```image
overlapping
```
- We can customize the spacing between our subplots to make sure that the figure we create is visible and easy to understand
- To do this, we use the `plt.subplots_adjust()` command
    - `.subplots_adjust()` has some keyword arguments that can move your plots within the figure:
        - `left` — the left-side margin, with a default of 0.125
            - You can increase this number to make room for a y-axis label
        - `right` — the right-side margin, with a default of 0.9
            - You can increase this to make more room for the figure, or decrease it to make room for a legend
        - `bottom` — the bottom margin, with a default of 0.1
            - You can increase this to make room for tick mark labels or an x-axis label
        - `top` — the top margin, with a default of 0.9
        - `wspace` — the horizontal space between adjacent subplots, with a default of 0.2
        - `hspace` — the vertical space between adjacent subplots, with a default of 0.2

- For example
    - if we were adding space to the bottom of a graph
    - by changing the bottom margin to 0.2 (default 0.1)
    - we would use the command:
```python
plt.subplots_adjust(bottom=0.2)
```
- We can also use multiple keyword arguments, if we need to adjust multiple margins
- For instance, we could adjust both the top and the hspace:
```python
plt.subplots_adjust(top=0.95, hspace=0.25)
```
Let’s use wspace to fix the figure above:
```python
# Left Plot
plt.subplot(1, 2, 1)
plt.plot([-2, -1, 0, 1, 2], [4, 1, 0, 1, 4])
 
# Right Plot
plt.subplot(1, 2, 2)
plt.plot([-2, -1, 0, 1, 2], [4, 1, 0, 1, 4])
 
# Subplot Adjust
plt.subplots_adjust(wspace=0.35)
 
plt.show()
```
- sample code:
```python
x = range(7)
straight_line = [0, 1, 2, 3, 4, 5, 6]
parabola = [0, 1, 4, 9, 16, 25, 36]
cubic = [0, 1, 8, 27, 64, 125, 216]

# Subplot 1
plt.subplot(2, 1, 1)
plt.plot(x, straight_line)

# Subplot 2
plt.subplot(2, 2, 3)
plt.plot(x, parabola)

# Subplot 3
plt.subplot(2, 2, 4)
plt.plot(x, cubic)

plt.subplots_adjust(wspace=0.35, bottom=0.2)

plt.show()
```

## Legends
- When we have multiple lines on a single graph we can label them by using the command `plt.legend()`
- The legend method takes a list with the labels to display
- So, for example, we can call:
```python
plt.plot([0, 1, 2, 3, 4], [0, 1, 4, 9, 16])
plt.plot([0, 1, 2, 3, 4], [0, 1, 8, 27, 64])
plt.legend(['parabola', 'cubic'])
plt.show()
```
- which would display a legend on our graph, labeling each line: legend

- `plt.legend()` can also take a keyword argument loc, which will position the legend on the figure.

- These are the position values `loc` accepts:

| Number Code | String       |
|-------------|--------------|
| 0           | best         |
| 1           | upper right  |
| 2           | upper left   |
| 3           | lower left   |
| 4           | lower right  |
| 5           | right        |
| 6           | center left  |
| 7           | center right |
| 8           | lower center |
| 9           | upper center |
| 10          | center       |

- Note: If you decide not to set a value for `loc`, it will default to choosing the “best” location.

- For, example, we can call `plt.legend()` and `set` loc to `6`:
```python
plt.legend(['parabola', 'cubic'], loc=6)
plt.show()
```
- which would move the legend to the left side of the graph: legend_loc

- Sometimes, it’s easier to label each line as we create it
- If we want, we can use the keyword label inside of `plt.plot()`
- If we choose to do this, we don’t pass any labels into `plt.legend()`
- For example:
```python
plt.plot([0, 1, 2, 3, 4], [0, 1, 4, 9, 16],
         label="parabola")
plt.plot([0, 1, 2, 3, 4], [0, 1, 8, 27, 64],
         label="cubic")
plt.legend() # Still need this command!
plt.show()
```
- This would display a legend that looks just like what we had before: 
- sample code :
```python
import codecademylib
from matplotlib import pyplot as plt

months = range(12)
hyrule = [63, 65, 68, 70, 72, 72, 73, 74, 71, 70, 68, 64]
kakariko = [52, 52, 53, 68, 73, 74, 74, 76, 71, 62, 58, 54]
gerudo = [98, 99, 99, 100, 99, 100, 98, 101, 101, 97, 98, 99]

plt.plot(months, hyrule)
plt.plot(months, kakariko)
plt.plot(months, gerudo)

#create your legend here
legend_labels = ["Hyrule", "Kakariko", "Gerudo Valley"]
plt.legend(legend_labels, loc=8)

plt.show()
```

## Modify Ticks
- In all of our previous exercises, our commands have started with `plt.`
- In order to modify __tick marks__, we’ll have to try something a little bit different
- Because our plots can have multiple subplots, we have to specify which one we want to modify
- In order to do that, we call `plt.subplot()` in a different way
```python
ax = plt.subplot(1, 1, 1)
```
- `ax` is an axes object, and it lets us modify the axes belonging to a specific subplot
    - Even if we only have one subplot
    - when we want to modify the __ticks__
    - we will need to start by calling either `ax = plt.subplot(1, 1, 1)` or `ax = plt.subplot()` in order to get our axes object

- Suppose we wanted to set our x-ticks to be at 1, 2, and 4. We would use the following code:
```python
ax = plt.subplot()
plt.plot([0, 1, 2, 3, 4], [0, 1, 4, 9, 16])
plt.plot([0, 1, 2, 3, 4], [0, 1, 8, 27, 64])
ax.set_xticks([1, 2, 4])
```
- Our result would look like this:
```image
tick_marks
```
- We can also modify the y-ticks by using `ax.set_yticks()`

- When we change the x-ticks, their labels automatically change to match
- But, if we want special labels (such as strings), we can use the command `ax.set_xticklabels()` or `ax.set_yticklabels()`
- For example, we might want to have a y-axis with ticks at 0.1, 0.6, and 0.8, but label them 10%, 60%, and 80%, respectively
- To do this, we use the following commands:
```python
ax = plt.subplot()
plt.plot([1, 3, 3.5], [0.1, 0.6, 0.8], 'o')
ax.set_yticks([0.1, 0.6, 0.8])
ax.set_yticklabels(['10%', '60%', '80%'])
```
This would result in this y-axis labeling:
```image
y_ticks
```
- Now, let’s practice with tick marks
```python
import codecademylib
from matplotlib import pyplot as plt

month_names = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep","Oct", "Nov", "Dec"]

months = range(12)
conversion = [0.05, 0.08, 0.18, 0.28, 0.4, 0.66, 0.74, 0.78, 0.8, 0.81, 0.85, 0.85]

plt.xlabel("Months")
plt.ylabel("Conversion")

plt.plot(months, conversion)

# Your work here
ax = plt.subplot()
ax.set_xticks(months)
ax.set_xticklabels(month_names)
ax.set_yticks([0.10, 0.25, 0.5, 0.75])
ax.set_yticklabels(["10%", "25%", "50%", "75%"])

plt.show()
```

## Figures
- When we’re making lots of plots, it’s easy to end up with lines that have been plotted and not displayed
- If we’re not careful, these “forgotten” lines will show up in your new plots
- In order to be sure that you don’t have any stray lines
    - you can use the command `plt.close('all')` to clear all existing plots before you plot a new one

- Previously, we learned how to put two sets of axes into the same figure
    - Sometimes, we would rather have two separate figures
    - We can use the command `plt.figure()` to create new figures and size them how we want
    - We can add the keyword `figsize=(width, height)` to set the size of the figure, in inches
    - We use parentheses (`(` and `)`) to pass in the width and height, which are separated by a comma (`,`)

- To create a figure with a width of 4 inches, and height of 10 inches, we would use:
```python
plt.figure(figsize=(4, 10))
```
- It would look tall and skinny, like this:
```image
!tall_fig
```
- Once we’ve created a figure, we might want to save it so that we can use it in a presentation or a website
- We can use the command `plt.savefig()` to save out to many different file formats, such as `png`, `svg`, or `pdf`
- After plotting, we can call `plt.savefig('name_of_graph.png')`:
```python
# Figure 2
plt.figure(figsize=(4, 10)) 
plt.plot(x, parabola)
plt.savefig('tall_and_narrow.png')
```
- This will save `tall_and_narrow.png` to our file system
- example code :
```python
word_length = [8, 11, 12, 11, 13, 12, 9, 9, 7, 9]
power_generated = [753.9, 768.8, 780.1, 763.7, 788.5, 782, 787.2, 806.4, 806.2, 798.9]
years = [2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009]

plt.close('all')
plt.figure()
plt.plot(years, word_length)
plt.savefig('winning_word_lengths.png')
plt.figure(figsize=(7, 3))
plt.plot(years, power_generated)
plt.savefig('power_generated.png')
```
```python
from matplotlib import pyplot as plt

x = range(6)
y1 = [1, 2, 3, 4, 5, 6]
y2 = [-1, 1, 3, 4, 4, 4]

plt.plot(x, y1, marker='o', color='pink')
plt.plot(x, y2, marker='o', color='gray')

plt.title("Two Lines on One Graph")
plt.xlabel("Amazing X-axis")
plt.ylabel("Incredible Y-axis")

plt.legend(["Y1","Y2"], loc=4)

plt.show()
```
