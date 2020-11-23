# K-Nearest Neighbor Regressor

- Review

- Great work! Here are some of the major takeaways from this lesson:
    - The K-Nearest Neighbor algorithm can be used for regression
        - Rather than returning a classification, it returns a number
    - By using a weighted average, data points that are extremely similar to the input point will have more of a say in the final result
    - scikit-learn has an implementation of a K-Nearest Neighbor regressor named `KNeighborsRegressor`

- In the browser, you’ll find an example of a K-Nearest Neighbor regressor in action
    - Instead of the training data coming from IMDb ratings, you can create the training data yourself! Rate the movies that you have seen
    - Once you’ve rated more than `k` movies, a K-Nearest Neighbor regressor will train on those ratings
    - It will then make predictions for every movie that you haven’t seen

- As you add more and more ratings, the predictor should become more accurate
    - After all, the regressor needs information from the user in order to make personalized recommendations
    - As a result, the system is somewhat useless to brand new users — it takes some time for the system to “warm up” and get enough data about a user
    - This conundrum is an example of the cold start problem
- In this lesson, you will learn how the K-Nearest Neighbor algorithm can be modified to perform regression

## Regression
- The K-Nearest Neighbors algorithm is a powerful supervised machine learning algorithm typically used for classification
    - However, it can also perform regression

- In this lesson, we will use the movie dataset that was used in the K-Nearest Neighbors classifier lesson
    - However, instead of classifying a new movie as either good or bad, we are now going to predict its IMDb rating as a real number

- This process is almost identical to classification, except for the final step
    - Once again, we are going to find the k nearest neighbors of the new movie by using the distance formula
    - However, instead of counting the number of good and bad neighbors, the regressor averages their IMDb ratings

- For example, if the three nearest neighbors to an unrated movie have ratings of 5.0, 9.2, and 6.8
    - then we could predict that this new movie will have a rating of 7.0
## Weighted Regression
- 
## Scikit-learn
- Now that you’ve written your own K-Nearest Neighbor regression model, let’s take a look at scikit-learn’s implementation
    - The KNeighborsRegressor class is very similar to KNeighborsClassifier

- We first need to create the regressor
    - We can use the parameter n_neighbors to define our value for k

- We can also choose whether or not to use a weighted average using the parameter weights
    - If weights equals "uniform", all neighbors will be considered equally in the average
    - If weights equals "distance", then a weighted average is used
```python
classifier = KNeighborsRegressor(n_neighbors = 3, weights = "distance")
```
- Next, we need to fit the model to our training data using the .fit() method
    - .fit() takes two parameters
    - The first is a list of points, and the second is a list of values associated with those points
```python
training_points = [
  [0.5, 0.2, 0.1],
  [0.9, 0.7, 0.3],
  [0.4, 0.5, 0.7]
]
 
training_labels = [5.0, 6.8, 9.0]
classifier.fit(training_points, training_labels)
```
- Finally, we can make predictions on new data points using the .predict() method
    - .predict() takes a list of points and returns a list of predictions for those points
```python
unknown_points = [
  [0.2, 0.1, 0.7],
  [0.4, 0.7, 0.6],
  [0.5, 0.8, 0.1]
]
 
guesses = classifier.predict(unknown_points)
```
## Review

