# introduction to hypothesis testing
<!-- vim-markdown-toc GFM -->

* [What is hypothesis testing?](#what-is-hypothesis-testing)
    * [Step 1: Ask a Question](#step-1-ask-a-question)
    * [Step 2: Define the Null and Alternative Hypotheses](#step-2-define-the-null-and-alternative-hypotheses)
    * [Step 3: Determine the Null Distribution](#step-3-determine-the-null-distribution)
    * [Step 4: Calculate a P-Value (or Confidence Interval)](#step-4-calculate-a-p-value-or-confidence-interval)
        * [Option 1](#option-1)
        * [Option 2](#option-2)
        * [Option 3](#option-3)
    * [Step 5: Interpret the Results](#step-5-interpret-the-results)
        * [Significance thresholds](#significance-thresholds)
        * [Impact of the Alternative Hypothesis](#impact-of-the-alternative-hypothesis)
* [Summary and further applications](#summary-and-further-applications)

<!-- vim-markdown-toc -->
- The goal of this unit is to learn about __hypothesis testing__ and how to design and implement a hypothesis test in Python
    - Understand the theory behind hypothesis testing
    - Form a null and alternative hypothesis for a hypothesis test
    - Interpret a __p-value__
    - Implement many __different hypothesis tests__ in Python, including 1- and 2-sample t-tests, ANOVA, Tukey’s range test, a Binomial test, and a Chi-Square test
    - Determine an appropriate sample size for a hypothesis test


- Introduction to Hypothesis Testing (learn about hypothesis testing by Simulating a One-Sample T-Test)
# What is hypothesis testing?
- Hypothesis Testing is a __framework__ for __asking__ questions about a dataset and __answering__ them with __probabilistic statements__
- There are many different kinds of hypothesis tests that can be used to address different kinds of questions and data
- In this article, we’ll walk through a simulation of a __one sample t- test__ in order to build intuition about how many different kinds of hypothesis tests work!

## Step 1: Ask a Question
- The International Baccalaureate Degree Programme (IBDP) is a world-wide educational program
- Each year, students in participating schools can take a standardized assessment to earn their degree
- Total scores on this assessment range from 1-45
- Based on data provided here, the average total score for all students who took this exam in May 2020 was around 29.92
- The distribution of scores looks something like this:
```image
population_distribution
```
- Imagine a hypothetical online school, Statistics Academy, that offers a 5-week test-preparation program
- Suppose that 100 students who took the IBDP assessment in May 2020 were randomly chosen to participate in the first cohort of this program
- and that these 100 students earned an average score of 31.16 points on the exam — about 1.24 points higher than the international average!
- Question : 
    - Are these students really outperforming their peers? Or could this difference be attributed to random chance?

## Step 2: Define the Null and Alternative Hypotheses
- Before attempting to answer this question, it is useful to __reframe__ it in a way that is testable
- Right now, our question (“Are the Statistics Academy students really outperforming their peers?”) is not clearly defined
- Objectively, this group of 100 students performed better than the general population 
- but answering “yes, they outperformed their peers!” doesn’t feel particularly satisfying

- The reason it’s not satisfying is this:
    - if we randomly choose ANY group of 100 students from the population of all test takers and calculate the average score for that sample
    - there’s a 50% chance it will be higher than the population average
    - Observing a higher average for a single sample is not surprising.

- Of course, large differences from the population average are less probable 
- if all the Statistics Academy students earned 45 points on the exam (the highest possible score)
- we’d probably be convinced that these students had a real advantage
- The trick is to quantify when differences are “large enough” to convince us that these students are systematically different from the general population
- We can do this by reframing our question to focus on population(s), rather than our specific sample(s)

- A hypothesis test begins with two competing hypotheses about the population that a particular sample comes from — in this case, the 100 Statistics Academy students:
    - Hypothesis 1 (technically called the __Null Hypothesis__):
        - The 100 Statistics Academy students are a random sample from the general population of test takers, who had an average score of 29.92
        - If this hypothesis is true, the Statistics Academy students earned a slightly higher average score by random chance
        - Visually, this set-up looks something like this:
```image
!null hypothesis
```
    - Hypothesis 2 (technically called the __Alternative Hypothesis__):
        - The 100 Statistics Academy students came from a population with an average score that is different from 29.92
        - In this hypothesis, we need to imagine two different populations that don’t actually exist:
            - one where all students took the Statistics Academy test-prep program
            - and one where none of the students took the program
        - If the alternative hypothesis is true, our sample of 100 Statistics Academy students came from a different population than the other test-takers
        - This can be visualized as follows:
```image
!alternative hypothesis
```
- There’s one more clarification we need to make in order to fully specify the alternative hypothesis
- Notice that, so far, we have not said anything about the average score for “population 1” in the diagram above, other than that it is NOT 29.92
- We actually have three choices for what the alternative hypothesis says about this population average:
    - it is GREATER THAN 29.92
    - it is NOT EQUAL TO (i.e., GREATER THAN OR LESS THAN) 29.92
    - it is LESS THAN 29.92
- Later on, we’ll discuss how the choice between “greater than”, “not equal to” and “less than” impacts the test

## Step 3: Determine the Null Distribution
- Now that we have our __null hypothesis__, we can generate a __null distribution__:
    - the distribution (across repeated samples) of the statistic we are interested in if the __null hypothesis__ is true
- In the IBDP example described above
    - this is the distribution of average scores for repeated samples of size 100 drawn from a population with an average score of 29.92
- This might feel familiar if you’ve learned about the __central limit theorem (CLT)__!
- Statistical theory allows us to estimate the shape of this distribution using a single sample
- You can learn how to do this by __reading more about the CLT__
- but for the purposes of this example, let’s simulate the __null distribution__ using our population
- We can do this by:
    - Taking many random samples of 100 scores, each, from the population
    - Calculating and storing the average score for each of those samples
    - Plotting a histogram of the average scores
- This __yields__ the following distribution, which is approximately normal and centered at the population average:
```image
!sampling_distribution
```
- If the __null hypothesis__ is true, then the average score of 31.16 observed among Statistics Academy students is simply one of the values from this distribution
- Let’s plot the sample average on the __null distribution__
- Notice that this value is within the range of the __null distribution__, but it is off to the right where there is less density:
```image
population_distribution_with_sample_mean
```
## Step 4: Calculate a P-Value (or Confidence Interval)
- Here is the basic question asked in our hypothesis test:

- Given that the __null hypothesis__ is true (that the 100 students from Statistics Academy were sampled from a population with an average IBDP score of 29.92)
- how likely is it that their average score is 31.16?

- The minor problem with this question is that the probability of any exact average score is very small
- so we really want to estimate the probability of a range of scores
- Let’s now return to our three possible __alternative hypotheses__ and see how the question and calculation each change slightly, depending on which one we choose:

### Option 1
- Alternative Hypothesis:
- The sample of 100 scores earned by Statistics Academy students came from a population with an average score that is `greater` than 29.92
        - In this case, we want to know the probability of observing a sample average greater than or equal to 31.16 given that the __null hypothesis__ is true
        - Visually, this is the proportion of the null distribution that is greater than or equal to 31.16 (shaded in red below)
        - Here, the red region makes up about 3.1% of the total distribution
        - This proportion, which is usually written in decimal form (i.e., 0.031), is called a __p-value__
```image
!one_sided_upper_test
```
### Option 2
- Alternative Hypothesis:
- The sample of 100 scores earned by Statistics Academy students came from a population with an average score that is `not equal to` 29.92.

- We observed a sample average of 31.16 among the Statistics Academy students
    - which is 1.32 points higher than the population average (if the __null hypothesis__ is true) of 29.92
- In the first version of the hypothesis test (option 1)
    - we estimated the probability of observing a sample average that is at least 1.32 points higher than the population average
- For the __alternative hypothesis__ described in option 2
    - we’re interested in the probability of observing a sample average that is at least 1.32 points DIFFERENT (higher OR lower) than the population average
- Visually, this is the proportion of the null distribution that is at least 1.32 units away from the population average (shaded in red below)
- Note that this area is twice as large as in the previous example, leading to a __p-value__ that is also twice as large: 0.062
```image
!two_sided_test
```
- While option 1 is often referred to as a One Sided or One-Tailed test
    - this version is referred to as a Two Sided or Two-Tailed test, referencing the two tails of the __null distribution__ that are counted in the __p-value__
- It is important to note that most hypothesis testing functions in Python and R implement a two-tailed test by default.
### Option 3
- Alternative Hypothesis: The sample of 100 scores earned by Statistics Academy students came from a population with an average score that is `less than` 29.92

- Here, we want to know the probability of observing a sample average less than or equal to 31.16, given that the __null hypothesis__ is true
- This is also a one-sided test, just the opposite side from option 1
- Visually, this is the proportion of the null distribution that is less than or equal to 31.16
- This is a very large area (almost 97% of the distribution!), leading to a p-value of 0.969
```image
lower_tail_test
```
- At this point, you may be thinking: why would anyone ever choose this version of the alternative hypothesis?!
- In real life, if a __test-prep__ program was planning to run a rigorous experiment to see whether their students are scoring differently than the general population
- they should choose the alternative hypothesis before collecting any data
- At that point, they won’t know whether their sample of students will have an average score that is higher or lower than the population average 
- although they probably hope that it is higher

## Step 5: Interpret the Results
- In the three examples above, we calculated three different p-values (0.031, 0.062, and 0.969, respectively)
- Consider the first __p-value__ of 0.031
- The interpretation of this number is as follows:
- If the 100 students at Statistics Academy were randomly selected from the full population (which had an average score of 29.92)
- there is a 3.1% chance of their average score being 31.16 points or higher

- This means that it is relatively unlikely, but not impossible
    - that the Statistics Academy students scored higher (on average) than their peers by random chance
    - despite no real difference at the population level
- In other words, the observed data is unlikely if the __null hypothesis__ is true
- Note that we have directly tested the __null hypothesis__ but not the __alternative hypothesis__!
- We therefore need to be a little careful about how we interpret this test:
    - we cannot say that we’ve proved that the alternative hypothesis is the truth 
    - only that the data we collected would be unlikely under null hypothesis
- and therefore we believe that the alternative hypothesis is more consistent with our observations

- Suppose that a random sample of 300 runners in the Boston Marathon were chosen to run in a new model of shoes: the Flying Flier
- The average finishing time for these 300 runners was 230 minutes, while the average finishing time for all runners was 233 minutes
- We ran a 2-sided one-sample __t-test__ with the following __null__ and __alternative__ hypotheses:
    - Null Hypothesis: The average finishing time for Boston Marathon runners wearing the Flying Flyer is equal to 233 minutes
    - Alternative Hypothesis: The average finishing time for Boston Marathon runners wearing the Flying Flyer is not equal to 233 minutes
- If we get a __p-value__ of 0.10 for this test, fill in the blanks to provide a correct interpretation of that number
- If the 300 runners were randomly selected from the full population of runners (who had an average finishing time of 233 minutes)
    - there is a  chance of their average finishing time being at least 3 minutes  the average finishing time of all runners

### Significance thresholds
- While it is perfectly reasonable to report a __p-value__
- many data scientists use a __predetermined threshold__ to decide whether a particular __p-value__ is significant or not
- __P-values__ below the chosen threshold are declared significant and lead the data scientist to “reject the __null hypothesis__ in favor of the alternative”
- A common choice for this __threshold__, which is also sometimes referred to as Alpha, is 0.05 — but this is an arbitrary choice!
- Using a lower threshold means you are less likely to find significant results
- but also less likely to mistakenly report a significant result when there is none

- Using the first __p-value__ of 0.031 and a __significance threshold__ of 0.05
- Statistics Academy could reject the __null hypothesis__
- and conclude that the 100 students who participated in their program scored significantly higher on the test than the general population

### Impact of the Alternative Hypothesis
- Note that __different alternative hypotheses__ can lead to __different conclusions__
- For example, the __one-sided test described above (p = 0.031)__ would lead a data scientist to __reject the null at a 0.05 significance level__
- Meanwhile, a two-sided test on the same data leads to a __p-value__ of 0.062, which is greater than the 0.05 __threshold__
- Thus, for the __two-sided test__, a data scientist could not reject the __null hypothesis__
- This highlights the importance of choosing an __alternative hypothesis__ ahead of time!

# Summary and further applications
- As you have hopefully learned from this article, __hypothesis testing__ can be a useful __framework__ for __asking and answering questions about data__
- Before you use hypothesis tests in practice, it is important to remember the following:
    - A __p-value__ is a probability, usually reported as a decimal between zero and one
    - A small p-value means that an observed sample statistic (or something more extreme) would be unlikely to occur if the __null hypothesis__ is true
    - A __significance threshold__ can be used to translate a __p-value__ into a “significant” or “non-significant” result
    - In practice, the __alternative hypothesis__ and __significance threshold__ should be chosen prior to data collection
- There are many different hypothesis tests that can be used to answer different kinds of questions about data
- Now that you’ve learned about one, you have all the skills you’ll need to understand many more!
