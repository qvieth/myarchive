# intro ml
- Begin Your Journey
- DING DING DING!
- It was but a dream and there’s still time
    - Understanding Machine Learning will help you change this bleak future, or be ready for it
- As you begin your journey through our Machine Learning curriculum, you will learn the different applications of this powerful field
- You will build your own models, test them, and try to improve them
- You will analyze bigger, and more complex data and deliver faster, more accurate results — even on a very large scale using:
    - Supervised Learning
    - Unsupervised Learning

Throughout your exploration of ML, we hope you gain an understanding of how to harness predictive models to do good, and enhance human life rather than replace it!
## Introduction: Foundations of Machine Learning: Supervised Learning
- The goal of this unit is to learn common supervised machine learning __algorithms__ and how to implement them using scikit-learn
- After this unit, you will be able to:
    - Understand what machine learning is
    - Use scikit-learn effectively to implement a variety of supervised learning models
    - Recognize the difference between supervised and unsupervised learning algorithms
    - Create regression models, including linear regression and multiple linear regression
    - Use past user data to predict Yelp ratings
    - Build k-nearest neighbors classifiers
    - Evaluate and improve your supervised model
    - Implement and train logistic regression and Naive Bayes classifiers
    - Create advanced classifiers with SVMs, Decision Trees, and Random Forests
    - Classify Twitter data using a variety of supervised models

## What is Machine Learning
- While at IBM, Arthur Samuel developed a program that learned how to play checkers (1959). He called it:
> “The field of study that gives computers the ability to learn without being explicitly programmed”
- What does this mean?
- As programmers, we often approach problems in a methodical, logic-based way
    - We try to determine what our desired outputs should be, and then create the proper rules that will transform our inputs into those outputs

- Machine learning flips the script
- We want the program itself to learn the rules that describe our data the best, by finding patterns in what we know and applying those patterns to what we don’t know

- These algorithms are able to learn
    - Their performance gets better and better with each iteration, as it uncovers more hidden trends in the data

![Machine Learning Timeline](https://content.codecademy.com/courses/updated_images/timeline2_Updated_1-01.svg)

- Machine learning can be branched out into the following categories:
    - Supervised Learning
    - Unsupervised Learning
## Supervised Learning
- Supervised Learning is where the data is labeled and the program learns to predict the output from the input data
    - For instance, a supervised learning algorithm for credit card fraud detection would take as input a set of recorded transactions
    - For each transaction, the program would predict if it is fraudulent or not

- Supervised learning problems can be further grouped into regression and classification problems
- Regression:
    - In regression problems, we are trying to predict a continuous-valued output. Examples are:
        - What is the housing price in Neo York?
        - What is the value of cryptocurrencies?
- Classification:
    - In classification problems, we are trying to predict a discrete number of values. Examples are:
        - Is this a picture of a human or a picture of an AI?
        - Is this email spam?

- For a quick preview, we will show you an example of supervised learning :
1. NYBD (Neo York Bot Department) wants to analyze how Neo Yorkers are talking to one another so that they can determine who is being negative
    - They have built a Naive Bayes classifier that predicts whether an intercepted text is good or bad
    - based on the frequency that a word is used in a good training example or a bad one
- Run the code to see if the model classifies the sentence "This hot dog was awful!" as a negative sentiment.
2. The NYBD wants to know what its citizens are saying
    - Put in the sentence "I love my government" in intercepted_text
    - and see if the classifier predicts a positive sentiment!
3.  Put a sentence of your own in intercepted_text and see if the classifier predicts a positive sentiment!
- Note: This Naive Bayes classifier won’t always get the sentiment correct!
```python
from texts import text_counter, text_training
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

intercepted_text = "I love Neo York."

text_counts = text_counter.transform([intercepted_text])

text_classifier = MultinomialNB()

text_labels = [0] * 1000 + [1] * 1000

text_classifier.fit(text_training, text_labels)

final_pos = text_classifier.predict_proba(text_counts)[0][1]

final_neg = text_classifier.predict_proba(text_counts)[0][0]

if final_pos > final_neg:
  print("The text is positive.")
else:
  print("The text is negative.")
```
## Unsupervised Learning
- Unsupervised Learning is a type of machine learning where the program learns the inherent structure of the data based on unlabeled examples

- Clustering is a common unsupervised machine learning approach that finds patterns and structures in unlabeled data by grouping them into clusters
- Some examples:
    - Social networks clustering topics in their news feed
    - Consumer sites clustering users for recommendations
    - Search engines to group similar objects in one cluster

- For a quick preview, we will show you an example of unsupervised learning
1. NYBD wants to determine how humans and cyborgs differ from each other in terms of:
   - The speed of recovering from wounds
   - Emotional intelligence (EQ)
   - Words per minute (WPM) reading speed
- They have taken measurements of these things for the Neo York population and have plotted them on 3 axes
- Press run to see the clusters!
```python
import matplotlib.pyplot as plt
import numpy as np 

from os.path import join, dirname, abspath
from mpl_toolkits.mplot3d import Axes3D

from sklearn.cluster import KMeans
from sklearn import datasets

iris = datasets.load_iris()

x = iris.data
y = iris.target

fignum = 1

# Plot the ground truth

fig = plt.figure(fignum, figsize=(4, 3))

ax = Axes3D(fig, rect=[0, 0, .95, 1], elev=48, azim=134)

for name, label in [('Robots', 0),
                    ('Cyborgs', 1),
                    ('Humans', 2)]:
    ax.text3D(x[y == label, 3].mean(),
              x[y == label, 0].mean(),
              x[y == label, 2].mean() + 2, name,
              horizontalalignment='center',
              bbox=dict(alpha=.2, edgecolor='w', facecolor='w'))

# Reorder the labels to have colors matching the cluster results

y = np.choose(y, [1, 2, 0]).astype(np.float)
ax.scatter(x[:, 3], x[:, 0], x[:, 2], c=y, edgecolor='k')

ax.w_xaxis.set_ticklabels([])
ax.w_yaxis.set_ticklabels([])
ax.w_zaxis.set_ticklabels([])

ax.set_xlabel('Time to Heal')
ax.set_ylabel('Reading Speed')
ax.set_zlabel('EQ')

ax.set_title('')
ax.dist = 12

plt.show()
```
