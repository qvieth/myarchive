# data science
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
