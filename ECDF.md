# ECDF
- EDA : histogram, beeswarmplot, ECDF plot
- ECDF plot overcome the limitation of beeswarm plot
- https://data.library.virginia.edu/understanding-empirical-cumulative-distribution-functions/
```python
def ecdf(data):
    """Compute ECDF for a one-dimensional array of measurements."""
    # Number of data points: n
    n = len(data)

    # x-data for the ECDF: x
    x = np.sort(data)

    # y-data for the ECDF: y
    y = np.arange(1, n+1) / n

    return x, y
```
- You will now use your `ecdf()` function to compute the ECDF for the petal lengths of Anderson's Iris versicolor flowers
    - You will then plot the ECDF
    - Recall that your `ecdf()` function returns two arrays so you will need to unpack them
    - An example of such unpacking is `x, y = foo(data)`, for some function `foo()`

```python
# Compute ECDF for versicolor data: x_vers, y_vers
x_vers, y_vers = ecdf(versicolor_petal_length)

# Generate plot
_ = plt.plot(x_vers, y_vers, marker='.', linestyle='none')

# Label the axes
_ = plt.xlabel('petal length (cm)')
_ = plt.ylabel('ECDF')

# Display the plot
plt.show()
```

## Comparison of ECDFs
- ECDFs also allow you to compare two or more distributions (though plots get cluttered if you have too many)
- Here, you will plot ECDFs for the petal lengths of all three iris species
- You already wrote a function to generate ECDFs so you can put it to good use!

- To overlay all three ECDFs on the same plot, you can use `plt.plot()` three times, once for each ECDF
- Remember to include `marker='.'` and `linestyle='none'` as arguments inside `plt.plot()`
```python
# Compute ECDFs
x_set, y_set = ecdf(setosa_petal_length)
x_vers, y_vers = ecdf(versicolor_petal_length)
x_virg, y_virg = ecdf(virginica_petal_length)

# Plot all ECDFs on the same plot
_ = plt.plot(x_set, y_set, marker='.', linestyle='none')
_ = plt.plot(x_vers, y_vers, marker='.', linestyle='none')
_ = plt.plot(x_virg, y_virg, marker='.', linestyle='none')

# Annotate the plot
_ = plt.legend(('setosa', 'versicolor', 'virginica'), loc='lower right')
_ = plt.xlabel('petal length (cm)')
_ = plt.ylabel('ECDF')

# Display the plot
plt.show()
```
- The ECDFs expose clear differences among the species
- Setosa is much shorter, also with less absolute variability in petal length than versicolor and virginica
