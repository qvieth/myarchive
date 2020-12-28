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

## summary
### what is machine learning?
- the art and science of :
    - giving computers the ability to learn to make decisions from data
    - __without being explicitly programmed__
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
- __automate__ time-consuming or expensive manual tasks
    - example : Doctor's diagnosis
- __make predictions__ about the future
    - example : will a customer click on an ad or not
- need labeled data
    - historical data with labels 
    - experiments to get labeled data
    - crowd-sourcing labeled data

### supervised learning in python
- we will use scikit-learn
- integrates well with scipy/numpy

