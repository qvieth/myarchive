# classification
- In this chapter you will be introduced to __classification problems__
    - and learn how to __solve them using supervised learning techniques__
- And you’ll apply what you learn to a political dataset
    - where you classify the party affiliation
    - of United States congressmen based on their voting records

## Contents

- [classification](#classification)
- [summary](#summary)
    - [what is machine learning?](#summary#what is machine learning?)
    - [unsupervised learning](#summary#unsupervised learning)
    - [reinforcement learning](#summary#reinforcement learning)
    - [supervised learning](#summary#supervised learning)
    - [naming conventions](#summary#naming conventions)
    - [goals of supervised learning](#summary#goals of supervised learning)
    - [supervised learning in python](#summary#supervised learning in python)
- [which of these is a classification problem ?](#which of these is a classification problem ?)
- [exploratory data analysis - supervised learning with scikit-learn](#exploratory data analysis - supervised learning with scikit-learn)
- [Exploratory Data Analysis?](#Exploratory Data Analysis?)
        - [Techniques](#Exploratory Data Analysis?#Techniques)
- [numerical EDA](#numerical EDA)
- [Visual EDA](#Visual EDA)
- [the classification challenge](#the classification challenge)
    - [k-Nearest Neighbors](#the classification challenge#k-Nearest Neighbors)
        - [Using scikit-learn to fit a classifier](#the classification challenge#k-Nearest Neighbors#Using scikit-learn to fit a classifier)
        - [Predicting on unlabeled data](#the classification challenge#k-Nearest Neighbors#Predicting on unlabeled data)
- [k-Nearest Neighbors : Fit](#k-Nearest Neighbors : Fit)
- [k Nearest Neighbors: Predict](#k Nearest Neighbors: Predict)
    - [Instructions](#k Nearest Neighbors: Predict#Instructions)
    - [Hint](#k Nearest Neighbors: Predict#Hint)
- [measuring model performance](#measuring model performance)
    - [Measuring model performance](#measuring model performance#Measuring model performance)
    - [Train/test split](#measuring model performance#Train/test split)
    - [Model complexity and over/underfitting](#measuring model performance#Model complexity and over/underfitting)
- [the digits regconition datasets](#the digits regconition datasets)

# summary
## what is machine learning?
- the art and science of :
    - giving computers the ability to learn to make decisions from data
    - __without being explicitly programmed__
- example :
    - learning to predict whether an email is spam or not
    - clustering wikipedia entries into different categories
- __supervised__ learning : uses __labeled__ data
- __unsupervised__ learning : uses __unlabeled__ data

## unsupervised learning
- uncovering hidden patterns from unlabeled data
- example :
    - grouping customers into distinct categories (clustering)

## reinforcement learning
- software agents interact with an environment :
    - learn how to optimize their behavior
    - given a system of rewards and punishments
    - draws inspiration from behavioral psychology
- applications :
    - economics
    - genetics
    - game playing
- alphago: first computer program beat world champion in go

## supervised learning
- predictor variables/features and a target variable
- aim : predict the __target variable__, given the __predictor variables__
    - classification : target variable consists of categories
    - regression : target variable is continuous

## naming conventions
- feature = predictor variables = independent variables
- target variables = dependent variable = response variable

## goals of supervised learning
- __automate__ time-consuming or expensive manual tasks
    - example : Doctor's diagnosis
- __make predictions__ about the future
    - example : will a customer click on an ad or not
- need labeled data
    - historical data with labels 
    - experiments to get labeled data
    - crowd-sourcing labeled data

## supervised learning in python
- we will use scikit-learn
- integrates well with scipy/numpy


# which of these is a classification problem ?
- Once you decide to __leverage__ supervised machine learning to __solve a new problem__
    - you need to identify whether your problem is better suited to
        - classification
        - or regression

- This exercise will help you develop your intuition for distinguishing between the two

- Provided below are 4 example applications of machine learning
- Which of them is a supervised classification problem?
    - [x] Using labeled financial data to predict whether the value of a stock will go up or go down next week
    - [ ] Using labeled housing price data to predict the price of a new house based on various features
    - [ ] Using unlabeled data to cluster the students of an online education company into different categories based on their learning styles
    - [ ] Using labeled financial data to predict what the value of a stock will be next week

- In this example, there are two __discrete__, __qualitative__ outcomes: the stock market going up, and the stock market going down
    - This can be represented using a __binary variable__, and is an application perfectly suited for classification

# exploratory data analysis - supervised learning with scikit-learn

```python
import matlotlib.pyplot as plt
_ = plt.hist
_ = plt.xlabel('x')
_ = plt.ylabel('y')
```

- always label your axis
- The "square root rule" is a commonly-used rule of thumb for choosing number of bins :
    - choose the __number of bins__ to be the __square root__ of the __number of samples__


# Exploratory Data Analysis?
- Exploratory Data Analysis involves two fundamental steps :
    - Data Analysis (Data Pre processing, Cleaning and Manipulation)
    - Data Visualisation (Visualise relationships in data using different types of plots)

- Many people associate data science with fields like machine learning and artificial intelligence
- but EDA often takes up a larger percentage a data scientist’s day-to-day work! This is because:
    - Before fitting any sort of machine learning __model__
        - it is important to inspect a dataset and get to know it!
        - Often the best way to improve a __model__ is to spend more time thinking about the data itself
        - EDA can help you make decisions about what data to include, exclude, or transform
    - Sometimes a data scientist does not plan to fit a predictive model to their data at all
        - Instead, their goal may be to inspect and analyze existing data to answer questions like:
            - What proportion of visitors to a website made a purchase?
            - Or, how has the purchase rate changed over the last 6 months?
> EDA generally happens before __model fitting__!

### Techniques 
- The particular __graphical techniques__ employed in EDA are often quite simple, consisting of various techniques of:
    - Plotting the raw data such as :
        - data traces
        - histograms
        - bihistograms
        - probability plots
        - lag plots
        - block plots
        - and Youden plots
    - Plotting simple statistics such as :
        - mean plots
        - standard deviation plots
        - box plots
        - and main effects plots of the raw data
    - __Positioning__ such plots so as to maximize our natural pattern-recognition abilities
        - such as using multiple plots per page


# numerical EDA
- pandas'
    - `.read_csv()`
    - `.head()`
    - `.info()`
    - `.describe()`
    - `.corr()`

- distinguish __features__ and __target variable__

 
# Visual EDA
> In the video, Hugo used the `scatter_matrix()` for visual EDA

- However, you may have noticed in the previous exercise that __all the features__ in this dataset are __binary__ : either 0 or 1
- So a different type of plot would be more useful here, such as Seaborn's `countplot`

```python
plt.figure()
sns.countplot(x='education', hue='party', data=df, palette='RdBu')
plt.xticks([0,1], ['No', 'Yes'])
plt.show()
```

- In `sns.countplot()`, we specify
    - the x-axis data to be `'education'`
    - and hue to be `'party'`
    - Recall that `'party'` is also our __target variable__

- So the resulting plot shows the difference in voting behavior __between the two parties__ for the `'education'` bill
    - with each party colored differently
- We manually specified the color to be `'RdBu'`
    - Republican : red
    - Democratic : blue

- It seems like Democrats voted resoundingly against this bill, compared to Republicans
- __This is the kind of information that our machine learning model will seek to learn__
    - when we try to predict party affiliation solely based on voting behavior

- In the IPython Shell, explore the voting behavior further by generating __countplots__ for the `'satellite'` and `'missile'` bills
    - and answer the following question
        - Of these two bills
        - for which ones do Democrats vote resoundingly in favor of compared to Republicans?
        - Be sure to begin your plotting statements
            - for each figure with `plt.figure()` so that a new figure will be set up
- Otherwise, your plots will be overlayed onto the same figure

 
# the classification challenge  

<!-- vim-markdown-toc GFM -->

    * [k-Nearest Neighbors](#k-nearest-neighbors)
        * [Using scikit-learn to fit a classifier](#using-scikit-learn-to-fit-a-classifier)
        * [Predicting on unlabeled data](#predicting-on-unlabeled-data)
* [k-Nearest Neighbors : Fit](#k-nearest-neighbors--fit)
* [k Nearest Neighbors: Predict](#k-nearest-neighbors-predict)
    * [Instructions](#instructions)
    * [Hint](#hint)
* [measuring model performance](#measuring-model-performance)
    * [Measuring model performance](#measuring-model-performance-1)
    * [Train/test split](#traintest-split)
    * [Model complexity and over/underfitting](#model-complexity-and-overunderfitting)
* [the digits regconition datasets](#the-digits-regconition-datasets)

<!-- vim-markdown-toc -->

- We have a set of __labeled data__
- and we want to build a classifier that __takes unlabeled data__ as input and __outputs a label__
- We first need choose a type of classifier and it needs to learn from the already labeled data
- For this reason, we call the __already labeled__ data the __training data__

- So let's build our first classifier!

## k-Nearest Neighbors
- We'll choose a simple algorithm called K-nearest neighbors
- All machine learning models implemented as __Python classes__, serve 2 purposes :
    - they implement the algorithms for __learning a model__ and predicting
    - while also store the information learned from the data
* Training a model on the data is also called ‘fitting’ a model to the data
    - `.fit()` method
- To predict the labels of new data
    - `.predict()` method

### Using scikit-learn to fit a classifier
- Now we're going to fit our very first classifier using scikit-learn!
    - we first `from sklearn.neighbors import KNeighborsClassifier`
- We then __instantiate__ our knn __object__ from KNeighborsClassifier __class__
    - set the number of neighbors equal to 6, and assign it to the variable knn
- Then we can fit this classifier to our training set (the labeled data) by applying the method `.fit()` to the classifier and pass it two arguments:
    - the __features__ as a NumPy array
    - and the __labels__, or target, as a NumPy array

```python
from sklearn.neighbors import KNeighborsClassifier
knn = KNeighborsClassifier(n_neighbors=6)
knn.fit(iris['data'], iris['target'])
```
- The scikit-learn API requires
    - firstly that you have the data as a NumPy array or pandas DataFrame
    - the features take on __continuous values__, such as the price of a house, as opposed to categories, such as 'male' or 'female'
    - there are no missing values in the data
- Later in the course, you'll see how to deal with categorical features and missing data
- In particular, the scikit-learn API requires that
    - the features are in an array where each column is a feature
    - and each row a different observation or data point
- Looking at the shape of iris data, we see that there are 150 observations of four features

```python
iris['data'].shape
```

- Similarly, the target needs to be a single column with the same number of observations as the feature data

```python
iris['target'].shape
```

- We see in this case there are indeed also 150 labels
- Also check out what is returned when we fit the classifier: it returns the classifier itself and modifies it to fit it to the data
- Now that we have fit our classifier, lets use it to predict on some unlabeled data!

### Predicting on unlabeled data
- Here we have set of observations, X new
- We use the predict method on the classifier and pass it the data

```python
X_new = np.array([[5.6, 2.8, 3.9, 1.1],
        [5.7, 2.6, 3.8, 1.3],
        [4.7, 3.2, 1.3, 0.2]])
prediction = knn.predict(X_new)
```

- Once again, the API requires that we pass the data as a NumPy array with features in columns and observations in rows
    - checking the shape of X new, we see that it has three rows and four columns, that is, three observations and four features

```python
X_new.shape
```

- Then we would expect calling knn dot predict of X new to return a three-by-one array with a prediction for each observation or row in X new
    - And indeed it does! It predicts one, which corresponds to 'versicolor' for the first two observations and 0, which corresponds to 'setosa' for the third

```python
print('Prediction: {}’.format(prediction))
```

# k-Nearest Neighbors : Fit
```python
# Import KNeighborsClassifier from sklearn.neighbors
from sklearn.neighbors import KNeighborsClassifier

# Create arrays for the features and the response variable
y = df['party'].values
X = df.drop('party', axis=1).values

# Create a k-NN classifier with 6 neighbors
knn = KNeighborsClassifier(n_neighbors=6)

# Fit the classifier to the data
knn.fit(X,y)
```

- Having explored the Congressional voting records dataset, it is time now to build your first classifier
- In this exercise, you will fit a k-Nearest Neighbors classifier to the voting dataset, which has once again been pre-loaded for you into a DataFrame df

- In the video, Hugo discussed the importance of ensuring your data adheres to the format required by the scikit-learn API
- The features need to be in an array
    - where each column is a feature
    - and each row a different observation or data point 
        - in this case, a Congressman's voting record
- The target needs to be a single column with the same number of observations as the feature data
- We have done this for you in this exercise
- Notice we named the feature array X and response variable y: This is in accordance with the common scikit-learn practice

- Your job is to create an instance of a k-NN classifier with 6 neighbors (by specifying the n_neighbors parameter) and then fit it to the data
- The data has been pre-loaded into a DataFrame called df

 
# k Nearest Neighbors: Predict
- Having fit a k-NN classifier, you can now use it to predict the label of a new data point
- However, there is no unlabeled data available since all of it was used to fit the model!
- You can still use the .predict() method on the X that was used to fit the model
    - but it is not a good indicator of the model's ability to generalize to new, unseen data

- In the next video, Hugo will discuss a solution to this problem
- For now, a random unlabeled data point has been generated and is available to you as `X_new`
- You will use your classifier to predict the label for this new data point, as well as on the training data `X` that the model has already seen
- Using `.predict()` on `X_new` will generate 1 prediction, while using it on `X` will generate 435 predictions: 1 for each sample

- The DataFrame has been pre-loaded as `df`
- This time, you will create the feature array `X` and target variable array `y` yourself

## Instructions
- Create arrays for the features and the target variable from `df`
- As a reminder, the target variable is `'party'`
- Instantiate a `KNeighborsClassifier` with `6` neighbors
- Fit the classifier to the data
- Predict the labels of the training data, `X`
- Predict the label of the new data point `X_new`

```python
# Import KNeighborsClassifier from sklearn.neighbors
from sklearn.neighbors import KNeighborsClassifier 

# Create arrays for the features and the response variable
y = ____
X = ____

# Create a k-NN classifier with 6 neighbors: knn
knn = ____

# Fit the classifier to the data
____

# Predict the labels for the training data X
y_pred = ____

# Predict and print the label for the new data point X_new
new_prediction = ____
print("Prediction: {}".format(new_prediction))
```
## Hint
* To create the __target variable y__, select the `'party'` column of `df` and access its `.values` attribute
* To create the __feature array X__, use the `.drop()` method on `df` with `'party'` and `axis=1` as arguments
- Then access its `.values` attribute
- To instantiate the classifier, use `KNeighborsClassifier` and specify the number of neighbors using the `n_neighbors` parameter
- Use the `.fit()` method with `X` and `y` as arguments to fit the classifier to the data
- Use the `.predict()` method on `X` to predict the labels of the training data
- Use the `.predict()` method on `X_new` to predict the label of the new data point

```python
# Import KNeighborsClassifier from sklearn.neighbors
from sklearn.neighbors import KNeighborsClassifier 

# Create arrays for the features and the response variable
y = df['party'].values
X = df.drop('party', axis=1).values

# Create a k-NN classifier with 6 neighbors: knn
knn = KNeighborsClassifier(n_neighbors=6)

# Fit the classifier to the data
knn.fit(X, y)

# Predict the labels for the training data X: y_pred
y_pred = knn.predict(X)

# Predict and print the label for the new data point X_new
new_prediction = knn.predict(X_new)
print("Prediction: {}".format(new_prediction)) 
```

# measuring model performance 

<!-- vim-markdown-toc GFM -->

* [Measuring model performance](#measuring-model-performance)
* [Train/test split](#traintest-split)
* [Model complexity and over/underfitting](#model-complexity-and-overunderfitting)

<!-- vim-markdown-toc -->

## Measuring model performance
- Now that we know how to fit a classifier
    - and use it to predict the labels of previously unseen data
    - we need to figure out how to __measure its performance__
- That is, we need a metric
- In classification problems, __accuracy__ is a commonly-used metric
```
accuracy = number of correct predictions / total number of data points
```
- This begs the question though: which data do we use to compute __accuracy__?
- What we are really interested in is __how well__ our model will perform on new(unseen) data

- Well, you could compute the accuracy on the data you used to fit the classifier
- However, as this data was used to train it, the classifier's performance will not be indicative of how well it can generalize to unseen data

- For this reason, it is common practice to split your data into two sets
    1. __training set__
    2. __test set__

1. You train or `.fit()` the classifier on the __training set__
2. Then you `.predict()` on the labeled __test set__ and compare these predictions with the known labels
3. You then compute the accuracy of your predictions

## Train/test split
- To do this, we first `from sklearn.model_selection import train_test_split `
- We then use the `train_test_split()` function to randomly split our data
    - The first argument will be the __feature__ data
    - the second the __targets__ or labels
    - The test size keyword argument specifies what proportion of the original data is used for the test set
    - Lastly, the random state kwarg sets a seed for the random number generator that splits the data into train and test
    - Setting the seed with the same argument later will allow you to reproduce the exact split and your downstream results

- train test split returns four arrays:
    1. the training data
    2. the test data
    3. the training labels
    4. and the test labels
    - We unpack these into four variables: `X train, X test, y train, y test`, respectively

- By default, train test split splits the data into 75% training data and 25% test data, which is a good rule of thumb
    - We specify the size of the test size using the keyword argument `test_size`, which we do here to set it to 30%
- It is also best practice to perform your split so that the split reflects the the labels on your data
- That is, you want the labels to be distributed in train and test sets as they are in the original dataset
- To achieve this, we use the keyword argument `stratify=y`, where `y` the list or array containing the labels

- We then __instantiate__ our `KNeighborsClassifier()`
    - fit it to the training data using the `.fit()` __method__
    - make our predictions on the test data and store the results as `y_pred`
- Printing them shows that the predictions take on three values, as expected

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test =
    train_test_split(X, y, test_size=0.3,
                    random_state=21, stratify=y)
knn = KNeighborsClassifier(n_neighbors=8)
knn.fit(X_train, y_train)
y_pred = knn.predict(X_test)
print(\"Test set predictions:\\n {}\".format(y_pred))
```
```output
Test set predictions:
[2 1 2 2 1 0 1 0 0 1 0 2 0 2 2 0 0 0 1 0 2 2 2 0 1
1 1 0 0 1 2 2 0 0 2 2 1 1 2 1 1 0 2 1]
```

- To check out the accuracy of our model, we use the `score()` method of the model and pass it `X_test` and `y_test`
- See here that the accuracy of our K-nearest neighbors model is approximately 95%, which is pretty good for an out-of-the-box model!

```python
knn.score(X_test, y_test)
```
```output
0.9555555555555556
```

## Model complexity and over/underfitting
- Recall that we recently discussed the concept of a __decision boundary__
- Here, we visualize a decision boundary for several, increasing values of K in a KNN model
- Note that, as K increases, the decision boundary gets smoother and less curvy
- Therefore, we consider it to be a less complex model than those with a lower K
    - larger k = less complex model = smoother decision boundary (better at reflecting general trends in the data) => too much can lead to __underfitting__ 
    - smaller k = more complex model = can lead to __overfitting__ (sensitive to noise in the specific data)
- look at the __model complexity curve__ to see more
- We can see that there is a sweet spot in the middle that gives us the best performance on the test set

# the digits regconition datasets
 complete intro to import python first
