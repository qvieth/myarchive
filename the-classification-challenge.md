# the classification challenge  

<!-- vim-markdown-toc GFM -->

* [k-Nearest Neighbors](#k-nearest-neighbors)
    * [Using scikit-learn to fit a classifier](#using-scikit-learn-to-fit-a-classifier)
    * [Predicting on unlabeled data](#predicting-on-unlabeled-data)

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
