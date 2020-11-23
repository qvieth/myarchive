#  K-Nearest Neighbors Classifier
- ![documentation](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)
- [cheatsheet](https://www.codecademy.com/learn/paths/data-science/tracks/dscp-foundations-of-machine-learning-supervised-learning/modules/dscp-supervised-learning-introduction-to-classification-with-k-nearest-neighbors/cheatsheet)
- review
- Congratulations! You just implemented your very own classifier from scratch and used Python’s sklearn library
- In this lesson, you learned some techniques very specific to the K-Nearest Neighbor algorithm, but some general machine learning techniques as well
- Some of the major takeaways from this lesson include:
    - Data with `n` features can be conceptualized as points lying in n-dimensional space
    - Data points can be compared by using the __distance formula__
        - Data points that are similar will have a smaller distance between them
    - A point with an unknown class can be classified by finding the `k` nearest neighbors
    - To verify the effectiveness of a __classifier__, data with known classes can be split into a __training set__ and a __validation set__
        - __Validation error__ can then be calculated
    - Classifiers have __parameters__ that can be tuned to increase their effectiveness
        - In the case of K-Nearest Neighbors, `k` can be changed
    - A classifier can be trained improperly and suffer from overfitting or underfitting
        - In the case of K-Nearest Neighbors, a low `k` often leads to overfitting and a large `k` often leads to underfitting
    - Python’s sklearn library can be used for many classification and machine learning algorithms
- K-Nearest Neighbors (KNN) is a classification algorithm
- The central idea is that data points with similar attributes tend to fall into similar categories

![k-nearest](https://content.codecademy.com/courses/learn-knn/nearest_neighbor.gif)

- Consider the image to the right
    - This image is complicated, but for now, let’s just focus on where the data points are being placed
    - Every data point — whether its color is red, green, or white — has an x value and a y value
    - As a result, it can be plotted on this two-dimensional graph

- Next, let’s consider the color of the data
    - The color represents the class that the K-Nearest Neighbor algorithm is trying to classify
    - In this image, data points can either have the class green or the class red
    - If a data point is white, this means that it doesn’t have a class yet
    - The purpose of the algorithm is to classify these unknown points

- Finally, consider the expanding circle around the white point
    - This circle is finding the k nearest neighbors to the white point
    - When k = 3, the circle is fairly small
    - Two of the three nearest neighbors are green, and one is red
    - So in this case, the algorithm would classify the white point as green
    - However, when we increase k to 5, the circle expands, and the classification changes
    - Three of the nearest neighbors are red and two are green, so now the white point will be classified as red

- This is the central idea behind the K-Nearest Neighbor algorithm
    - If you have a dataset of points where the class of each point is known
    - you can take a new point with an unknown class, find it’s nearest neighbors, and classify it

<!-- vim-markdown-toc GFM -->

* [Introduction](#introduction)
* [Distance Between Points - 2D](#distance-between-points---2d)
* [Distance Between Points - 3D](#distance-between-points---3d)
* [Data with Different Scales: Normalization](#data-with-different-scales-normalization)
* [Finding the Nearest Neighbors](#finding-the-nearest-neighbors)
* [Count Neighbors](#count-neighbors)
* [Classify Your Favorite Movie](#classify-your-favorite-movie)
* [Training and Validation Sets](#training-and-validation-sets)
* [Choosing K](#choosing-k)
* [Graph of K](#graph-of-k)
* [Using sklearn](#using-sklearn)

<!-- vim-markdown-toc -->
## Introduction
- Before diving into the K-Nearest Neighbors algorithm, let’s first take a minute to think about an example

- Consider a dataset of movies
- Let’s brainstorm some features of a movie data point
- A feature is a piece of information associated with a data point
- Here are some potential features of movie data points:
    - the length of the movie in minutes
    - the budget of a movie in dollars

- If you think back to the previous exercise, you could imagine movies being places in that two-dimensional space based on those numeric features
- There could also be some boolean features: features that are either true or false
- For example, here are some potential boolean features:
    - Black and white
        - This feature would be True for black and white movies and False otherwise
    - Directed by Stanley Kubrick
        - This feature would be False for almost every movie, but for the few movies that were directed by Kubrick, it would be True

- Finally, let’s think about how we might want to classify a movie
    - For the rest of this lesson, we’re going to be classifying movies as either good or bad
    - In our dataset, we’ve classified a movie as good if it had an IMDb rating of 7.0 or greater
    - Every “good” movie will have a class of 1, while every bad movie will have a class of 0

- To the right, we’ve created some movie data points where the first item in the list is the length
    - the second is the budget, and the third is whether the movie was directed by Stanley Kubrick

## Distance Between Points - 2D
- In the first exercise, we were able to visualize the dataset and estimate the k nearest neighbors of an unknown point
    - But a computer isn’t going to be able to do that!

- We need to define what it means for two points to be close together or far apart
    - To do this, we’re going to use the __Distance Formula__

- For this example, the data has two dimensions:
    - The length of the movie
    - The movie’s release date
- Consider Star Wars and Raiders of the Lost Ark
    - Star Wars is 125 minutes long and was released in 1977
    - Raiders of the Lost Ark is 115 minutes long and was released in 1981

- The distance between the movies is computed below:
![a](https://content.codecademy.com/courses/learn-knn/StarWars-Raiders-Distance.png)

```python
star_wars = [125, 1977]
raiders = [115, 1981]
mean_girls = [97, 2004]

def distance(movie1, movie2):
  length_difference = (movie1[0] - movie2[0]) ** 2
  year_difference = (movie1[1] - movie2[1]) ** 2
  distance = (length_difference + year_difference) ** 0.5
  return distance

print(distance(star_wars, raiders))
print(distance(star_wars, mean_girls))
```
## Distance Between Points - 3D
- Making a movie rating predictor based on just the length and release date of movies is pretty limited
- There are so many more interesting pieces of data about movies that we could use! So let’s add another dimension

- Let’s say this third dimension is the movie’s budget
- We now have to find the distance between these two points in three dimensions
![3D graph](https://content.codecademy.com/courses/learn-knn/threed.png)

- What if we’re not happy with just three dimensions? Unfortunately, it becomes pretty difficult to visualize points in dimensions higher than 3
- But that doesn’t mean we can’t find the distance between them

- The generalized distance formula between points A and B is as follows:
```
sqrtroot((A1-B1)**2+(A2-B2)**2+...(An-Bn)**2)
```
- Here, A1-B1 is the difference between the first feature of each point
- An-Bn is the difference between the last feature of each point

- Using this formula, we can find the K-Nearest Neighbors of a point in N-dimensional space! We now can use as much information about our movies as we want

- We will eventually use these distances to find the nearest neighbors to an unlabeled point

## Data with Different Scales: Normalization
- In the next three lessons, we’ll implement the three steps of the K-Nearest Neighbor Algorithm:
    - Normalize the data
    - Find the `k` nearest neighbors
    - Classify the new point based on those neighbors
- When we added the dimension of budget, you might have realized there are some problems with the way our data currently looks

- Consider the two dimensions of release date and budget
    - The maximum difference between two movies’ release dates is about 125 years (The Lumière Brothers were making movies in the 1890s)
    - However, the difference between two movies’ budget can be millions of dollars

- The problem is that the distance formula treats all dimensions equally, regardless of their scale
    - If two movies came out 70 years apart, that should be a pretty big deal
    - However, right now, that’s exactly equivalent to two movies that have a difference in budget of 70 dollars
    - The difference in one year is exactly equal to the difference in one dollar of budget
    - That’s absurd!

- Another way of thinking about this is that the budget completely outweighs the importance of all other dimensions because it is on such a huge scale
    - The fact that two movies were 70 years apart is essentially meaningless compared to the difference in millions in the other dimension


- The solution to this problem is to [normalize](https://www.codecademy.com/articles/normalization) the data so every value is between 0 and 1
    - In this lesson, we’re going to be using min-max normalization

1. Write a function named min_max_normalize that takes a list of numbers named lst as a parameter (lst short for list)
- Begin by storing the minimum and maximum values of the list in variables named minimum and maximum
2. Create an empty list named normalized. Loop through each value in the original list
- Using min-max normalization, normalize the value and add the normalized value to the new list
- After adding every normalized value to normalized, return normalized
3. Call min_max_normalize using the given list release_dates
    - Print the resulting list
- What does the date 1897 get normalized to? Why is it closer to 0 than 1?

```python
release_dates = [1897.0, 1998.0, 2000.0, 1948.0, 1962.0, 1950.0, 1975.0, 1960.0, 2017.0, 1937.0, 1968.0, 1996.0, 1944.0, 1891.0, 1995.0, 1948.0, 2011.0, 1965.0, 1891.0, 1978.0]

def min_max_normalize(lst):
  minimum = min(lst)
  maximum = max(lst)
  normalized = []
  
  for value in lst:
    normalized_num = (value - minimum) / (maximum - minimum)
    normalized.append(normalized_num)
  
  return normalized

print(min_max_normalize(release_dates))
```
## Finding the Nearest Neighbors
- The K-Nearest Neighbor Algorithm:
    - Normalize the data
    - Find the k nearest neighbors
    - Classify the new point based on those neighbors
- Now that our data has been normalized and we know how to find the distance between two points, we can begin classifying unknown data!

- To do this, we want to find the k nearest neighbors of the unclassified point
    - In a few exercises, we’ll learn how to properly choose k, but for now, let’s choose a number that seems somewhat reasonable
    - Let’s choose 5

- In order to find the 5 nearest neighbors, we need to compare this new unclassified movie to every other movie in the dataset
    - This means we’re going to be using the distance formula again and again
    - We ultimately want to end up with a sorted list of distances and the movies associated with those distances

- It might look something like this:
```python
[
  [0.30, 'Superman II'],
  [0.31, 'Finding Nemo'],
  ...
  ...
  [0.38, 'Blazing Saddles']
]
```
- In this example, the unknown movie has a distance of 0.30 to Superman II

- In the next exercise, we’ll use the labels associated with these movies to classify the unlabeled point

## Count Neighbors
- The K-Nearest Neighbor Algorithm:
    - Normalize the data
    - Find the k nearest neighbors
    - Classify the new point based on those neighbors

- We’ve now found the k nearest neighbors, and have stored them in a list that looks like this:
```python
[
  [0.083, 'Lady Vengeance'],
  [0.236, 'Steamboy'],
  ...
  ...
  [0.331, 'Godzilla 2000']
]
``` 

- Our goal now is to count the number of good movies and bad movies in the list of neighbors
    - If more of the neighbors were good, then the algorithm will classify the unknown movie as good
    - Otherwise, it will classify it as bad

- In order to find the class of each of the labels, we’ll need to look at our movie_labels dataset
- For example, movie_labels['Akira'] would give us 1 because Akira is classified as a good movie

- You may be wondering what happens if there’s a tie
    - What if k = 8 and four neighbors were good and four neighbors were bad?
    - There are different strategies, but one way to break the tie would be to choose the class of the closest point
## Classify Your Favorite Movie
- Nice work! Your classifier is now able to predict whether a movie will be good or bad
- So far, we’ve only tested this on a completely random point [.4, .2, .9]
- In this exercise we’re going to pick a real movie, normalize it, and run it through our classifier to see what it predicts!

- In the instructions below, we are going to be testing our classifier using the 2017 movie Call Me By Your Name
- Feel free to pick your favorite movie instead!

## Training and Validation Sets
- You’ve now built your first K Nearest Neighbors algorithm capable of classification
- You can feed your program a never-before-seen movie and it can predict whether its IMDb rating was above or below 7.0
- However, we’re not done yet
    - We now need to report how effective our algorithm is
    - After all, it’s possible our predictions are totally wrong!

As with most machine learning algorithms, we have split our data into a training set and validation set

- Once these sets are created, we will want to use every point in the validation set as input to the K Nearest Neighbor algorithm
    - We will take a movie from the validation set, compare it to all the movies in the training set, find the K Nearest Neighbors, and make a prediction
    - After making that prediction, we can then peek at the real answer (found in the validation labels) to see if our classifier got the answer correct

- If we do this for every movie in the validation set, we can count the number of times the classifier got the answer right and the number of times it got it wrong
    - Using those two numbers, we can compute the validation accuracy

- Validation accuracy will change depending on what K we use
- In the next exercise, we’ll use the validation accuracy to pick the best possible K for our classifier

## Choosing K
- In the previous exercise, we found that our classifier got one point in the training set correct
- Now we can test every point to calculate the validation accuracy

- The validation accuracy changes as k changes
    - The first situation that will be useful to consider is when k is very small
    - Let’s say k = 1
    - We would expect the validation accuracy to be fairly low due to overfitting
    - Overfitting is a concept that will appear almost any time you are writing a machine learning algorithm
    - Overfitting occurs when you rely too heavily on your training data
        - you assume that data in the real world will always behave exactly like your training data
    - In the case of K-Nearest Neighbors, overfitting happens when you don’t consider enough neighbors
    - A single outlier could drastically determine the label of an unknown point
    - Consider the image below

![colored dots with a single outlier](https://content.codecademy.com/courses/learn-knn/overfit.png)

- The dark blue point in the top left corner of the graph looks like a fairly significant outlier
    - When k = 1, all points in that general area will be classified as dark blue when it should probably be classified as green
    - Our classifier has relied too heavily on the small quirks in the training data

- On the other hand, if k is very large, our classifier will suffer from underfitting
    - Underfitting occurs when your classifier doesn’t pay enough attention to the small quirks in the training set
    - Imagine you have 100 points in your training set and you set k = 100
    - Every single unknown point will be classified in the same exact way
    - The distances between the points don’t matter at all! This is an extreme example
    - however, it demonstrates how the classifier can lose understanding of the training data if k is too big
## Graph of K
- The graph to the right shows the validation accuracy of our movie classifier as k increases
- When k is small, overfitting occurs and the accuracy is relatively low
- On the other hand, when k gets too large, underfitting occurs and accuracy starts to drop

- what seems to be the best `k` for this dataset

![k](https://content.codecademy.com/courses/updated_images/KnnGraph_Update_1.svg)

## Using sklearn
- You’ve now written your own K-Nearest Neighbor classifier from scratch! However, rather than writing your own classifier every time, you can use Python’s sklearn library
    - sklearn is a Python library specifically used for Machine Learning
    - It has an amazing number of features, but for now, we’re only going to investigate its K-Nearest Neighbor classifierx

- There are a couple of steps we’ll need to go through in order to use the library
    - First, you need to create a KNeighborsClassifier object
    - This object takes one parameter - k
    - For example, the code below will create a classifier where k = 3
```python
classifier = KNeighborsClassifier(n_neighbors = 3)
```
- Next, we’ll need to train our classifier. The .fit() method takes two parameters. The first is a list of points, and the second is the labels associated with those points. So for our movie example, we might have something like this
```python
training_points = [
  [0.5, 0.2, 0.1],
  [0.9, 0.7, 0.3],
  [0.4, 0.5, 0.7]
]
 
training_labels = [0, 1, 1]
classifier.fit(training_points, training_labels)
```
- Finally, after training the model, we can classify new points
    - The .predict() method takes a list of points that you want to classify
    - It returns a list of its guesses for those points
```python
unknown_points = [
  [0.2, 0.1, 0.7],
  [0.4, 0.7, 0.6],
  [0.5, 0.8, 0.1]
]
 
guesses = classifier.predict(unknown_points)
```
