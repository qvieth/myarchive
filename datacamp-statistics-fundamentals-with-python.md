# datacamp statistics fundamentals with python

-   https://learn.datacamp.com/skill-tracks/statistics-fundamentals-with-python
- https://en.wikipedia.org/wiki/Anscombe%27s_quartet
- https://en.wikipedia.org/wiki/Descriptive_statistics
- https://en.wikipedia.org/wiki/Statistical_inference

## statistical thinking (part 1)

### graphical EDA

-   historgram
-   bee swarm plots
-   ECDF : empirical cumulative distribution function
    -   sort x
    -   y : max 1 - evenly space equal to data point

*   ecdf value generator function :

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

### quantitative EDA

-   summary statistics :
    -   mean
    -   median
-   covariance
-   pearson correlation coefficient

### thinking probabilistcally - discrete variables

-   statistical inference -> probability
-   random number generator :
    -   `np.random.seed()`
    -   `np.random.random()`
    -   `np.empty()`
-   bernoulli trial (aka binomial trial): coin flip
    -   p and 1 - p probability

```python
def perform_bernoulli_trials(n, p):
    """Perform n Bernoulli trials with success probability p
    and return number of successes."""
    # Initialize number of successes: n_success
    n_success = 0

    # Perform trials
    for i in range(n):
        # Choose random number between zero and one: random_number
        random_number = np.random.random()

        # If less than p, it's a success  so add one to n_success
        if random_number < p:
            n_success += 1

    return n_success
```

-   PMF (probability mass function)
    -   set of probabilities of discrete outcomes

*   distribution :
    -   a mathematical description of outcomes
    -   aka probability distribution

```python
# Take 10,000 samples out of the binomial distribution: n_defaults
n_defaults = np.random.binomial(n=100, p=0.05, size=10000)
# Compute CDF: x, y
x, y = ecdf(n_defaults)
```

### poisson process

-   the timing of the next event is completely independent of when the previous event happened
-   poisson is binomial distribution with rare event(low p ,high n)

```python
# Draw 10,000 samples out of Poisson distribution: samples_poisson
samples_poisson = np.random.poisson(10, size=10000)
```

## thinking probabilistically - continuous variables

-   `np.random.distribution_name()`
-   PDF (probability density function)
-   the probability is given by the area under PDF(think of histogram)
-   exponential distribtution :
    -   `np.random.exponential()`
-   a random process :
    -   when an event will happen is independent of
        -   when the last event was

# part 2

## parameter estimation by optimization

-   the importance of EDA
    -   anscombe's quartet - https://en.wikipedia.org/wiki/Anscombe%27s_quartet
    -   look before you leap
-   linear regression :
    -   `np.polyfit()`

## bootstrap confidence intervals

-   The bootstrap method is a resampling technique
    -   used to estimate statistics on a population
    -   by sampling a dataset with replacement.
    -   each resampled array is called a bootstrap sample
-   resampling engine :
    -   `np.random.choice(array,size=len(array))`
-   boostrap samples and replicates(statistics)
-   permutation :

```python
def permutation_sample(data1, data2):
    """Generate a permutation sample from two data sets."""

    # Concatenate the data sets: data
    data = np.concatenate((data1, data2))

    # Permute the concatenated array: permuted_data
    permuted_data = np.random.permutation(data)

    # Split the permuted array into two: perm_sample_1, perm_sample_2
    perm_sample_1 = permuted_data[:len(data1)]
    perm_sample_2 = permuted_data[len(data1):]

    return perm_sample_1, perm_sample_2
```

-   test statistics and p-value
- permutation replicate(bootstrap statistics)
- statistical significance(low p-values)
- practical significance
- p-value :
    - the probability of observing a test statistic
    - equally or more extreme than the one you observed
    - given that the null hypothesis is true
- A test statistic is a statistic used in statistical hypothesis testing
- a/b testing
    - used by organizations to see if a strategy change gives a better result 
- test of correlation

## final thoughts
- perform EDA :
    - graphical EDA
    - compute summary statistics
- estimate parameters
    - by optimization, including linear regression
    - determine confidence intervals
- formulate and test hypothesis
