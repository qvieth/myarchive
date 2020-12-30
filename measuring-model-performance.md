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

