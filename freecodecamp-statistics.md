# freecodecamp statistics
- https://www.youtube.com/watch?v=xxpc-HPKN28
- https://brownmath.com/swt/symbol.htm

## Contents

- [freecodecamp statistics](#freecodecamp statistics)
- [Chapter 1.1 : What is statistics](#Chapter 1.1 : What is statistics)
- [Chapter 1.2 : Sampling](#Chapter 1.2 : Sampling)
- [Chapter 1.3 : Introduction to experimental design](#Chapter 1.3 : Introduction to experimental design)
- [Chapter 1.4 : Avoiding bias in survey design (important)](#Chapter 1.4 : Avoiding bias in survey design (important))
- [Chapter 1.5 : Topics in Randomization](#Chapter 1.5 : Topics in Randomization)
- [Chapter 2.1 : Frequency histograms and distribution](#Chapter 2.1 : Frequency histograms and distribution)
- [Chapter 2.2 : Other graphs](#Chapter 2.2 : Other graphs)
- [Chapter 3.1 : Measures of Central Tendency](#Chapter 3.1 : Measures of Central Tendency)
- [Chapter 3.2 : Measures of Variation](#Chapter 3.2 : Measures of Variation)
    - [Chebyshev Theorem](#Chapter 3.2 : Measures of Variation#Chebyshev Theorem)
- [Chapter 3.3 : Percentiles and Box-and-Whisker Plots](#Chapter 3.3 : Percentiles and Box-and-Whisker Plots)
- [Chapter 4.1 : Scatter Plots and Linear Correlation](#Chapter 4.1 : Scatter Plots and Linear Correlation)
    - [correlation coefficient r](#Chapter 4.1 : Scatter Plots and Linear Correlation#correlation coefficient r)
    - [Lurking variables and 'correlation is not causation'](#Chapter 4.1 : Scatter Plots and Linear Correlation#Lurking variables and 'correlation is not causation')
    - [conclusion](#Chapter 4.1 : Scatter Plots and Linear Correlation#conclusion)
- [Chapter 4.2 : Linear Regression and the Coefficient of Determination](#Chapter 4.2 : Linear Regression and the Coefficient of Determination)
    - [Least-squares criterion](#Chapter 4.2 : Linear Regression and the Coefficient of Determination#Least-squares criterion)
    - [coefficient of determination : get out of the r](#Chapter 4.2 : Linear Regression and the Coefficient of Determination#coefficient of determination : get out of the r)
    - [summary](#Chapter 4.2 : Linear Regression and the Coefficient of Determination#summary)
    - [Chapter 7.1 : normal distribution & empirical rule](#Chapter 4.2 : Linear Regression and the Coefficient of Determination#Chapter 7.1 : normal distribution & empirical rule)
    - [empirical rule](#Chapter 4.2 : Linear Regression and the Coefficient of Determination#empirical rule)
- [Chapter 7.2 & 7.3 : Z-scores & Probabilities](#Chapter 7.2 & 7.3 : Z-scores & Probabilities)
- [Chapter 7.4 & 7.5 : Sampling distributions and the central limit theorem](#Chapter 7.4 & 7.5 : Sampling distributions and the central limit theorem)
    - [types of inferences :](#Chapter 7.4 & 7.5 : Sampling distributions and the central limit theorem#types of inferences :)
    - [frequency vs sampling distribution](#Chapter 7.4 & 7.5 : Sampling distributions and the central limit theorem#frequency vs sampling distribution)
    - [central limit theorem](#Chapter 7.4 & 7.5 : Sampling distributions and the central limit theorem#central limit theorem)

| measure            | statistic | parameter     |
|--------------------|-----------|---------------|
| mean               | x-bar     | mu            |
| variance           | s**2      | sigma squared |
| standard deviation | s         | sigma         |
| propotion          | p-hat     | p             |

# Chapter 1.1 : What is statistics
- population(people or objects) parameters vs sample statistics
- individual vs variables
- classifying variable (levels of measurement):
    1. quantitative : interval + ratio
    2. category : norminal(can't be ordered) + ordinal(can be ordered)
- describing vs inferring statistics
# Chapter 1.2 : Sampling
- 34:27
- at the end of this lecture, the student should be able to :
    - define '__sampling frame__' and '__sampling error__'
    - give one example of how to do __simple random sampling__, and one sample of how do __systematic sampling__
    - explain one reason to choose __stratified sampling__ over other approaches
    - state two differences between cluster sampling and convenience sampling
    - give an example of a national survey that uses multi-stage sampling

- sampling :
    - simple random sampling (SRS) : means equal chance of being selected
    - stratified sampling : cover subpopulation
    - systematic sampling
    - cluster sampling : devide map into clusters
    - convenience (can be biased, often miss important subpopulation)
    - and multistage sampling : combination of sampling strategies layered in stages
- we take a sample of the population because we want to do 'inferential statistics'
    - we want to infer from the sample to the population
- reason not to measure the whole population
    - impractical
    - unecessary

- sampling frame :
    - list of individual from which a sample is actually selected
    - list maybe physical, concrete list
        - list of student enrolled at a nursing college
    - maybe a theoretical list not made up yet
        - list of patient who will present to the emergency department today
- __sample error__ vs __non-sample error__
- data datum, strata stratum

# Chapter 1.3 : Introduction to experimental design
- 1:21:33
- at the end of this lecture, the student should be able to :
    - state the steps of conducting a __statistical study__
    - select one step of developing a statistical study, and state the reason for this step
    - name one common mistake that can introduce bias to a survey, and give an example
    - explain what a lurking variable is , and given example
    - define what a completely randomized experiment is

- basic guidelines for planning a  statistical study :
    1. state a hypothesis
    2. identify the individuals of interest
    3. specify the variables to measure
    4. determine if you will use the entire population or a sample
        - if you choose a sample, choose a  sampling method
    5. address ethical concerns before data collection
    6. collect the data
    7. use descriptive or inferential statistics to answer your hypothesis
    8. note any concerns about your data collection or analysis
        - make recommendations for future studies

- eperiment vs observational study
- replication : studies must be done rigorously enough to be replicated

# Chapter 1.4 : Avoiding bias in survey design (important)
- surveys can provide a lot of useful information
- however, it is important that all aspects of survey design and administration __minimize__ 'bias'
- several considerations should be made

1. non-response and voluntary response
    - if many people refuse your survey, the people who do complete it are likely to have a biased opinion
    - there may be a reason they do not complete your survey that has to do with how they feel about your survey topic
2. truthfulness of reponse
    - respondents may lie on purpose:
        - if asked a question that is too personal
        - if asked a question too hard to think about
    - respondents may lie inadvertently
        - may not remember if asking about something that happened a long time ago
        - may have 'recall bias' influanced by events that have happened since original event
3. hidden bias :
    - question wording may induce a certain response
        - how long have you been using software A
    - order of questions and other wording may induce a certain response
        - do you agree with obamacare?
        - more people have health insurance than ever before, do you agree with obamacare?
    - scales of question may not accurately measure responses
        - do you feelings always fit on a scale of 1 to 5
4. interviewer influence
5. avoid vague terms used in a survey
- instead of asking if a person have waited 'a long time' in the waiting room, ask the number of minutes
6 lurking variables (can cause confounding)

# Chapter 1.5 : Topics in Randomization
- randomize: help distributing lurking variables evenly 

# Chapter 2.1 : Frequency histograms and distribution
- histogram vs reletive frequency histogram
- 5 main types of distributions
1. normal distribution (symetric)
2. uniform distribution
3. skewed left distribution
4. skewed right distribution
5. bimodal distribution

- histograms and stem-leaf plot are used to look for __outliers__
- the purpose of histogram and stem-leaf plot is to reveal the distribution
- knowing the distribution is important in statistics

# Chapter 2.2 : Other graphs
- at the end of this lecture, the student should be able to:
    - describe a case in which a __time-series graph__ would be appropriate
    - explain the difference between what would be graphed on a __bar__ vs a __time-series__ graph
    - describe the type of data graphed in a __pie chart__
    - list two considerations to make when choosing what type of chart to develop

- frequency tables vs stem-leaf plot : main purpose is to reveal __distribution__
    1. frequency tables
        - are necessary for organizing quantitative data
        - set up classes, class widths
        - lots of pre-calculations
    2. stem-leaf plot
        - just another way to organize quantitative data
        - do not need to set up classes or class widths
        - no need to count
        - quicker than frequency table to do

# Chapter 3.1 : Measures of Central Tendency
- At the end of this lecture, the student should be able to:
    - Explain how to calculate the mean
    - Describe what a mode is and say how many modes a dataset can have
    - demonstrate how to find the median in a set of data with an odd number of values, as well as in a set of data with an even number of values
    - define __trimmed mean__(cut down x% data from top and bottom) and __weighted average__(how university score is like)
- what is Central Tendency things : mean median mode
- __sigma__ (sum of) is used a lot in statistics 

# Chapter 3.2 : Measures of Variation
- __coefficient__ of variation
- coefficient is use for comparison
- s
## Chebyshev Theorem
- 1 - 1/(k**2) = % of data between x-bar minus k and x-bar plus k
- take-home message on chebyshev interval :
    - it works for any distribution(normal, skewed, etc)
    - Chebyshev intervals tell you that at least a certain % is in the interval
    - Chebyshev intervals are sometimes non-sensical(negative number, very high limits)
    - they are not very useful and not used in healthcare
    - the purpose of teaching this is to point our :
        - in statistics, we often use the s o 6 and add/subtract it from the mean
        - because it is a good way to make lower and upper limits that have special significance

# Chapter 3.3 : Percentiles and Box-and-Whisker Plots
- at the end of this lecture, the student should be able to :
    - explain what a percentile means
    - describe what the 'interquartile range' is and how to calculate it
    - explain the steps to making a box-whisker plot
    - state how a box-whisker plot helps a person evaluate the distribution of the data
- what are percentiles :
    - quantitative data
    - remember standardized tests
    - example : __if you test at the 77th percentile, it means you did better than 77% of the people taking the test__
    - if 100 people took the test, you'd have done better than 77 of them
- percentile rules:
    - be between 1 and 99 : you can't have a -2nd percentile or a 105 percentile
    - whatever number you pick:
        - that % of value fall below the number
        - and 100 minus that % of values fall above the number
    - example : 20 people take a test :
        - let's say there is a maximum score of 5 on the test
        - the 25th percentile mean 25 of the scores fall below this score, and 75% fall above that score
    - let's say it is an easy test, and 12 people get a 4, and the remaining 8 get a 5,
    - the 25th percentile, or the score the cuts off the bottom 5 tests scores, will be 4(even the 50th percentile will be 4)
    - this would come out very different if it were a hard test, and most people got below a score of 3
- quartiles is a specific set of percentiles:
    - 1st quartile : 25th percentile
    - 2nd quartile : 50th percentile
    - 3rd quartile : 75th percentile
- box-whisker plot :
    - minimum
    - Q1
    - median
    - Q3
    - maximum
- why box-whisker plots:
    - another way to look at distribution
    - also can see spread of data

# Chapter 4.1 : Scatter Plots and Linear Correlation
- linear correlation :
    - direction : positive, negative, no correlation
    - strength : strong, moderate, weak
- outliers can havea very powerful effect on a correlation
- an outlier in any of the 4 corners of the plot can really affect the __direction__ of the line
- an outlier can also change the correlation from __strong and moderate to weak__
- it's good to look at a scatterplot to make sure you identify outliers

## correlation coefficient r
- putting a number on correlation
- a numerical quantification of how correlated a set of x,y pairs are
- calculated from plugging x,y pairs into an equation
- opinion :
    - for negative correlations :
        - -0.0 to -0.4 : weak
        - -0.4 to -0.7 :moderate
        - -0.7 to -1.0 : strong
- facts about r :
    - r requires data with a bivariate normal distribution
    - r does not have units
    - perfect linear correlation is r=-1.0 or r=1.0(depending on direction)
    - no linear correlation is r=0
    - positive r means as x goes up, y goes up, as x goes down, y goes down
    - negative r means as x goes up, y goes down, as x goes down, y goes up
    - even if you switched x and y on the axes, you'd get the same r

## Lurking variables and 'correlation is not causation'
- beware of lurking variables
- selecting x and y is political - you are implying x could cause y
    - example : taller people are heavier so x=height and y=weight 
    - people who are overweight do not suddenly grow taller
- but there are other causes of weight besides height
- genetics can cause both height and weight
    - a genetic profile that leads to tallness and obesity could be a lurking variable in the relationship between height and weight 
- examples => please don't ...ban ice cream just to bring down the murder rate, ...make us eat tons of onions just to increase the stock market

## conclusion
- when doing correlations, make scatterplots first to get an idea of strength, direction, and outliers
- be careful when calculating r by hand
- beware of lurking variables - __correlation__ is not necessarily __causation__

# Chapter 4.2 : Linear Regression and the Coefficient of Determination
- at the end of this lecture, the student should be able to:
    - explain what the 'least-squares line' is
    - identify and describe the components of the least-squares line equation
    - explain how to calculate the residuals
    - calculate and interpret the coefficient of determination(CD)
- crystalball:
    - predict the future 
    - least-squares line
    - least-squares line equation
    - dealing with prediction using the least-squares line
    - coefficient of determination

## Least-squares criterion
- residual : y minus y-hat
- y-hat = ax - b
- to evaluate if our least-squares line equation is should be used for interpretation, we use the coefficient of determination

## coefficient of determination : get out of the r
- also called r^2 : like CV, we turn it into a %
- 100% - CD = unexplained variation

## summary
- we started with quantitative x,y pairs
- we made a scatterplot to look at the linear relationship between x and y, and look at outliers
- we calculated r to see if our correlation was positive or negative, and weak, moderate or strong
- we calculated b and a to come up with the least-squares line equation
    - __notice__ : the sign on b will always match the sign on r (negative or positive)
    - __also notice__ : strong correlation will give you high CDs
- we used the linear equation to calculate residuals
- we used __r__ to calculate the CD to decide if we wanted to use the linear equation for prediction
- we decided it was goo for prediction at 90%

- least-squares criterion and calculating the least-squares line
- reviewing issues with prediction using the least-squares line
- coefficient of determination

## Chapter 7.1 : normal distribution & empirical rule
- at the end of this lecture, the student should be able to :
    - state two properties of the normal curve
    - state two differences between Chebyshev Intervals and the Empirical Rule
    - explain how to apply the Empirical Rule to a normal distribution

## empirical rule
- remember chebyshev?
    - intervals have boundaries, or limits : lower limit and upper limit
- chebyshev vs empirical rule :
    - chebyshev's theorem :
        - applies to any distribution
        - say 'at least'
    - empirical rule :
        - applies only the normal distribution
        - say 'approximately'
- conclusion :
    - the empirical rule helps establish __intervals__ that apply to normally distributed data
    - these intervals have a certain percentage of the data points in them
    - these intervals depend on the __mean__ and __standard deviation__ of the data distribution

# Chapter 7.2 & 7.3 : Z-scores & Probabilities
- at the end of this lecture, the student should be able to :
    - explain how to convert an x to a z-score
    - show how to look up a z-score in a z-table
    - explain how to find the probability of an x falling between two values on a normal distribution
    - describe how to use the z table to look up a z corresponding to a percentage
    - describe how to use the formula to calculate x from a z-score
- what is z-score and what is a standard normal distribution :
    - o7 : standard deviation
    - remeber the empirical rule:
    - z is the standard normal distribution
    - z = (x-mu)/o7
    - every value on a normal distribution (every 'x') can be converted to a z-score
    - you must know the following to use formula :
        - the x - what you wnat to convert to z
        - the mu of the distribution
        - mu and o7(standard deviation) 
- tips and trick of what to do with z-scores :
    1. where is x : usually in the question
    2. what to do with x : calculate the z-score
    3. what do you do with a z : look it up in the z table
    4. what if the question asks for x : use the x formula
    5. what if a question give you a p : dig around in the table to find the p to map back to z, then use x formula

# Chapter 7.4 & 7.5 : Sampling distributions and the central limit theorem
- at the end of this lecture, the student should be able to :
    - state the statistical notation for parameters and statistics for two measures of variation
    - name one type of __inference__ and describe it
    - explain the difference between the __frequency distribution__ and __sampling distribution__
    - describe the __central limit theorem__ in either words or formulas
    - describe how to calculate __standard error__
- reminder :
    - a __statistic__ is a __numerical measure__ describing a __sample__
    - a __parameter__ is a __numerical measure__ describing a __population__

- Notion of statistics and parameters

| measure            | statistic | parameter     |
|--------------------|-----------|---------------|
| mean               | x-bar     | mu            |
| variance           | s**2      | sigma squared |
| standard deviation | s         | sigma         |
| propotion          | p-hat     | p             |

## types of inferences :
- inferences is something you do in statistics
1. estimation : we estimate the value of a population parameter using a sample
2. testing : we do a test to help us make a decision about a population parameter
3. regression : we make predicitons or forecasts about a statistics
- requres understanding sampling distributions and the central limit theorem

## frequency vs sampling distribution
- frequency distribution :
    1. make a histogram of a quantitative variable
    2. draw the shape and name the distribution
- sampling distribution :
    1. start with a population
    2. decide on an n
    3. take as many samples of n as possible from the population
    4. make an x-bar for each sample
    5. make a historgram of all the x-bars
- definition of a sampling distribution :
    - a sampling distribution is a probability distribution
        - of a __sample statistic__ based on
            - all possible __simple random samples__ of the __same size__ from the __same population__

## central limit theorem
- for any normal distribution :
    1. the sampling distribution (the distributions of x-bars from all possible samples) is also a normal distribution
    2. the mean of the x-bars is actually mu
    3. the standard deviation of the x-bars is actually o7/squareroot(n)
