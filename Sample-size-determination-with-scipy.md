# Sample size determination with scipy 
<!-- vim-markdown-toc GFM -->

* [Introduction to Sample Size and A/B Testing](#introduction-to-sample-size-and-ab-testing)
* [A/B Testing: Using a Calculator](#ab-testing-using-a-calculator)
* [A/B Testing: Understanding the Baseline](#ab-testing-understanding-the-baseline)
* [A/B Testing: Determining Lift](#ab-testing-determining-lift)
* [A/B Testing: Don't Interfere With Your Tests](#ab-testing-dont-interfere-with-your-tests)
* [A/B Testing: Splitting a Test](#ab-testing-splitting-a-test)
* [Sample Size Calculator for Margin of Error](#sample-size-calculator-for-margin-of-error)
    * [Margin of Error](#margin-of-error)
    * [Population Size](#population-size)
    * [Likely Sample Proportion](#likely-sample-proportion)
    * [Confidence Level](#confidence-level)
* [Sample Size of a Survey](#sample-size-of-a-survey)
* [Differing Survey Results](#differing-survey-results)

<!-- vim-markdown-toc -->
## Introduction to Sample Size and A/B Testing
- One of the first steps to designing a successful experiment
    - is determining the sample size that you need in order to have confidence in the results
- We don’t want to go through the trouble of running an A/B test or administering a survey
    - only to discover that we don’t have enough information to make a good decision
- For instance, if we asked 5 people who they were voting for in an election
    - that small sample size would not be sufficient to predict the election results

- In this lesson we’ll cover two common types of experiment
    - and their __methods of sample size determination__:
        - A/B Tests
        - Surveys
- Online sample size calculators are available for both of these scenarios
    - These calculators will require quantities like
        - __baseline conversion rate__
        - or __population size__
    - but it’s not always obvious what these should be for a specific experiment
    - We’ll be covering that and more in this lesson.

## A/B Testing: Using a Calculator
- An A/B Test is a scientific method of choosing between two options (Option A and Option B)
- Some examples of A/B tests include:
    - What number of sale items on a website makes customers most likely to purchase something: 25 or 50?
    - What color button are customers more likely to click on: blue or green?
- In order to determine the sample size necessary for an A/B test, a sample size calculator requires three numbers:
    - The __Baseline conversion rate__
    - The __Minimum desired lift__ (also called the Minimum detectable effect)
    - The Statistical __significance threshold__

## A/B Testing: Understanding the Baseline
- A/B tests compare an option that we’re currently using to a new option that we suspect might be better
- In order to compare the two options, we need a metric
- Generally, our metric will be the percent of users who take a certain action after interacting with one of our options
- For instance:
    - The percent of customers who buy a t-shirt after visiting one of two versions of a website
    - The percent of users who click on one of two versions of an ad
    - The percent of readers who open an email with one of two subject lines
- Suppose we are running an A/B test to understand whether
    - customers are more likely to buy a shirt after visiting the current version of a website
    - or a new version with a more brightly colored design
- The `baseline conversion rate` is our estimate for the percent of people who will buy a shirt under the current website design
- This number may be written as a proportion (eg., .5) or a percent (eg., 50%)

- We can generally calculate a baseline by looking at historical data for the option that we’re currently using

## A/B Testing: Determining Lift
- We’re running an A/B Test in order to know
    - if Option B is better than Option A but if Option B were only a tiny percent better
        - would we really care?
- In order to detect precise differences, we need a very large sample size
    - In order to choose a sample size
    - we need to know the smallest difference that we actually care to measure

- This “smallest difference” is our `desired lift`
    - This is also sometimes referred to as the “minimum detectable effect” for the test

- Lift is generally expressed as a __percent__ of the __baseline conversion rate__
- Suppose that 6% of our customers currently buy socks on our website Sock Hops (that’s our baseline conversion rate)
- We think that a new website layout would increase this
- Changing a website layout is hard, so we only think that it’s worth doing if at least 8% of our customers would buy socks on Sock Hops with the new layout
- That means that we want to increase our conversions by 2%
- To calculate lift:
```
100 * (new - old) / old
100 * (8 - 6) / 6
33%
```
- Sock Hops’ desired lift is 33%.

## A/B Testing: Don't Interfere With Your Tests
- Brian the Product Manager has been running an A/B Test for a redesign of Viral Villanelle’s landing page
- Brian used the principles in the Sample Size Determination course on Codecademy to calculate a sample size
- He needs 1,100 users to view each variant of the landing page in order to be able to detect his __desired lift__
- When he reaches a total of 2,200 visits to both variants, he runs a Chi-Square test
- The new website design performs slightly better, but the results are not statistically significant
- Brian decides to run the test for another week to see if he can get to significance
- He really wants to launch the redesigned website and he needs statistical validation to show to his boss

- Brian has made a big mistake!
    - By choosing to extend the A/B test past the sample size he needs
        - he introduces personal bias to the results of the test

- If the results had already been significant, he wouldn’t have run the test any longer
- If he continues this pattern of preferentially extending the test when he wants a different answer
    - he will be more likely to get the results he wants
    - regardless if these desired results reflect reality

- It’s sad, but Brian will need to accept that the redesigned website isn’t significantly better than the original website

- Here are two important rules for making sure that A/B tests remain unbiased:
    1. Don’t continue to run the test after the predetermined sample size, until “significant” results are found
    2. Don’t stop a test before reaching the predetermined sample size
        - just because your results reach significance early
        - (unless there are ethical reasons that require you to stop, like a prescription drug trial)

- Test data is sensitive to changes in sample size
    - which is why it is important to calculate beforehand

## A/B Testing: Splitting a Test
- Viral Villanelle’s social media presence drives visits to its website
- Product Manager Brian wants to test a new ad
- Using a sample size calculator, he finds that he will need a sample size of 1,100
- Viral Villanelle’s current advertisement is shown to 500 users per day
- What’s the best way for Brian to get his desired sample size?

- It’s important to remember that Brian will need to show both the old and the new ad to 1,100 users each
- If Brian wants to complete this test as quickly as possible
    - he could randomly divide users into two groups:
        - half of users would see the old ad
        - and half would see the new ad
- It would take a little more than 4 days for 2,200 users to see one of the two ads

- What if Brian doesn’t want to divide Viral Villanelle’s audience evenly?
    - If Brian is running many different types of A/B tests, he might not want to expose users to a barrage of different tests
    - Maybe only 10% of users should be shown the new ad, in case it performs terribly
    - By doing this, he would only be getting 50 users per day towards the 1,100 users that need to see the new ad
    - In this case, he would need to wait for 22 days (1100 / 50 = 22) in order to get his results
    - even though he would have gotten the 1,100 views for the old ad 3 days into the experiment

- For his final analysis, Brian should use all of the data from the 22 days
    - The Chi-Square test will correctly take into account that there is more data from the original ad than from the new ad

## Sample Size Calculator for Margin of Error
- Let’s imagine that we own a juice bar called BeetsMe in the small town of Vancucumber
- We want to know what our customers’ favorite vegetable is so that we know what to base our next juice recipe around
- How many people do we need to survey to be confident in our results?

- It is easy to find a sample size calculator online, but it is difficult to determine what parameters to input
- Generally, sample size calculators use 4 parameters:
    - Margin of error
    - Confidence level
    - Population size
    - Expected proportion

- We have provided an example of a sample size calculator for you in the browser to the right
- In the next 4 exercises, we will explain what these parameters mean and how we can choose them to accurately represent our experiment

### Margin of Error
- What does it mean to have “enough” people for a survey? Generally
    - we are making sure that our results are within a margin of error of the correct answer

- The margin of error is the furthest we expect the true value to be from what we measure in our survey
- For example, let’s say we choose a margin of error of 4%
    - If we get results showing 40% of people love beets the most, we can be confident that the true proportion in the population lies somewhere between 36% and 44%
    - Thus, the smaller we make the margin of error, the more certainty we have in the results
    - The larger we make the margin of error, more uncertain we are that they represent the views of the total population

- In order to make our margin of error smaller, we will need a larger sample size

### Population Size
- Our sample should accurately represent the population as a whole
- So, when we are dealing with a larger population, we should probably be sampling more people

- It is sometimes tricky to determine what the effective population size is
- For example, suppose there are 200 people who currently visit BeetsMe regularly
    - Is 200 the population size for our vegetable survey?

- If BeetsMe wants to appeal to the tourists that frequently visit Vancucumber
- or if they ever want to launch an online store to ship healthy treats all over the world
    - the real population size is closer to 8 billion (or infinity, really
    - if we think about the number of humans who could eventually exist and have vegetable preferences)
- So, for experiments like this, we use the highest population size we can
- Normally, 100,000 will suffice, as changes become negligible beyond that

- Often, for decisions that require extrapolation to an unknown customer base
    - it is important to understand the preferences of a typical person out in the world
    - whether or not they are part of your customer base right now
- Generally, we use this larger population size of 100,000 or greater instead of focusing on the amount of current customers

- However, if the small town of Vancucumber is holding an election for a new mayor
    - and we want to project the results of the election, then the 1700 citizens would be the only important people
- In this case, 1700 is the population size we would use in a sample size calculator

### Likely Sample Proportion
- Often, before we conduct a survey, we have a guess of what we expect the results to be
    - This guess could be based upon the results from a previous survey
    - or perhaps the results of a small pilot study before the real study

- As the expected proportion of people with the desired trait decreases, we can survey fewer people
- For example
    - if we are projecting election results and Candidate C has 1% of the voter base
    - taking a small sample of only 5 people might be fine
    - because it is very likely that no one we have chosen is voting for Candidate C
- This is close enough to the true proportion

- As the expected proportion increases, it is rarer that we hit that proportion accurately with the random sample we choose

- If we do not have historical data, we normally use 50%, which gives the most conservative (i.e., largest required) sample size

### Confidence Level
- We also need to choose a confidence level
- The confidence level is the probability that the margin of error contains the true proportion
- For example
    - if we choose a confidence level of 99%
    - we can expect that after multiple repetitions of the survey
    - the true value will lie within our specified range 99% of the time
- As we increase the confidence level, we must have a larger sample size

- We normally use a confidence level of 95%
## Sample Size of a Survey
- Once we determine appropriate values for
    - the margin of error
    - confidence level
    - population size
    - and expected proportion values for our experiment
- we can use a sample size calculator
    - to determine the minimum sample size we need to survey
    - to get the desired confidence in our answer

- Let’s put together what we’ve learned so far
    - and determine the appropriate sample size for BeetsMe’s vegetable survey

## Differing Survey Results
- Suppose we are going to survey a group of high school students to see what programming language they want to learn
    - In the survey, we give the students two choices: JavaScript or Python
    - This seems like a problem where we would use a Sample Size Survey Calculator

- But what if we don’t care about getting a specific margin of error?
    - What if instead, we want to make a comparison:
        - Are girls more likely to want to learn Python than boys are?

- This survey is more similar to an A/B Test
    - Our baseline is the approximate percent of boys who want to learn Python
        - and our desired lift is the minimum difference between boys and girls that we want to be able to detect

- Whenever we want to make comparisons between subpopulations in our survey
    - we can use the A/B Test Calculator in order to get our desired survey size
