# data science introduction

<!-- vim-markdown-toc GFM -->

* [introduction to data science](#introduction-to-data-science)
* [probability](#probability)
* [programming in data science](#programming-in-data-science)
* [data science process](#data-science-process)
    * [ask a question](#ask-a-question)
        * [variable relationships](#variable-relationships)
        * [scope](#scope)
        * [context](#context)
    * [determine the necessary data](#determine-the-necessary-data)
    * [getting data](#getting-data)
    * [cleaning data](#cleaning-data)
    * [explore the data](#explore-the-data)
        * [statistical calculations](#statistical-calculations)
        * [data visualiztions](#data-visualiztions)
    * [modeling the data (and analysis)](#modeling-the-data-and-analysis)
    * [communicating findings](#communicating-findings)
        * [visualizing](#visualizing)
        * [story telling](#story-telling)
    * [reproducibility and automation](#reproducibility-and-automation)

<!-- vim-markdown-toc -->

## introduction to data science
- __venn diagram__ for data science : [domain expertise](domain expertise) + mathmetics + computer science
- a fundamental part of data science is __statistics__
- statistics has been practiced for centuries but with the advent of __computing powers__ in the middle of the 20th century, statistics has taken on a new form
- statistics is the practice of applying mathematical calculations to sets of data to derive meaning
- there are 2 types of statistics : __descriptive statistics__ and __inferential statistics__ :
    - descriptive statistics : describe a dataset using mathematically calculated values, such as the mean and standard deviation
    - inferential statistics : the statistical calculations that enable us to draw conclusions about the larger population
- mean, standard deviation => distribution

## probability
- another field that informs the field of data science is __probability__
- in data science, probability calculations are used to build models
- __models__ are able to help us understand data that has yet to exist - either data we hadn't previously collected or that has yet to be created
- data scientists __create models__ to help calculate the probability of a certain action and then they use that probability to make __informed decisions__

## programming in data science
- programming is what sets data science apart from __similar fields__, like __data analytics__
- in data science, programming allows us to hand the processing power over to the computer
- in further lessons, you will learn to write code that __organizes__ and __analyzes__ data
- furthermore, within data science, programs will allow you to reproduce experiments by simply running the program again
- you will also learn how to program models that can make predictions based on data point
- these models are the basis of __machine learning__ - a field of computer science that allows computers to __make predictions based on data__
- __clustering__ is a subsection of data science that allows us to classify data
- __clustering__ is important in data science because with massive amount of data, clustering by hand can take an extremely long time

## data science process
- professionals who do data science are driven by a desire to ask questions
- to answer these questions, data scientists use a __process of experimentation and exploration__ to answers

> like other scientific fields, data science follows the __scientific method__

- but the data science process also includes steps particular to working with large, digital datasets
- the process generally goes as follows :
    - ask a question
    - determine the necessary data
    - get the data
    - clean and organize the data
    - explore the data
    - model the data
    - communicate your findings
- while we present these steps as a linear process, it's important to keep in mind that you'll often __repeat steps or do things out of order__

### ask a question
- data science is all about asking questions and understanding how data can provide us with answer
- coming up with a question is arguably the most important step since the question that we ask will guide the rest of our process
- from deciding which datasets to use to constructing visualizations
- while coming up with a question may seem relatively simple, coming up with a good question requires practice
#### variable relationships
- in data science, we want to know the effect that different things have on each other
- one way of framing a question is to think of the relationship between different variables:
    - like how does __x__ impact, affect __y__?
    - does __eating dinner late(x)__ impact __your ability to sleep early(y)__?
    - do __the most popular songs in the US(x)__ affect __what is the most popular song worldwide(y)__?

#### scope
- another thing to keep in mind while forming a question is __scope__
- a question should be specific enough that we know it is answerable
- but shouldn't be too specific to the point where no relevant data exist
- and we are unable to draw any real conclusions
- for example :
    - asking "do people learn on codecademy" is too abstract and doesn't tell us what data to collect
    - on other hand, asking the highly specific question "how many people with blonde hair and the astrological sign aquarius complete half a lesson in november" while answerable, will probably __not tell us anything meaningful__
    - the question "how many lessons do learners complete within the first week of sign-up" is both __answerable__ and can provide us with __insights__(meaningful)

#### context
- another thing to keep in mind is that a __good question requires context__
- part of doing data science is having __professional expertise__
- or a __significant amount of background knowledge in the area that you want to explore__
- __gaining context__ requires doing __research__, such as looking at any relevant data that you already have
- if you're working with a large database, like _redshift_, you can run _sql_ queries to find your data
- professionals often use third-party software such as looker and tableau to __run their queries__

```
what else might we keep in mind when coming up with a question?
- a few concepts to keep in mind when coming up with a good question which include : variable relationships, scope, and context
- other concepts : how useful it is, cost, whether the question has been answered already
```

### determine the necessary data
- after you have a question, you have to make an educated guess about what you think the answer might be
- this educated guess is known as __hypothesis__ and helps to determine the data you need to collect
- it's important to remember that the data you decide to collect can't just be the data that you think is going to answer your question
- we can't carefully select for what we know will prove the __hypthesis__ is correct
- actually, the data needs to disprove the hypothesis
- what do we mean by that :
    - in science, it's __actually impossible__ to __prove__ that __something is true__
    - rather, we try and show that we're really, really confident that it's not false
    - that's because the only way we can say we're 100 % positive our hypothesis is correct is to collect all the data for an entire population
    - and that's pretty much imposible

- __so how do we determine what data is necessary to collect :__ 
    - first, we need to determine what data could disprove our __hypothesis__
    - for example
    - if our __hypothesis__ is that sriracha is the most popular hot sauce in the entire world
    - we can't just survey a group of 100 people and ask if they refer sriracha over frank's red hot
    - we need to look at how sriracha consumption compares to the consumption of multiple other brands of hot sauce
    - next we need to figure out how much data to collect
    - while it's preferable to get information for an entire population
    - that process is often difficult or impractical
    - so instead we __collect a sample__ set of data
    - a smaller amount of data that are __representative__ of the entire population

- __how do we ensure that our sample is representative :__
    - we figure out out the necessary number of samples that have similar __descriptive statistics__ to the entire population
    - for example
    - say that we know the length of oyster in long island
    - our hypothesis is that they're about 3 inches
    - if we collect 5 oyster shells, they may only measure on average, 2 inches
    - however, if we collect 145 more, we'll find that the average is closer to 3 inches
- rule of thumb : 
    - the larger the sample size and the more diverse your dataset is, the more confident you'll be in your results
    - we don't want to go through the trouble of designing and running an experiment only to discover that we don't have enough information to make a good decision
    - __online sample size calculator__ : margin of error, confidence level, population size, likely sample propotion, sample size

### getting data
- once you've determined which data you need, it's time to collect it
- data collection can be simple as locating a file or as complicated as designing and running experiment
- here are couple of different ways to get data :
    - __active data collection__ : you're settting up specific conditions in which to get data, you're on the hunt, examples include running different experiments and surveys
    - __passive data collection__ : you're looking for data that already exists, you're foraging data, examples include locating datasets and web scraping
- there are couple of things to keep in mind when we collect data :
    - the size of dataset : if you're unsure about the size of your dataset, use a __sample calculation__
    - error and bias : having a larger sample size is one way to mitigate errors and bias

### cleaning data
- data is typically organized in columns and rows, like you'd see in a spreedsheet
- but __raw data__ can actually come in a variety of file types and formats, this especially true if you're getting your data from elsewhere, like public datasets
- we as human may understand the organizing logic of a dataset, but computer are very literal
- a missing value or unlabeled column can completely throw them off their game
- even worse your program could still run, but your outcomes would be incorrect
- an important part of data science is to __clean__ and __organize__ our datasets, sometimes referred to as __data wrangling__
- processing data set could mean a few different things : getting rid of invalid data or correctly labeling columns
- the python library __pandas__ is a great tool for __importing__ and __organizing__ datasets
- you can use pandas to convert a spreadsheet document, like a CSV into easily readable tables and charts known as __dataframes__
- we can also use __libraries like pandas__ to transform our datasets by adding columns and rows to an existing table or by merging multiple tables together

### explore the data
- now that our data is organized, we can begin looking for __insights__
- but just because our data is all cleaned up, we still can't learn alot by staring at tables
- in order to truly explore our data, we'll need to go a few steps further
- __exploring a dataset__ is a key step because it will help us __quickly understand the data__ we're working with 
- and allow us to determine if we need to make any changes before moving forward
- changes could include some additional dataset cleaning
- collecting more data
- or even modifying the initial question we're trying to answer
- remember : data science is __not necessarily a linear process__
- there are 2 strategies for exploring our data :
    - statistical calculations
    - data visualizations

#### statistical calculations
- when we first get a data set, we can use __descriptive statistics__ to get a sense of what it contains
- __descriptive statistics__ summarize a given dataset using __statistical calculation__
- such as the average (aka mean), median, and standard deviation
- we can imediately learn what are common values in our datasets and how spread out the dataset is (are most of the values the same, or they are wildly different?)
- we can use a python module known as __numpy__ to __calculate descriptive statistics values__
- __numpy__ (short for numerical python) supplies short commands to easily perform statistical calculations, like `np.mean()`, which calculates the mean of a dataset

#### data visualiztions
- another way we can quickly get a sense of our data is by __visualizing__ it
- the practice of __data visualization__ enables us to see paterns, relationships, and outliers, and how they relate to the entire dataset
- visualizations are particularly useful when working with large amounts of data
- python __data visualization libraries__ like __matplotlib__ and __seaborn__ can display distributions and statistical summaries for easy comparison
- the __javascript__ library __D3__ enables the creation of __interactive data visualizations__, which are useful for modeling different scenarios

### modeling the data (and analysis)
- data in hand, we can begin to dig in and __analyze__ what we have
- to __analyze our data__, we'll want to create a __model__
- __models__ are abstractions of reality, informed by real data
- that allows us to __understand situations__ and __make guesses__ about how things might change given __different variables__
- a model give us the __relationship__ between two or more variables
- for example :
    - you could build a model that relates the number of grade school children in a neighborhood with sales of toys
    - or a model that connects the amount of trucks that travel certain roads with the amount of a city's budget assigned to road maintenance

- models allow us to __analyze__ our data because once we begin to understand the relationships between different variables
- we can make __inferences__ about certain circumstances
- why is it that the sales of toys increases as the number of grade school children grows
- well, maybe it's because parents are buying their children more toys
- models are also useful for __informing__ decisions
- since they can be used to predict unknowns
- once we understand a relationship between variables
- we can introduce unknown variables and calculate different possibilities
- if the number children in the neighborhood increases
- what do we predict will happen to the sales of toys?

- as we collect more data, our model can change
- allowing us to draw new insights and get a better idea of what might happen in different circumstances
- our model can tell us whether or not an observed variance is within reason, is due to an error, or possibly carries significance
- how would our understanding of our model change if in 2016 we discovered that the number of toys did not increase, but instead decreased?
- we'd want to look for an explanation as to why this year did not fit the trend

- model can be expressed as __mathematical equations__, such as the equation of a line
- you can use __data visualization__ libraries like matplotlib and seaborn to visualize relationships
- if you pursue machine learning
- you can use the python package __scikit-learn__ to build __predictive models__, such as __linear regression__

### communicating findings
- after you've done your analyses, built your models and gotten some results, it's time to communicate your findings
- 2 important parts of communicating data are __visualizing__ and __story telling__

#### visualizing
- as we saw earlier, visualizations are helpful for exploring and understanding our data
- however, they are also very useful for communicating results
- if you're giving a presentation at a conference for data scientists who also work at dating companies, then you can reuse your graph
- but if you're writing an article for medium, you'll probably want to simplify your visualizations and style them so they're easy to read and highly engaging

#### story telling
- it's also  important to remmeber that visualizations can't always stand on their own
- they need to tell a story
- story telling is an important part of data science because it gives the meaning to the data
- in fact, data story telling is an important practices in its own right
- contextualizing your findings and giving them a narrative draws people into your work 
- and enables you to convince them as to why these results are important and why they should make a certain decision

### reproducibility and automation
- you've followed the data science process and completed a study
- but there's one last step to cover
- after you've finished your experiments and communicated your findings
- it's also __important__ to remember that the scientific method requires that your work can be __reproduced__
- in the field of data science, we call this quality __reproducibility__
- __reproducibility__ is important because it  enables you to reuse and modify experiments
- but it is also how the scientific community can confirm your analysis is valid
- if your study produces results that no one can reproduce, it is likely that your results are invalid and the product of __bias and error__
- another concept tied to reproducibility is the idea of __automation__
- if you're creating reports, it's most likely that you'll be processing the same data at regular intervals
- rather than writing a new program each time, you can write a program that automates these process
- freeing up your time to do even more data science
- __automation__ maybe as simple as writing a python program you can re-use all the way up to __building machine learning models__
