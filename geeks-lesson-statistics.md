# geek's lesson statistics
- https://www.youtube.com/watch?v=hjZJIVWHnPE

<!-- vim-markdown-toc GFM -->

* [1.1 Vocabulary and frequency tables](#11-vocabulary-and-frequency-tables)
* [1.2 Data and Sampling techniques](#12-data-and-sampling-techniques)
    * [level of measurement : NOIR](#level-of-measurement--noir)
    * [types of data](#types-of-data)
    * [Sampling : random to avoid bias](#sampling--random-to-avoid-bias)
* [1.3 Histogram and box plots](#13-histogram-and-box-plots)
    * [histogram - describe shape](#histogram---describe-shape)
    * [box plot - describe shape](#box-plot---describe-shape)
* [1.4 Measure of center and spread](#14-measure-of-center-and-spread)
* [2.1 Probability formulas](#21-probability-formulas)
    * [probability formulas :](#probability-formulas-)
* [2.2 Contigency tables and basic probabilities](#22-contigency-tables-and-basic-probabilities)
* [2.3 Tree diagrams and Bayes theorem](#23-tree-diagrams-and-bayes-theorem)
* [2.4 Discrete probability distribution](#24-discrete-probability-distribution)
* [2.5 Binomial Distribution](#25-binomial-distribution)
* [2.6 Poisson Distribution](#26-poisson-distribution)
* [2.7 Continuous probability distributions and the uniform distribution](#27-continuous-probability-distributions-and-the-uniform-distribution)
* [2.8 Normal distribution](#28-normal-distribution)
* [3.1 Central limit theorem](#31-central-limit-theorem)
* [3.2 Confidence Interval for Proportions](#32-confidence-interval-for-proportions)
* [*3.3 Hypothesis testing for single proportion](#33-hypothesis-testing-for-single-proportion)
* [3.4 Hypothesis testing for two proportion](#34-hypothesis-testing-for-two-proportion)
* [Confidence Interval for a Mean (5:52:00)](#confidence-interval-for-a-mean-55200)
* [Hypothesis Testing with a single Mean (6:7:00)](#hypothesis-testing-with-a-single-mean-6700)
* [Hypothesis Test for Two Means (6:45:00)](#hypothesis-test-for-two-means-64500)
* [Hypothesis Testing for Matched Pairs (6:25:00)](#hypothesis-testing-for-matched-pairs-62500)
* [Hypothesis Testing for Goodness of Fit (7:00:1)](#hypothesis-testing-for-goodness-of-fit-7001)
* [Hypothesis Testing for Independence (7:25:00)](#hypothesis-testing-for-independence-72500)
* [Hypothesis Testing a Single Variance (8:02:00)](#hypothesis-testing-a-single-variance-80200)
* [Hypothesis Testing for Two Variances (8:04:00)](#hypothesis-testing-for-two-variances-80400)
* [Hypothesis Test for Several Means (8:21:00)](#hypothesis-test-for-several-means-82100)
* [Hypothesis Testing for Correlation and Regression (8:35:00)](#hypothesis-testing-for-correlation-and-regression-83500)

<!-- vim-markdown-toc -->

## 1.1 Vocabulary and frequency tables
- what is statistics :
    - key vocabulary :
        1. __population__ - everything (or everyone) being studied
        2. parameter - characteristic of the population / numerical measurement of the population 
           - parameter - __greek letters__
        3. __sample__ - portion of the larger population
        4. statistic - characteristic of the sample / numerical measurement of the sample 
           - statistic - __english letters__
        5. variable - any characteristic of interest gathered from each item in the sample 
           - ex : in the question 'what is your GPA' - the variable is 'GPA'
        6. data - actual values of the variables

- identify key vocabulary :
- you want to know the average cost of math textbooks
- so you survey 25 textbooks :
    1. population - all math textbooks
    2. parameter - average cost of all math textbooks
    3. sample - 25
    4. statistics - average cost of 25 textbooks
    5. variable - cost of a math textbook
    6. data - actual cost of the text book ($23)

- frequency : how often a value occur
    - frequency table
        - table : 4 columns : data value, f, rf, crf


## 1.2 Data and Sampling techniques
- how is statistical data collected
- __levels of measurement__ :
### level of measurement : NOIR
- https://www.youtube.com/watch?v=LPHYPXBK_ks&feature=emb_title
- https://www.youtube.com/watch?v=hZxnzfnt5v8 : different charts and graphs for different level of measurement
- the levels of measurement that is used to measure a variable
    - has a significant impact on the type of tests researchers can do with their data
    - and therefore the conclusions they can come to
    - the higher the level of measurement the more statistical tests that can be run with the data
    - that is why it is best to use the highest level of measurement possible when collecting information
- reason for learning about the levels of measurement
    - is so you know __what statistical tests__ can be __performed__ on __different types of data__
    - that way you can avoid making mistakes in your own work and critique the work of others
- higher level of measurement means more possible measure
- level of measurement decision tree (8:32)
- summary (10:46)
### types of data
- category
- quantitative - measured or counted, numbers
- discrete - countable (digit)
- continuous - measured (decimal)

### Sampling : random to avoid bias
1. random
    1. simple random sampling - random selection methods such as random number or draw out of a hat
    2. stratified random sampling - divide population into groups and select a proportionate number at each group
    3. cluster random sampling - divide population into groups and randomly select entire groups
    4. systematic random sampling - start with a random item/person and choose every nth person after this
        - e.g. random number in phone book, then every 50th person after this (circle back to beginning)
2. non-random : convinience sampling - we results that are readily available
- e.g. people nearby, within drving distance
- drawbacks : bias result, may not be representative of the population, result may not be useful outside of the sample

## 1.3 Histogram and box plots
- how do we display data visually :
    - histogram - frequencies over intervals
    - box plot - spread with 5 number summary :
        - minimum
        - Q1
        - medium
        - Q3
        - maximum
### histogram - describe shape
1. uniform - bars about the same
2. normal - taller in middle, shorter on edges
3. V-shape - hosrter in middle, taller on edges
4. symmetrical - same on both sides
5. skewed - normal but more extra stuff on right/left

### box plot - describe shape
1. spread out - wide range of values
2. cluster together - small range of values
3. describe entire shape and middle 50% (box)

## 1.4 Measure of center and spread
- how do we summarize data numerically
- measure of center : mean, median, mode
- measure of spread :
    - all of the following have the same mean & median :
        - 1115999, 1245689, 5555555
    - range : large - small
        - problem with range : outlier can have great impact
    => interquartile range (IQR)
        - problem with IQR : only consider 2 values
    => standard deviation 
        - consider all the value and how spread out those are
        - measure the average distance from the mean
        - z is the number of standard deviation from the mean
        - x-bar +- standard deviation => outlier

## 2.1 Probability formulas
- Q : how do we calculate basic probabilities
- vocabulary :
    - sample space - all possible outcomes (flip a coin : H, T)
    - outcome - result of on experiment (flip a coin : H)
    - probability - chance that an event will occur - scale from 0 to 1
    - independent events - one occuring does not change the probability of the other occuring
- types of probability
    - theoretical probability - what should happen
        - P(E) = number of outcomes / sample space
    - empirical probability - what happened in an experiment
> **law of large number** - more trials done, the closer the empirical probability is to the theoretical probability

### probability formulas :
- dependent events
1. conditional probability : P(B|A) => probability of B given A has already occured
```
P(B|A) = P(A and B)/P(A)
```
2. AND : P(A and B) => probability both occur together
```
P(A and B) = P(A)P(B|A)
```
3. OR : P(A or B) => probability of A, or B or both
```
P(A or B) = P(A) + P(B) - P(A and B)
```

- independent events - one occuring does not change the probability of the other occuring
- can show this one of three ways :
    - P(A|B) = P(A)
    - P(B|A) = P(B)
    - P(A and B) = P(A)P(B)
- example :
    - in a class, 20% of students are left-handed
    - 5% of students are earning on A
    - only 1% of students are left handed and earning on A
- answer :
```
P(L)=.20
P(A)=.05
P(L and A)=.01
P(L and A)=P(L)P(A)
.01=(.2)(.05)
.01=.01
therefore they are independent event
```
- mutually exclusive (XOR) : both cannot occur at the same time

## 2.2 Contigency tables and basic probabilities
- Q : how do we organize probability information in a table
- A : __contigency table__ - table listing results in relation to two variables :
    - make calculating probabilities easier
    - add column and row for totals
    - example :

|                 | under 21 | 21-25 | over 25 | totals |
|-----------------|----------|-------|---------|--------|
| speeding ticket | 82       | 39    | 18      | 139    |
| no ticket       | 17       | 27    | 61      | 105    |
| totals          | 99       | 66    | 79      | 244    |

## 2.3 Tree diagrams and Bayes theorem
- Q : how do we visually organize conditional probabilities?
- A : tree diagram - branch for each outcome, we can multiply down branches for final probabilities
- bayes theorem : find P(B|A) using known values of P(A|B)
1. P(B|A) = P(A and B)/( P(A|B) + P(A|notB) )
    - tree makes this easy
2. A marketing company predicts 90% of new products are profitable
    - however, only 70% of those product predicted to be profitable actually are
    - in addition, those predicted to be not profitable
    - 20% actually are profitable
    - given a product was profitable
    - what is the probability it was

## 2.4 Discrete probability distribution
- Q : what are discrete probability distribtutions?
- A : probability distribution function (pdf):
    1. chracteristics
        - each probability is between 0 and 1
        - all probabilities sum to 1
    2. random variable - describes the outcome of an experiment
    3. discrete probability distribution - countable or discrete outcomes
    4. example let x = number of movies watched last week
        - a survey is conducted and it is found that 40% watched 2 movies, 50% watched 1 movie, the rest watched no movies
        - summarize the pdf in a table

| x | P(x) |
|---|------|
| 0 | .1   |
| 1 | .5   |
| 2 | .4   |

- expected value (mean) and standard deviation of pdf
    1. expected value - long term average (mean) of pdf 
        - mu =sigma(x*p(x)) 
```
| x | P(x) | x*p(x) |
|---|------|--------|
| 0 | .1   | 0      |
| 1 | .5   | .5     |
| 2 | .4   | .8     |
sigma(x*p(x))=1.3
```
    1. standard deviation - spread of random variable
        - o7 = squareroot(sigma((x-mu)**2*P(x))) 

## 2.5 Binomial Distribution
- Q : what is the probability of x successes out of n trials
- A : binomial distribution
    - characteristics
        - fixed number of trials
        - two options : 'success(x) or failure'
        - p = probability of success(x/n), q=probability of failure
    - distribution : X~B(n,p)
        - expected value : mu = np
        - standard deviation : sigma = squareroot(npq)
- using binomial distribution

## 2.6 Poisson Distribution
- Q : what is the probability of x success in a certain amount of time?
- A : poisson distribution
    - characteristics 
        - interested in number of successes in a fixed interval 
        - we have the average number of successes in that interval
    - distribution : X~P(mu)
        - mu = mu 
        - sigma = squareroot(mu)

## 2.7 Continuous probability distributions and the uniform distribution
- how do we find probabilities of continuous distributions?
- probability = area under a curve
    - f(x) = 1x/2  is a probability distribution function from 0 to 2

## 2.8 Normal distribution
- what is a normal distribution?
- normal distribution : f(x) = e/(sigma*squareroot(2pi))
    - shape : bell shape  
    - distribution : X~N(mu,sigma)
    - standard normal : Z~N(0,1)
        - has a table to help find areas 
        - change between regular Normal curve(x) and Standard normal curve(Z)
            - Z = (x-mu)/sigma
            - x = mu +z*sigma
                - x has meaning in context 
                - Z is the number of standard deviations from mean
        - table gives are between a z-value and mean(0)

## 3.1 Central limit theorem
- Q : how do we find probabilities with sample means?
- A : the Central Limit Theorem
    - the mean of a sample should be close to the mean of a population (with a smaller standard deviation)
    - the larger the sample, the closer to the mean, the smaller to the standard deviation
    - standard error - sigmax or se is the standard deviation of the sample means
        - se = sigmax/squareroot(n) = s/squareroot(n) 
    - distribution of the mean : X-bar~N(mu,s/squareroot(n)
    - z-scores : z = x-bar - mu / se

## 3.2 Confidence Interval for Proportions
- Q : how close is a sample proportion to a population proportion?
- A : proportion
    - underlying distribution is binomial : x=success , n=trials 
    - `p-hat = x/n`
    - p-hat~N(p-hat,squareroot(p-hat*q-hat/n) where q-hat =1 - p-hat
- confidence interval - an interval based on the sample statistics, where the population parameter is likely to be located
    - our sample statistic is likely off by some error 
        - `(p-hat - E, p-hat + E)` 
    - Confidence Level - probability the interval contains the population parameter
    - proportion error : `E = za/2 *squareroot(p-hat*q-hat/n)`
        - z-value that gives correct area in each tail 

## *3.3 Hypothesis testing for single proportion
- a significant part of statistics is testing a claim to bring a claim whether it's true
- Q : how do we test a claim for a proportion?
- A : hypothesis testing : test whether a claim is true
    1. set up 2 hypothesis 
        - H0 : null hypothesis (always use =) : always assume null hypothesis is true until proven otherwise 
        - Ha : alternate hypothesis (either use >,<,!=)
    2. run a sample
    3. calculate the probability the null hypothesis is true, based on our sample -> __p-value__
    4. compare to alpha or the smallest probability we still believe null hypothesis is true
    5. either reject the null hypothesis (p-value < alpha) or fail to reject null hypothesis (p-value > alpha)
- trial : person A is accused of a crime
    - H0 : innocent 
    - Ha : guilty
    - assume innocent until proven (p-value) gulty beyond a reasonable doubt (alpha)
    - 2 conclusion we can make :
        - if proven guilty : reject null hypothesis and conclude 'guilty'
        - if not : fail to reject null hypothesis and conclude 'not guilty'
        * `never conclude  H0 is true, always conclude alternative hypothesis be proven or can't be proven`
- conclusion : in context, focus on alternative hypothesis(Ha)
- formula with propotions : P-hat~N(p,squareroot(pq/n) 
- example :
    - a phone company claims 43% of smartphone users have an iphone
    - you doubt this claim
    - so you conduct a survey of 83 smartphone users
    - 44 of them use an iphone
    - what can you conclude if alpha = 0.5
- how to solve : 
    - H0 p = .43
    - Ha p !=.43
    - two-tailed test

## 3.4 Hypothesis testing for two proportion
- how do we test a claim about 2 proportion?
- equation needed
    - pooled proportion : Pc = (xa+xb)/(na+nb) 
    - distribution : P-hata - P-hatb~N(0,squareroot(Pc(1-Pc)(1/na + 1/nb)))
    - test statistic : Z = (P-hata - P-hatb)/Se
- example :
    - a restaurant wants to know if teens are more likely to order desert than adults
    - they contact a sample of 84 adults, 33 order desert
    - they contact a sample of 91 teens, 46 order desert
    - can they conclude teens are more likely to order desert if alpha = .10?
- how to sole :
    - H0 Pt = Pa
    - Ha Pt > Pa
    - right tailed test

## Confidence Interval for a Mean (5:52:00)
- Just as we've done inferential statistics with proportion 
- we can do the same thing with mean, in fact we're often working with mean than proportions
- Q : how do we find a confidence a confidence interval for a mean?
- A : no standard deviation of population - students-t distribution
    1. similar to normal, but it allows for greater flexibility as we use the sample standard deviation to estimate the population standard deviation 
    2. the larger the sample size, the less flexibility is needed
        - degrees of freedom : df=n-1 
        - if n>30, student-t is almost indentical to normal
        - if n<=30, use student-t table for critical values
- confidence interval for means
    1. X-bar~t(df)   df=n-1
    2. error : E = ta/2 *(S/squareroot(n))
    3. confidence interval : (x-bar - E, x-bar + E)
- example :
    - you are interested in the average cost of a smartphone
    - you take a sample of 16 smartphones and find a mean cost of 531 bucks with a standard deviation of 83 bucks

## Hypothesis Testing with a single Mean (6:7:00)
- Q : how do we conduct a hypothesis test for a mean?
- A : formulas for mean is different :
    - Distribution : X-bar~t(df)
    - standard error : Se = S/squareroot(n)
    - test statistic : t=(x-bar - mu)/Se
- example :
    - it is claimed the average page in a novel has 275 words per page
    - to test this claim, you sample 24 pages of a novel
    - you find the average page has 260 words with a standard deviation of 34 words
    - do you believe the claim is true if alpha=.05
- how to solve :
    - H0 : mu = 275
    - Ha : mu != 275
    - two-tailed test
    - distribution : x-bar~t23 (tdf-t`d`egreeof`f`reedom=23)

## Hypothesis Test for Two Means (6:45:00)
- Q : how do we compare 2 means?
- A : formulas :
    - distribution : x-bara - x-barb ~ t(df)
    - df is an ugly formula (we will use calculator)
    - Se = squareroot(Sa**2/na + Sb^2/nb)
    - t = (x-bara - x-barb)/Se
- example :
    - you want to know if there is a difference in GPA of online students and face-to-face students
    - you survey 32 online students who have an average GPA of 3.45 with a standard deviation of 0.7
    - you also interview 41 face-to-face students who have an average GPA of 3.67 with a standard deviation of 0.4
    - if alpha = .10 , can you conclude the groups are different?
- how to solve :
    - H0 = muOL = muF2F
    - Ha = muOL != muF2F
    - two-tailed test
    - actual difference : 3.45 - 3.67 = -.22
    - distribution : x-barOL - x-barF2F ~ t

## Hypothesis Testing for Matched Pairs (6:25:00)
- Q : how do we hypothesis test for improment (a difference)?
- A : matched pairs : all data come in pairs and the pairs are matched together
    - do a t-test for one mean -> find the difference for each pair 
    - distribution : x-bard~tdf   (df = n-1)
    - standard error : Se=Sd/squareroot(n)
    - test statistics : t = (x-bard - mud)/se
- example :
    - a football coach wants to know if a strength class can  help improve his players bench press weight
    - the before and after data is below

| player | A   | B   | C   | D   |
|--------|-----|-----|-----|-----|
| before | 205 | 241 | 338 | 368 |
| after  | 295 | 252 | 330 | 360 |

    - if alpha = .05, can the coach conclude the class was helpful 

- how to solve :
    - H0 : mud = 0
    - Ha : mud > 0
    - right tailed test
        - distribution : x-bard~t3
        - test statistics : t=.91
        - p-value : .2149 -> given our sample the probability the strength class made no difference in bench press weight is 21.49%
        - decision : fail to reject the null hypothesis
        - reason p-value > alpha (.2149 > .05
        - conclusion : there is not sufficient evidence to conclude the strength class increased bench press weights

## Hypothesis Testing for Goodness of Fit (7:00:1)
- Q : how do we test if data is fits a claimed distribution?
- A : Chi-squared (X**2):
    - non-symetrical and skewed right
    - different shape based on the degrees of freedom
    - always greater than zero
- Goodness-of-fit :
    - test statistic : chi**2=sigma((O-E)`**`/E 
        - O : Observed frequency 
        - E : Expected frequency
    - df = one less than the number of categories
    - H0 : data fits the distribution
    - Ha : data does not fit the distribution (right tailed test)
- example :
    - a researcher wants to verify a claim about her community that
    - 40% of residents speak Spanish in the home
    - 10% speak russian
    - 45% speak english
    - and 5% speak other languages
    - in a survey of 200 community members
    - 71 speak spanish, 23 speak russian, 102 speak english and 4 speak another language
    - if alpha=.05, can the researcher conclude the claimed distribution is accurate?
- how to solve :
    - H0 : language spoken in the home match distribution of the claim
    - Ha : languages spoken in the home doesnt match the claimed distribution
    - right tailed test
    - distribution : chi**2 ~ chi-sub3-squared
    - test statistic : ... make a statistic table
    - p-value : chi-squared cdf = .0853
        - -> based on the survey there is an 8.35% chance the proportion of people who speak various languages matches the claimed distribution
    - decision : fail to reject the null hypothesis
    - reason : p>alpha (.835 > .05)
    - conclusion : there is not sufficient evidence to conclude the distribution of languages spoken in the home is different than the claimed distribution

## Hypothesis Testing for Independence (7:25:00)
- another use for the chi-squared distribution is testing to see if 2 variables is dependent or independent on each other
- Q : how do we test  if 2 variables are dependent or independent
- A : test for independence :
    - collect for frequency data and organize in rows and columns
    - calculate expected frequency (2nd table) : E=(row)(column)/total
    - test statistic (3rd table) : chi-squared = Sigma(O-E)**2/E
    - df = (rows-1)(columns-1)
    - H0 : independent
    - Ha : dependent (right tailed test)
- example : a restaurant wants to know if breakfast preference is dependent on gender, the following data is collected :

|       | french toast | pancakes | waffles | omelettes | total |
|-------|--------------|----------|---------|-----------|-------|
| m     | 47           | 35       | 28      | 53        | 163   |
| f     | 65           | 59       | 55      | 60        | 239   |
| total | 112          | 94       | 83      | 113       | 402   |

    - if alpha = .05, can the restaurant conclude breakfast preference is dependent on gender
- how to solve :
    - H0 : breakfast preference is independent of gender
    - Ha : breakfast preference is dependent of gender
    - right tailed test
    - df : (2-1)(4-1)=3
    - distribution : chi-squared = chi-squared-sub3
    - test statistic : ... make a statistic table
    - p-value : chi-squared cdt -> based on our survey, there is a 25.93% chance that breakfast preference is independent of gender
    - decision : fail to reject null hypothesis
    - reason : p-value > alpha (.2935>.05)
    - conclusion : there is not sufficient evidence to conclude breakfast preference is dependent on gender

## Hypothesis Testing a Single Variance (8:02:00)
- Q : how do we test a claim about a variance
- A : Test a single variance :
    - test statistic : chi-squared = (n-1)s**2/sigma`**`2
    - be aware of what we have :
        - sigma and s -> standard deviation
        - sigma**2 and s`**`2 -> variance
    - df = n-1
    - can be either left/right/two-tailed test
- example :
    - a customer wants to know how the cost of school supplies varies from store to store
    - a teacher claims the standard deviation is only 15 bucks
    - the customer surveys 43 stores and find a mean of 884 bucks and a standard deviation of 12 bucks
    - test if the standard deviation is less than the teacher's claim of 15 bucks if alpha = .05
- how to solve :
    - H0 = sigma-squared = 15**2 =225
    - Ha = sigma-squared < 15**2 =225
    - left tailed test
    - df = 43 -1 =42
    - test statistic = chi-squared = (42-1)12**2/15`**`2
    - p-value : chi-squared cdf ( 0.26*88.42)=.0337
        - -> based on our sample the probability the standard deviation of the cost of school suppies being 15 is 3.37%
    - decision : reject the null hypothesis
    - reason : p<a(.0337<.05)
    - conclusion : there is sufficient evidence to conclude the standard deviation of school supplies cost is less than 15 bucks 

## Hypothesis Testing for Two Variances (8:04:00)
- Q : how do we comare two variances ?
- A : F-distribution :
    - not summetrical, skewed right
    - different shape based on df
    - fraction (ratio) with two sets of df
        - numberator : dfn=n1-1
        - denominator : dfd=n2-1
    - as df get larger the curve becomes more normal
    - f is always greater than (or equal to) zero
- two variances :
    - test statistic : F = (s1)**2/(s2)`**`2
    - equal variances F = 1
    - different variances, F is closer to 0 or infinity
- example :
    - quality control is interested in the variance of two machines making widgets
    - the first makes 32 widgets with a variance in the radius of 4.1 mm
    - the second makes 37 widgets with a variance in the radius of 3.7 mm
    - at alpha = .05
    - can quality control conclude the first machine has a higher variance?
- how to solve :
    - H0 = sigma1-squared = sigma2-squared
    - Ha = sigma1-squared > sigma2-squared
    - dfn = 31
    - dfd = 36
    - distribution : F~Fsub31,36
    - test statistic : 4.1/3.7 = 1.1081
    - p-value : .3809
        - -> based on our sample, the probability both machines have the same variance is 38.09% 
    - decision : fail to reject null hypothesis
    - reason : p>alpha
    - conclusion : there is insufficient evidence to conclude the first machine has a higher variance than the second machine

## Hypothesis Test for Several Means (8:21:00)
- Q : How do we compare the means of more than 2 groups?
- A : ANOVA (Analysis of Variance) :
    - hypothesis :
        - H0 : mu1 = mu2 = mu3 = ... = mun
        - Ha : at least one mean is different 
    - we use the F-test for compare
    - we look for a difference, but not where the difference is
- example :
    - a university is comparing traditional students, transfer students, and non traditional students
    - by comparing GPA in the Jr. year

| Trad | Trans | non-Trad |
|------|-------|----------|
| 3.2  | 3.1   | 3.4      |
| 3.4  | 2.7   | 2.2      |
| 3.7  | 2.9   | 2.7      |
| 4.0  | 3.2   | 2.8      |
|      | 4.0   |          |

    - if alpha = .10, can the university conclude there is a difference in the groups
- how to solve :
    - H0 : mutrad=mutran=munon-t
    - Ha : at least on group have a different GPA
    - F~Fsub2,10
    - F=3.07
    - p-value =.0912
        - -> based on our sample, the probability all three groups of students have the same mean GPA in Jr. year is 9.12%
    - decision : reject the null hypothesis
    - reason : p<alpha
    - conclusion : there is sufficient evidence to conclude the mean GPA of traditional, transfer and nontraditional students in the jr.year is not the same

## Hypothesis Testing for Correlation and Regression (8:35:00)
- Q : how do we test for a relationship between variables?
- A : scatterplot :
    - example : a researcher collects a sample of the number of pages a person reads, based on their age

| age | pages |
|-----|-------|
| 14  | 40    |
| 21  | 45    |
| 33  | 92    |
| 45  | 167   |
| 63  | 171   |

- make a scatterplot from this data
- resgression equation (line of best fit, least-squares line)
    - y=a+bx 
- correlation coefficient :
    - r -> strength and direction
    - r = 0 -> no relation
    - r = +-1 -> perfect positive relation (up)
    - r = -1 -> perfect negative relation (down)
- t-test (LinRegT-test) which gives a p-value that tells if the relationship is significant (p<alpha=.05)
- r tells the strength of the relationship

| r       | strength    |
|---------|-------------|
| 0-.199  | very weak   |
| .2-.399 | weak        |
| .4-.599 | moderate    |
| .6-.799 | strong      |
| .8-1.00 | very strong |

- r**2 = tells the amount of variation in the dependent variable that is explained by the independent variable
- age vs pg example :
    - run LinRegT-test :
        - t = 5.09
        - r =.947
        - p-value=.0147
        - r**2=.896
    - H0 : p=0 (no relationship)
    - Ha : p!=0(is a relationship)
    - decision : reject the null
    - conclusion : there is significant evidence to conclude there is a relationship between age and pgs read
        - because r=.947 the relationship is very strong
        - because r**2 =.896, we claim 89.6% of the variation in pages read is explained by age
