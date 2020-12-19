# classification - supervised learning

<!-- vim-markdown-toc GFM -->

* [summary](#summary)
    * [what is machine learning?](#what-is-machine-learning)
    * [unsupervised learning](#unsupervised-learning)
    * [reinforcement learning](#reinforcement-learning)
    * [supervised learning](#supervised-learning)
    * [naming conventions](#naming-conventions)
    * [goals of supervised learning](#goals-of-supervised-learning)
    * [supervised learning in python](#supervised-learning-in-python)

<!-- vim-markdown-toc -->
1. What is machine learning?
    - But what is machine learning?
    - Machine learning is the science and art of giving computers the ability to __learn to make decisions__ **from data** without being explicitly programmed
    - For example, your computer can learn to predict whether an email is spam or not spam given its content and sender
    - Another example: your computer can learn to cluster, say, Wikipedia entries, into different categories based on the words they contain
    - It could then assign any new Wikipedia article to one of the existing clusters
    - Notice that, in the first example, we are trying to predict a particular class label, that is, spam or not spam
    - In the second example, there is no such label
    - When there are labels present, we call it supervised learning
    - When there are no labels present, we call it unsupervised learning

2. Unsupervised learning
    - Unsupervised learning, in essence, is the machine learning task of uncovering hidden patterns and structures from unlabeled data
    - For example, a business may wish to group its customers into distinct categories
        - based on their purchasing behavior without knowing in advance what these categories maybe
    - This is known as __clustering__, one branch of unsupervised learning

3. Reinforcement learning
    - There is also reinforcement learning, in which machines or software agents interact with an environment
    - Reinforcement agents are able to automatically figure out how to optimize their behavior given a system of rewards and punishments
    - Reinforcement learning draws inspiration from behavioral psychology and has applications in many fields, such as, economics, genetics, as well as game playing
    - In 2016, reinforcement learning was used to train Google DeepMind's AlphaGo, which was the first computer program to beat the world champion in Go

4. Supervised learning
    - But let's come back to supervised learning, which will be the focus of this course
    - In supervised learning, we have several data points or samples, described using predictor variables or features and a target variable
    - Our data is commonly represented in a table structure such as the one you see here, in which there is a row for each data point and a column for each feature
    - Here, we see the iris dataset: each row represents measurements of a different flower and each column is a particular kind of measurement
        - like the width and length of a certain part of the flower
    - The aim of supervised learning is to build a model that is able to predict the target variable
        - here the particular species of a flower
        - given the predictor variables, here the physical measurements
    - If the target variable consists of categories, like 'click' or 'no click', 'spam' or 'not spam', or different species of flowers
        - we call the learning task classification
    - Alternatively, if the target is a continuously varying variable, for example, the price of a house, it is a regression task
    - In this chapter, we will focus on classification
    - In the following, on regression

5. Naming conventions
    - A note on naming conventions: out in the wild
        - you will find that what we call a __feature__
            - others may call a predictor variable or independent variable
        - and what we call the __target variable__
            - others may call dependent variable or response variable

6. Supervised learning
    - The goal of supervised learning is frequently to either automate a time-consuming or expensive manual task
        - such as a doctor's diagnosis, or to make predictions about the future, say whether a customer will click on an add or not
    - For supervised learning, you need labeled data and there are many ways to get it:
        - you can get historical data, which already has labels that you are interested in
        - you can perform experiments to get labeled data, such as A/B-testing to see how many clicks you get
        - or you can also crowdsourced labeling data which, like reCAPTCHA does for text recognition
    - In any case, the goal is to learn from data for which the right output is known, so that we can make predictions on new data for which we don't know the output

7. Supervised learning in Python
    - There are many ways to perform supervised learning in Python
    - In this course, we will use scikit-learn, or sklearn, one of the most popular and user-friendly machine learning libraries for Python
    - It also integrates very well with the SciPy stack, including libraries such as NumPy
    - There are a number of other ML libraries out there, such as TensorFlow and keras, which are well worth checking out once you got the basics down

## summary
### what is machine learning?
- the art and science of :
    - giving computers the ability to learn to make decisions from data
    - without being explicitly programmed
- example :
    - learning to predict whether an email is spam or not
    - clustering wikipedia entries into different categories
- __supervised__ learning : uses __labeled__ data
- __unsupervised__ learning : uses __unlabeled__ data

### unsupervised learning
- uncovering hidden patterns from unlabeled data
- example :
    - grouping customers into distinct categories (clustering)

### reinforcement learning
- software agents interact with an environment :
    - learn how to optimize their behavior
    - given a system of rewards and punishments
    - draws inspiration from behavioral psychology
- applications :
    - economics
    - genetics
    - game playing
- alphago: first computer program beat world champion in go

### supervised learning
- predictor variables/features and a target variable
- aim : predict the __target variable__, given the __predictor variables__
    - classification : target variable consists of categories
    - regression : target variable is continuous

### naming conventions
- feature = predictor variables = independent variables
- target variables = dependent variable = response variable

### goals of supervised learning
- automate time-consuming or expensive manual tasks
    - example : Doctor's diagnosis
- make predictions about the future
- example : will a customer click on an ad or not
- need labeled data
    - historical data with labels 
    - experiments to get labeled data
    - crowd-sourcing labeled data

### supervised learning in python
- we will use scikit-learn
- integrates well with scipy/numpy

