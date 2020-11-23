# Hypothesis Testing II
- tools to answer questions about data
- https://docs.scipy.org/doc/scipy/reference/stats.html
<!-- vim-markdown-toc GFM -->

* [Types of Hypothesis Tests](#types-of-hypothesis-tests)
    * [1 Sample T-Testing](#1-sample-t-testing)
    * [One Sample T-Test II](#one-sample-t-test-ii)
    * [2 Sample T-Test](#2-sample-t-test)
    * [Dangers of Multiple T-Tests](#dangers-of-multiple-t-tests)
    * [ANOVA](#anova)
    * [Assumptions of T-Tests and ANOVA](#assumptions-of-t-tests-and-anova)
    * [Tukey's Range Test](#tukeys-range-test)
    * [Binomial Test](#binomial-test)
    * [Chi Square Test](#chi-square-test)

<!-- vim-markdown-toc -->

## Types of Hypothesis Tests
- When trying to estimate something based on sample(s) from a larger population of interest
    - it is important to formulate specific questions and then __quantify uncertainty__ about the answers

- Some situations involve __numerical data__ :
    - a professor expects an __exam average__ to be roughly 75%
        - and wants to know if the actual scores line up with this expectation
        - or was the test actually too easy or too hard?
    - a manager of a chain of stores wants to know if certain locations have __different revenues__ on different days of the week
        - are the revenue differences a result of natural fluctuations
        - or a significant difference between the stores’ sales patterns?
    - a PM for a website wants to __compare the time spent__ on different versions of a homepage
        - does one version make users stay on the page significantly longer?

- Others involve __categorical data__ :
    - a pollster wants to know if men and women have significantly __different yogurt flavor__ preferences
        - Does a result where men more often answer “chocolate” as their favorite reflect a significant difference in the population?
    - do different age groups have significantly __different emotional reactions__ to different ads?

- In this lesson, you will learn how about how we can use hypothesis testing to help answer these questions
    - There are several different types of hypothesis tests for the various scenarios you may encounter
    - Luckily, SciPy has built-in functions that perform all of these tests for us, normally using just one line of code

- For numerical data, we will cover:
    - One Sample T-Tests
    - Two Sample T-Tests
    - ANOVA
    - Tukey Tests
- For categorical data, we will cover:
    - Binomial Tests
    - Chi Square
- After this lesson, you will have a wide range of tools in your arsenal to answer questions about your data

### 1 Sample T-Testing
- Let’s imagine the fictional business BuyPie
    - which sends ingredients for pies to your household so that you can make them from scratch
- Suppose that a product manager wants online BuyPie orders to cost around 1000 Rupees on average
    - In the past day, 50 people made an online purchase and the average payment per order was only 980 Rupees
    - Are people really spending less than 1000 Rupees on average? Or is this just the result of chance and a small sample size?

- We can test this using a 1 Sample T Test, which compares a sample mean to a hypothetical population mean

- When we conduct a 1 Sample T Test
    - we want to first create a null hypothesis
        - which is a prediction that the observed sample comes from a population with a particular mean
    - For example: “the average cost of a BuyPie order is 1000 Rupees”
        - Note that, even if the null hypothesis were true, it’s very unlikely that any observed sample mean will be exactly 1000.00 Rupees

- We also have to determine an alternative hypothesis
    - which is a statement about the kind of difference we are interested in
        - For example, we might form the following alternative hypothesis: “The average cost of a BuyPie order is not 1000 Rupees”

- If we form the null and alternative tests as indicated above
- the test asks the following question: “Suppose that that the average cost of a BuyPie order is 1000 Rupees
    - what is the probability of observing a sample of 50 orders with cost as different or more different from 1000 as we did (i.e., < 980 or > 1020)?”

- The result of the test is a p-value
    - If the p-value is less than our pre-chosen threshold (usually .05)
        - we can reject the null hypothesis in favor of the alternative
        - When we reject the null, we are saying that it would be unlikely to observe our sample (or something more extreme) if the null hypothesis were true

- SciPy has a function called `ttest_1samp`, which performs a 1 Sample T-Test for you
    - `ttest_1samp` requires two inputs :
        - a sample distribution (eg. the list of the 50 observed purchase prices)
        - and a mean to test against (eg. 1000):
```python
from scipy.stats import ttest_1samp
tstat, pval = ttest_1samp(example_distribution, expected_mean)
print pval
```
- It also returns two outputs: the t-statistic (which we won’t cover in this course)
    - and the p-value — telling us how confident we can be
    - that the sample of values came from a distribution with the specified mean

### One Sample T-Test II
- In the last exercise, we got a p-value that was much higher than 0.05, so we cannot reject the null hypothesis
- If we conduct another experiment and take a new sample of orders, will we get the same result? Not necessarily!

- Just because we don’t have enough data to detect a difference doesn’t mean that there isn’t one
    - Generally, the larger the sample(s) we have, the smaller a difference we’ll be able to detect
    - You can learn more about the exact relationship between sample size and detectable differences in the Sample Size Determination course

- It’s also possible that the true mean order price really is 1000 Rupees
    - but a single sample still leads us to incorrectly reject the null hypothesis
- Remember that this is called Type 1 Error
    - and the significance threshold we use for our test should be equal to the type 1 error rate under the null hypothesis
        - In other words, if we set a 0.05 significance threshold and the true mean purchase price is truly 1000 Rupees
        - we still expect to incorrectly reject the null (and say that the mean is not 1000 Rupees) in 5% of experiments

- To build intuition for the limitations of conclusions based on any individual sample
    - let’s explore some more data from BuyPie.com and see whether we consistently observe the same results
```python
from scipy.stats import ttest_1samp
import numpy as np

incorrect_results = 0 # Start the counter at 0

daily_prices = np.genfromtxt("daily_prices.csv", delimiter=",")

for i in range(1000): # 1000 experiments
   #your ttest here:
   t, pval = ttest_1samp(daily_prices[i], 1000) # perform t-test
   if pval < 0.05: # check our p-value
       incorrect_results += 1
    #print the pvalue here:
   print pval

print "We incorrectly thought that the distribution was different in " + str(incorrect_results) + " out of 1000 experiments."
```
### 2 Sample T-Test
- Suppose that a company has recently updated their website to make it more colorful and inviting
    - The company wants to know whether the new design is resulting in visitors staying on the site for a longer period of time
    - A sample of 100 visitors who saw the old design spent an average of 25 minutes on the site
    - A second sample of 100 visitors who saw the new version spent an average of 28 minutes on the site
    - Did the average time spent per visitor vary across groups? Or is this difference attributable to random chance?

- One way of testing whether this difference is significant is by using a 2 Sample T-Test
    - A 2 Sample T-Test compares two sets of numerical data.

- The null hypothesis of a 2 Sample T-Test is that the two observed samples come from populations with the same mean
    - In the example above, this means:
        - if we could observe all site visitors in two alternate universes (one where they see each version of the site)
        - the average visiting times in these universes would be equal

- The alternative hypothesis could be: The two observed samples come from populations with different means
    - In the example above, this would mean that the average visiting times in our two alternate universes are actually different
    - hence why we observed a difference in our samples

- We can use SciPy’s ttest_ind function to perform a 2 Sample T-Test
    - It takes the two samples as inputs and returns the t-statistic and a p-value
        - which we can use to assess the probability of an observed difference happening by chance if the null hypothesis were true
    - For more information about p-values, refer to the earlier exercise on univariate t-tests.
```python
from scipy.stats import ttest_ind
import numpy as np

week1 = np.genfromtxt("week1.csv",  delimiter=",")
week2 = np.genfromtxt("week2.csv",  delimiter=",")

week1_mean = np.mean(week1)
week2_mean = np.mean(week2)

print week1_mean, week2_mean

week1_std = np.std(week1)
week2_std = np.std(week2)

print week1_std, week2_std

tstat, pval = ttest_ind(week1, week2)
print pval
```
### Dangers of Multiple T-Tests
- Suppose that we own a chain of stores that sell ants, called VeryAnts
    - There are three different locations: A, B, and C
    - We want to know if the average ant sales over the past year are significantly different between the three locations

- At first, it seems that we could perform t-tests between each pair of stores

- We know that the p-value is the probability that we incorrectly reject the null hypothesis on each t-test
    - The more t-tests we perform, the more likely that we are to get a false positive, a Type I error

- For a significance threshold of 0.05
    - if the null hypothesis is true
        - then the probability of correctly failing to reject the null is 1 – 0.05 = 0.95
- When we run another t-test where the null is true
    - the probability of correctly failing to reject the null on both of those tests is 0.95 * 0.95, or 0.9025
- That means our probability of making an error
    - is now 1 - 0.9025
    - or close to 10%!
- This error probability only gets bigger with the more t-tests we do
```python
from scipy.stats import ttest_ind
import numpy as np

a = np.genfromtxt("store_a.csv",  delimiter=",")
b = np.genfromtxt("store_b.csv",  delimiter=",")
c = np.genfromtxt("store_c.csv",  delimiter=",")

a_mean = np.mean(a)
b_mean = np.mean(b)
c_mean = np.mean(c)

a_std = np.std(a)
b_std = np.std(b)
c_std = np.std(c)

a_b_pval = ttest_ind(a, b).pvalue
a_c_pval = ttest_ind(a, c).pvalue
b_c_pval = ttest_ind(b, c).pvalue

error_prob = (1-(0.95**3))
```
### ANOVA
- In the last exercise, we saw that the probability of making a Type I error got dangerously high as we performed more t-tests

- When comparing more than two numerical datasets, one way to preserve a Type I error probability of 0.05 is to use ANOVA
    - ANOVA (Analysis of Variance) tests the null hypothesis that all of the samples come from populations with the same mean
    - If we reject the null hypothesis with ANOVA
        - we’re saying that at least one pair of populations (from which the samples were drawn) have different means;
        - however, we cannot determine exactly which pair(s)

- We can use the SciPy function f_oneway to perform ANOVA on multiple datasets
    - f_oneway takes in each dataset as a different input and returns the F-statistic and the p-value
    - For example :
        - if we were comparing scores on a videogame between
            - math majors
            - writing majors
            - and psychology majors
        - we could run an ANOVA test with this line:
```python
from scipy.stats import f_oneway
fstat, pval = f_oneway(scores_mathematicians, scores_writers, scores_psychologists)
```
- The null hypothesis, in this case, is that all three populations have the same mean score on this videogame
    - If we reject this null hypothesis (if we get a p-value less than 0.05)
    - we can say that we are reasonably confident that at least one pair of populations is significantly different
    - After using only ANOVA, we can’t make any conclusions on which two populations have a significant difference

### Assumptions of T-Tests and ANOVA
- Before we use one or two sample t-tests or ANOVA, we need to be sure that the following things are true:
1. The sample(s) should be normally distributed…ish
    - Data analysts in the real world often still perform t-tests or ANOVAs on data that are not normally distributed
    - This is usually not a problem if sample size is large, but it depends on how non-normal the data is
    - In general, the bigger the sample size, the safer you are!
2. The standard deviations of the samples should be equal
    - For ANOVA and 2-Sample T-Tests
        - using datasets with standard deviations
            - that are significantly different from each other
                - will often obscure the differences in group means
    - That said, there is also a way to run a 2-Sample T-Test without assuming equal standard deviations
        - (for example, by setting the equal_var parameter in the scipy.stats.ttest_ind() function equal to False)
        - Running the test in this way has some disadvantages
            - (it essentially makes it harder to reject the null hypothesis even when there is a true difference between groups)
            - so it’s important to check for equal standard deviations before running a test
    - To check this assumption
        - it is normally sufficient to divide the two standard deviations and see
        - if the ratio is “close enough” to 1
        - “Close enough” may differ in different contexts but generally staying within 10% should suffice
        - This equates to a ratio between 0.9 and 1.1.
3. The samples must be independent
    - When comparing two or more datasets
        - the values in one distribution should not affect the values in another distribution
    - In other words, knowing more about one distribution should not give you any information about any other distribution
    - Here are some examples where it would seem the samples are not independent:
        - the number of goals scored per soccer player before, during, and after undergoing a rigorous training regimen
        - a group of patients’ blood pressure levels before, during, and after the administration of a drug
    - It is important to understand your datasets before you begin conducting hypothesis tests on them
        - so that you know you are choosing the right test

### Tukey's Range Test
- Let’s say that we have performed ANOVA to compare three sets of data from the three VeryAnts stores
    - We received the result that there is some significant difference between datasets

- Now, we have to find out which datasets are different

- We can perform a Tukey’s Range Test to determine the difference between datasets

- If we feed in three datasets
    - such as the sales at the VeryAnts store locations A, B, and C
    - Tukey’s Test can tell us which pairs of locations are distinguishable from each other

- The function to perform Tukey’s Range Test is pairwise_tukeyhsd, which is found in statsmodel, not scipy
    - We have to provide the function with one list of all of the data
    - and a list of labels that tell the function which elements of the list are from which set
    - We also provide the significance level we want, which is usually 0.05

- For example
    - if we were looking to compare mean scores of movies that are
        - dramas
        - comedies
        - or documentaries
    - we would make a call to pairwise_tukeyhsd like this:
```python
from statsmodels.stats.multicomp import pairwise_tukeyhsd
movie_scores = np.concatenate([drama_scores, comedy_scores, documentary_scores])
labels = ['drama'] * len(drama_scores) + ['comedy'] * len(comedy_scores) + ['documentary'] * len(documentary_scores)
 
tukey_results = pairwise_tukeyhsd(movie_scores, labels, 0.05)
```
- It will return a table of information
    - telling you whether or not to reject the null hypothesis for each pair of datasets

### Binomial Test
- Let’s imagine that we are analyzing the percentage of customers who make a purchase after visiting a website
    - 1000 customers visited the site this month, and 58 of them made a purchase
    - The marketing department reports that historical data suggests about 72 of every 1000 visitors make a purchase
    - Thus, they estimate that the probability of any particular customer making a purchase is 7.2%
    - We would like to know if this month’s number, 58 purchases
        - is significantly different from normal or a reasonable fluctuation due to random chance

- In previous exercises, we collected samples of numerical information (eg. order price)
    - and then used the mean and standard deviation of those samples to make comparisons
        - In contrast, we now have a sample where each unit (a visitor) falls into one of two discrete categories:
            - “made a purchase”
            - “did not make a purchase”

- Instead of comparing sample means, we want to compare the percent in the “made a purchase” category to some expectation
    - This can be done with a Binomial Test
    - The binomial distribution describes the number of expected “successes” in an experiment with some number of “trials”
    - In this case, our experiment consists of 1000 people visiting the site
    - For each of those trials (visitors), we expect that there is a 7.2% chance of a purchase (success)

- SciPy has a function called binom_test(), which performs a Binomial Test for you
    - In this example, the null hypothesis is that the true probability of a purchase is 7.2%
    - The default alternative hypothesis for the binom_test() function in this example is that the true probability is not 7.2%

- binom_test() requires three inputs, the number of observed successes, the number of total trials, and an expected probability of success
    - For example, with 1000 coin flips of a fair coin
        - we would expect a “success rate” (the rate of getting heads)
        - to be 0.5, and the number of trials to be 1000
        - Let’s imagine we get 525 heads
        - Is the coin weighted? This function call would look like:
```python
from scipy.stats import binom_test
pval = binom_test(525, n=1000, p=0.5)
```
- It returns a p-value
    - telling us how likely we are to observe at least this much deviation from expectation (> 525 heads or < 475 heads)
        - given that the true probability of heads on any flip was 0.5 (meaning our expectation was 500 heads)
    - If we get a p-value less than 0.05
        - we can reject the null hypothesis
        - and say it is unlikely that the true probability of heads was 0.5 on each flip
        - suggesting that the coin is weighted.

### Chi Square Test
- In the last exercise, we looked at data where customers visited a website and either made a purchase or did not make a purchase
    - What if we also wanted to understand if the probability of making a purchase depends on some other categorical variable, like gender?
    - If we want to understand whether the outcomes of two categorical variables are associated, we should use a Chi Square test
    - It is useful in situations like:
        - An A/B test where half of users were shown a green submit button and the other half were shown a purple submit button
            - Was one group more likely to click the submit button?
        - People under and over age 40 were given a survey asking “Which of the following three products is your favorite?”
            - Did these age groups have significantly different preferences?

- In SciPy, you can use the function chi2_contingency to perform a Chi Square test

- The input to chi2_contingency is a contingency table where:
    - The columns are each a different condition, such as Interface A vs. Interface B
    - The rows represent different outcomes, like “Clicked a Link” vs. “Didn’t Click”

- This table can have as many rows and columns as you need

- Let’s return to the question of whether gender is associated with the probability of a website visitor making a purchase
    - The null hypothesis is that there’s no association between the variables
        - (eg. males, females, and non-binary people are all equally likely to make a purchase on the website
            - so gender and purchase-status are not associated)
    - If the p-value is below our chosen threshold (often 0.05)
        - we reject the null hypothesis and can conclude there is a statistically significant association between the two variables
            - (eg. men, women, and non-binary people appear to have different probabilities of making a purchase
                - so gender is associated with purchase-status).
```python
from scipy.stats import chi2_contingency

# Contingency table
#         harvester |  leaf cutter
# ----+------------------+------------
# 1st gr | 30       |  10
# 2nd gr | 35       |  5
# 3rd gr | 28       |  12
# 4th gr | 20 .     |  20

X = [[30, 10],
     [35, 5],
     [28, 12],
     [20, 20]]
chi2, pval, dof, expected = chi2_contingency(X)
print pval
```
