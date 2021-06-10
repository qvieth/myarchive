# crash course statistics

## Contents

-   [crash course statistics](#crash course statistics)
-   [what is statistics](#what is statistics)
-   [Mathematical thinking - crash course](#Mathematical thinking - crash course)
-   [Mean, median and mode : measure of central tendency](#Mean, median and mode : measure of central tendency)
-   [Measures of spread](#Measures of spread)
-   [Data visualization part1&2](#Data visualization part1&2)
    -   [Part 1](#Data visualization part1&2#Part 1)
    -   [Part 2](#Data visualization part1&2#Part 2)
-   [The shape of data : distribution](#The shape of data : distribution)
-   [correlation doesnt equal causation](#correlation doesnt equal causation)
-   [controlled experiments](#controlled experiments)
-   [sampling method and bias with survey](#sampling method and bias with survey)
-   [science journalism](#science journalism)
-   [henrietta lacks tuskegee experiment and ethical data collection](#henrietta lacks tuskegee experiment and ethical data collection)
-   [probability crash course part 1 and 2](#probability crash course part 1 and 2)
    -   [part 1](#probability crash course part 1 and 2#part 1)
    -   [part 2](#probability crash course part 1 and 2#part 2)
-   [binomial distribution](#binomial distribution)

# what is statistics

-   there're 2 related but seperate meanings of the word **statistics**
    -   **field of statistics** : the study and practice of collecting and analyzing data
    -   **statistics** : facts about, or summaries of data
-   test the claim
-   statistics are **tools** for us to use
-   but you're not measuring why people eat fast food everyday
-   you're measuring what we call a "proxy", something that is related to what we want to measure, but isn't **exactly** what we want to measure
-   the tools we use to answer these questions are statistics plural, and there're 2 main types :

    1. descriptive
        - **descriptive statistics** usually include things like **where the middle of the data is**
            - what statisticians call **measures of central tendency**
            - and measures of **how spread out the data are**
    2. inferential
        - inferential statistics allow us to make inferences
        - inferential statistics allow us to make conclusions that extend beyond the data we have in hand
        - we ask inferential statistics to do all sort of **much more complicated work for us**
        - inferential statistics lets us **test an idea or hypothesis**

-   statistics help us filter the loads of data that come at us everyday
-   **descriptive statistics** make the data we get more digestible, even though we lose information about individual data points
-   **inferential** can help us make decisions when there's uncertainty
-   but statistics can do all the work
    -   they help us to reason, not to reason for us
    -   they can get us through uncertainty, but they don't get rid of that uncertainty

# Mathematical thinking - crash course

-   **Mathematical thinking** is about seeing the world in a different way
-   Which means sometimes seeing beyond our intuition or gut feeling
-   a quick note about scientific notation :
    -   scientific notation can be really helpful for calculating with big numbers,
    -   but not necessary helpful for understanding them
    -   without context, exponents can be non-intuitive if that's a word in their own way
-   there're about 7.6 billion people on earth
-   understanding the sheer number of people out there in the world can help us make sense of the commonness of coincidences or improbable events
-   some statisticains call it the "law of truly large numbers"
-   the idea here is that with a large enough group, or sample, unlikely things are completely likely to happen
-   it's worth taking the time to think through small numbers , cause they can help you figure out what's actually worth worrying about
-   **thinking mathematically** isn't just about understanding numbers better
    -   it's about asking important questions about the world around us
    -   and letting numbers illuminate those question

# Mean, median and mode : measure of central tendency

-   mean : average
-   mean is good at measuring things that are relatively '**normally**' distributed
-   normal : a **distribution** of data that has roughly the same amount of data on either side of the middle, and has its most common values around the middle of the data
-   **distribution** : show us how often each value occurs in our data set, which is know as frequency
-   outliers :
-   median : the middle number if we lined up our data from smallest to largest
-   average is distorted by outliers
-   the word **mode** comes from the latin word modus, which means '**manner, fashion, or style**' and give us the french expression means **fashionable, popular** a la mode
-   mode : the value that appears most in our dataset, the **peak** of the diagram
-   bimodal data is an example of 'multimodal data' which has many values that are **similarly common**
-   usually multimodal data results from two or more underlying groups all being measured together
-   the fact that the **median** and the **mean** are **the same** tell us that the **distribution is symetric**
    -   that there's equal amount of data on **either side of the median**, and equal amounts on **either side of the mean**
-   statisticians say the normal distribution has zero skew, since the mean and median are the same
-   when the median and mean are different, a distribution is skewed, which is a way of saying that there are some unusually extreme values on one side of our distribution
-   either large or small in our dataset
-   an important part of statistics is understanding **which question you are trying to answer** and **whether or not the information you have is answering those question**

# Measures of spread

-   statistical measures of spread or dispersion tell us how data is spread around the middle
-   that lets us know how well the mean or median represents the data
-   interquartile range (IQR) : doesn't consider extreme value, the iqr looks at the spread of the middle 50% of your data
-   variance : which can give us a better sense of how spread out the whole dataset is
-   N and (N-1) for sample variance
-   standard deviation : the average amount we expect a point to differ (or deviate) from the mean

# Data visualization part1&2

## Part 1

-   Earlier in the series, i talked about how it can be hard to wrap your head around numbers
    -   especially when they get really big or really small
-   **frequency table** : best way to display **categorical data**
    -   **bar charts** :
        -   uses the frequencies that we saw in our frequency table
            -   to create bars that have a height equal to the frequency
            -   that way, we can compare the height of bar instead of looking at raw number
        -   display a lot of information in a very simple graph
        -   they can also display the frequencies of multiple variables
        -   when there're more then 1 variable : use stacked or double bar
    -   **pie charts** :
        -   another way to display **categorical data**
        -   are not good at displaying more than 1 variable
    -   **pictograph** :
        -   another way to display categorical data
        -   represent frequency with pictures
-   **bin frequency table** : distored by **re-binning**
    -   **binning** : a process takes a quantitative variable and bins it into categories that are either pre-existing or made up
-   **histograms**, like bar charts
    -   the height of the bars tell us how frequently data in a certain range occur
    -   a historgram also give us information about **how the data is distributed**
    -   histogram give us more information about the data than the **frequency table** does,
    -   but they're still obscuring what the specific data values are

## Part 2

-   **dotplot** : historgram but replace with dot
-   **stem and leaf plot** : cousin of dotplot : use value from raw data instead of dots
-   cumulative frequency plots
-   Two-way tables organize data based on **two categorical variables**

# The shape of data : distribution

-   normal distribution curve :
    -   the standard deviation is the average distance between any point and the mean
-   When collecting data to make observations about the world it usually just isn't possible to collect ALL THE DATA
-   So instead of asking every single person about student loan debt
    -   for instance we take a sample of the population
    -   and then use the shape of our samples to make inferences about the true underlying distribution our data
-   It turns out we can learn a lot about how something occurs, even if we don't know the underlying process that causes it
-   Today, we’ll also introduce the normal (or bell) curve
    -   and talk about how we can learn some really useful things from a sample's shape
        -   like if an exam was particularly difficult
        -   how often old faithful erupts
        -   or if there are two types of runners that participate in marathons!

# correlation doesnt equal causation

-   Today we’re going to talk about data relationships and what we can learn from them
-   We’ll focus on correlation
    -   which is a measure of how two variables move together
    -   and we’ll also introduce some useful statistical terms you’ve probably heard of
    -   like regression coefficient, correlation coefficient (r), and r^2
-   But first, we’ll need to introduce a useful way to represent **bivariate continuous data** - the **scatter plot**
-   The **scatter plot** has been called “the most useful invention in the history of statistical graphics”
    -   but that doesn’t necessarily mean it can tell us everything
-   Just because two data sets move together doesn’t necessarily mean one CAUSES the other
-   This gives us one of the most important tenets of statistics: correlation does not imply causation

-   **scatterplot** best for analyzing relationship between variables
-   coefficient r
-   examples the mayor uses are perfect examples of things that can go wrong when interpreting correlations
-   when A correlated with another B, there's a few possible reason :
    -   A causes B
    -   B causes A
    -   Variables C causes both A and B
    -   No relationship at all

# controlled experiments

-   We may be living IN a simulation (according to Elon Musk and many others)
    -   but that doesn't mean we don't need to perform simulations ourselves
-   Today, we're going to talk about good experimental design and how we can create controlled experiments to minimize bias when collecting data
-   We'll also talk about single and double blind studies
    -   randomized block design, and how placebos work

# sampling method and bias with survey

-   rewatch

# science journalism

-   rewatch

# henrietta lacks tuskegee experiment and ethical data collection

-   rewatch

# probability crash course part 1 and 2

## part 1

-   Today we’re going to begin our discussion of probability
-   We’ll talk about how the addition (OR) rule
    -   the multiplication (AND) rule
-   and conditional probabilities help us figure out the likelihood of sequences of events happening

    -   from optimizing your chances of having a great night out with friends to seeing Cole Sprouse at IHop!

-   statisticians talk about 2 types of probability :
    1. empirical
        - something we observe in actual data
    2. theoretical

## part 2

-   Today we're going to introduce bayesian statistics
    -   and discuss how this new approach to statistics has revolutionized the field
    -   from artificial intelligence and clinical trials to how your computer filters spam!
    -   We'll also discuss the Law of Large Numbers and how we can use simulations to help us better understand the "rules" of our data
-   even if we don't know the equations that define those rules
-   bayes'theorem :
    -   `P(B|A)=P(A|B)P(B)/P(A)`
-   conditional probability :

    -   `P(B|A)=P(AandB)/P(A)`

-   **bayesian statistic** is all about **updating** your beliefs based on **new(more) information**
-   frequentist statistic
-   law of large number

# binomial distribution

-   Today we're going to discuss the **Binomial Distribution**
    -   and a special case of this distribution known as a **Bernoulli Distribution**
-   The **formulas that define these distributions** provide us with
    -   shortcuts for calculating the probabilities
    -   of all kinds of events that happen in everyday life
-   They can can also be used to help us look at how probabilities are connected!
    -   For instance, knowing the chance of getting a flat tire today is useful
        -   but knowing the likelihood of getting one this year, or in the next five years, may be more useful
-   And heads up, this episode is going to have a lot more equations than normal, but to sweeten the deal, we added zombies!
