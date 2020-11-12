# Introduction
- When conducting data analysis, we want to __say something meaningful__ about our data
- Often, we want to know if a change or difference we see in a dataset is “real”
    - or if it’s just a normal fluctuation
    - or a result of the specific sample of people we have chosen to measure
- A __difference__ we __observe__ in our data is __only important__
    - if we can be __reasonably sure__ that it is __representative__ of the __population as a whole__
    - and reasonably sure that our __result is repeatable__

- This question of whether a difference is significant or not is essential to making decisions based on that difference
- Some instances where this might come up include:
    - Performing an __A/B test__ — are the different observations really the results of __different conditions__ (i.e., Condition A vs. Condition B)?
        - Or just the result of __random chance__?
    - Conducting a survey — is the fact that men gave slightly different responses than women a real difference between men and women?
        - Or just the result of chance?

- In this lesson, we will cover the __fundamental concepts__ that will help us create tests to __measure our confidence__ in our __statistical results__:
    - Sample means and population means
    - The Central Limit Theorem
    - Why we use hypothesis tests
    - What errors we can come across and how to classify them
<!-- vim-markdown-toc GFM -->

* [Sample Mean and Population Mean](#sample-mean-and-population-mean)
* [Central Limit Theorem](#central-limit-theorem)
* [Hypothesis Tests : numpy all the way](#hypothesis-tests--numpy-all-the-way)
* [Type I Or Type II : 2 type of errors to consider : about correlation and related](#type-i-or-type-ii--2-type-of-errors-to-consider--about-correlation-and-related)
* [P-Values](#p-values)

<!-- vim-markdown-toc -->
## Sample Mean and Population Mean
- Suppose you want to know the average height of an oak tree in your local park
- On Monday, you measure 10 trees and get an average height of 32 ft
- On Tuesday, you measure 12 different trees and reach an average height of 35 ft
- On Wednesday, you measure the remaining 11 trees in the park, whose average height is 31 ft
- Overall, the average height for all trees in your local park is 32.8 ft

- The __individual measurements__ on Monday, Tuesday, and Wednesday are called __samples__
- A __sample is a subset of the entire population__
- The mean of each sample is the __sample mean__ and it is an __estimate__ of the __population mean__

- Note that the sample means (32 ft., 35 ft., and 31 ft.) were all close to the population mean (32.8 ft.)
- but were all slightly different from the population mean and from each other

- For a population, the mean is a constant value no matter how many times it’s recalculated
- But with a set of samples, the mean will depend on exactly what samples we happened to choose
- From a sample mean, we can then __extrapolate__ the mean of the population as a whole
- There are many reasons we might use sampling, such as:
    - We don’t have data for the whole population
    - We have the whole population data, but it is so large that it is infeasible to analyze
    - We can provide meaningful answers to questions faster with sampling

- When we have a numerical dataset and want to know the average value, we calculate the mean
- For a population, the mean is a constant value no matter how many times it’s recalculated
- But with a set of samples, the mean will depend on exactly what samples we happened to choose
- From a sample mean, we can then extrapolate the mean of the population as a whole

## Central Limit Theorem
- In real life, we probably won’t be able to collect lots of repeated samples
    - but luckily we can use something called the Central Limit Theorem
    - which tells us that a sample mean is more likely to be similar to the population mean if the sample size is large

## Hypothesis Tests : numpy all the way
- When observing differences in data, a data analyst understands the possibility that these differences could be the result of random chance
- Suppose we want to know if men are more likely to sign up for a given programming class than women
- We invite 100 men and 100 women to this class
- After one week, 34 women sign up, and 39 men sign up
- More men than women signed up, but is this a “real” difference?

- We have taken sample means from two different populations, men and women
- We want to know if the difference that we observe in these sample means reflects a difference in the population means
- To formally answer this question, we need to re-frame it in terms of __probability__:
    - “If we gave the same invitation to every person in the world, would more men still sign up?”
    - A more formal version is:
        - “What is the probability that
            - the two population means are the same
            - and the difference we observed in the sample means is just chance?”
- These statements are all ways of expressing a __null hypothesis__
- A null hypothesis is a statement that the __observed difference__ is the __result of chance__

- Hypothesis testing is a mathematical way of determining __whether we__ can be __confident__ that the __null hypothesis__ is __false__
- __Different situations__ will require __different types__ of __hypothesis testing__, which we will learn about in the next lesson

## Type I Or Type II : 2 type of errors to consider : about correlation and related
- When we rely on automated processes to make our decisions for us
    - we need to be aware of how this automation can lead to mistakes
- Computer programs are as fallible as the humans who design them
    - the responsibility is on us to understand
        - what can go wrong
        - and what we can do to contain these foreseeable problems

- In statistical hypothesis testing, we concern ourselves primarily with two types of error
1. The first kind of error, known as a Type I error, is finding a __correlation__ between __things__ that are __not related__
    - This error is sometimes called a __“false positive”__ and occurs when the null hypothesis is rejected even though it is true
        - For example, let’s say you conduct an A/B test for an online store
            - and conclude that interface B is significantly better than interface A at directing traffic to a checkout page
        - You have rejected the null hypothesis that there is no difference between the two interfaces
        - If, in reality, your results were due to the groups you happened to pick
            - and there is actually no significant difference between interface A and interface B in the greater population
            - you have been the victim of a false positive

2. The second kind of error, a Type II error, is __failing to find__ a __correlation__ between things that are actually __related__
    - This error is referred to as a __“false negative”__ and occurs when the null hypothesis is accepted even though it is false
        - For example, with the A/B test situation
            - let’s say that after the test, you concluded that there was no significant difference between interface A and interface B
        - If there actually is a difference in the population as a whole
            - your test has resulted in a false negative

## P-Values
- We have discussed how a hypothesis test is used to determine the __validity__ of a __null hypothesis__
- A hypothesis test provides a numerical answer
    - called a `p-value`, that helps us decide how confident we can be in the result
- In this context, a `p-value` is the probability that we yield the observed statistics under the assumption that the null hypothesis is true

- A p-value of 0.05 means that if the null hypothesis is true
    - there is a 5% chance that an observed sample statistic could have occurred due to random sampling error
- For example, in comparing two sample means
    - a p-value of 0.05 indicates there is a 5% chance that the observed difference in sample means occurred by random chance
    - even though the population means are equal

- Before conducting a hypothesis test
    - we determine the necessary threshold we would need before concluding that the results are significant
        - A __higher threshold__ is more likely to give a __false positive__
        - so if we want to be very sure that the result is not due to just chance
        - we will select a very small threshold

- It is important that we choose the significance level before we perform our statistical hypothesis tests to yield a p-value
    - If we wait until after we see the results
        - we might pick our threshold such that we get the result we want to see
    - For instance, if we’re trying to publish our results, we might set a significance level that makes our results seem statistically significant
    - Choosing our significance level in advance helps keep us honest

- Generally, we want a p-value of less than 0.05
    - meaning that there is less than a 5% chance that our results are due to random chance
