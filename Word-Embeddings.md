# Word Embeddings
- [Token.similarity | spaCy](https://spacy.io/api/token) : This is helpful if you would like to process and derive insights from unstructured textual data
- Review
- Lost in a multidimensional vector space after this lesson? We hope not! We have covered a lot here, so let’s take some time to recap.
    - __Vectors__ are containers of information, and they can have anywhere from 1-dimension to hundreds or thousands of dimensions
    - __Word embeddings__ are vector representations of a word, where words with similar contexts are represented with vectors that are closer together
    - __spaCy__ is a package that enables us to view and use pre-trained word embedding models
    - The distance between vectors can be calculated in many ways, and the best way for measuring the distance between higher dimensional vectors is __cosine distance__
    - Word2Vec is a __shallow neural network model__ that can build word embeddings using either __continuous bag-of-words__ or __continuous skip-grams__
    - Gensim is a package that allows us to create and train word embedding models using any corpus of text

<!-- vim-markdown-toc GFM -->

* [Vectors](#vectors)
* [What is a Word Embedding?](#what-is-a-word-embedding)
* [Distance](#distance)
* [Word Embeddings Are All About Distance](#word-embeddings-are-all-about-distance)
* [Word2vec](#word2vec)
* [Gensim](#gensim)

<!-- vim-markdown-toc -->
- There is a famous saying by German writer Johann Wolfgang von Goethe:
    - "Tell me with whom you consort and I will tell you who you are..."
- Goethe’s assumption is that the people you spend time with each and every day are a reflection of who you are as a person. Would you agree?
- Now, what if we extend that same idea from people to words? Linguist John Rupert Firth took this step and came up with his own saying:
"You shall know a word by the company it keeps"

- This idea that a word’s meaning can be understood by its context, or the words that surround it, is the basis for __word embeddings__
    - A __word embedding__ is a representation of a word as a numeric vector
        - enabling us to compare and contrast how words are used and identify words that occur in similar contexts

- The applications of word embeddings include:
    - entity recognition in chatbots
    - sentiment analysis
    - syntax parsing
- Have little to no experience with vectors? Do not fear!
- We’ll break down word embeddings and how they relate to vectors, step-by-step, in the next few exercises with the help of the spaCy package
```python
import spacy
from scipy.spatial.distance import cosine

# load word embedding model
nlp = spacy.load('en')

# define word embedding vectors
sponge_vec = nlp('sponge').vector
starfish_vec = nlp('starfish').vector
squid_vec = nlp('squid').vector

# compare vectors with cosine distance
dist_sponge_star = cosine(sponge_vec, starfish_vec)
print(dist_sponge_star)
dist_sponge_squid = cosine(sponge_vec, squid_vec)
print(dist_sponge_squid)
dist_star_squid = cosine(starfish_vec, squid_vec)
print(dist_star_squid)
```
```python
import spacy
from scipy.spatial.distance import cosine

# load model
nlp = spacy.load('en')

# define vectors
summer_vec = nlp("summer").vector
winter_vec = nlp("winter").vector

# compare similarity
print(f"The cosine distance between the word embeddings for 'summer' and 'winter' is: {cosine(summer_vec, winter_vec)}\n")

# define vectors
mustard_vec = nlp("mustard").vector
amazing_vec = nlp("amazing").vector

# compare similarity
print(f"The cosine distance between the word embeddings for 'mustard' and 'amazing' is: {cosine(mustard_vec, amazing_vec)}\n")

# display word embeddings
# print(f"'summer' in vector form: {summer_vec}")
# print(f"'winter' in vector form: {winter_vec}")
# print(f"'mustard' in vector form: {mustard_vec}")
# print(f"'amazing' in vector form: {amazing_vec}")
```
## Vectors
- Vectors can be many things in many different fields, but ultimately they are containers of information
    - Depending on the size, or the dimension, of a vector, it can hold varying amounts of data

- The simplest case is a 1-dimensional vector, which stores a single number
- Say we want to represent the length of a word with a vector
- We can do so as follows:
```
"cat" ----> [3]
"scrabble" ----> [8]
"antidisestablishmentarianism" ----> [28]
```
- Instead of looking at these three words with our own eyes
    - we can compare the vectors that represent them by plotting the vectors on a number line

![one-dimensional number line with vectors](https://content.codecademy.com/programs/chatbots/word-embeddings/vectors-one-dimension.png)

- We can clearly see that the “cat” vector is much smaller than the “scrabble” vector
    - which is much smaller than the “antidisestablishmentarianism” vector

- Now let’s say we also want to record the number of vowels in our words, in addition to the number of letters
- We can do so using a 2-dimensional vector, where the first entry is the length of the word, and the second entry is the number of vowels:
```
"cat" ----> [3, 1]
"scrabble" ----> [8, 2]
"antidisestablishmentarianism" ----> [28, 11]
```
- To help visualize these vectors, we can plot them on a two-dimensional grid
    - where the x-axis is the number of letters, and the y-axis is the number of vowels

[two-dimensional grid with vectors](https://content.codecademy.com/programs/chatbots/word-embeddings/vectors-two-dimensions.png)

- Here we can see that the vectors for “cat” and “scrabble” point to a more similar area of the grid than the vector for “antidisestablishmentarianism”
- So we could argue that “cat” and “scrabble” are closer together

- While we have shown here only 1-dimensional and 2-dimensional vectors, we are able to have vectors in any number of dimensions
- Even 1,000! The tricky part, however, is visualizing them

- Vectors are useful since they help us summarize information about an object using numbers
- Then, using the number representation, we can make comparisons between the vector representations of different objects!

- This idea is central to how word embeddings map words into vectors

- We can easily represent vectors in Python using NumPy arrays
- To create a vector containing the odd numbers from `1` to `9`, we can use NumPy’s `.array()` method:
```python
odd_vector = np.array([1, 3, 5, 7, 9])
```
- code challenge :
1. Say you are working at a school and want to analyze student scores on the first two English exams of the semester
    - One student, Xavier, scored 88 on the first exam and 92 on the second
    - Another student, Niko, scored 94 on the first exam and 87 on the second
- Create vectors using NumPy arrays called scores_xavier and scores_niko that contain the students’ exam scores. Make sure the first exam score is the first value in each vector!
2. Take a look at the web browser component
    - You should see the two vectors representing Xavier’s and Niko’s exam scores plotted on a grid
    - What do you notice about the two vectors? Are they close together?
- A new student Alena transfers into your class from a different section
    - Alena scored 90 on the first exam but struggled on the second, scoring 48
    - Create a new vector named scores_alena containing her exam scores in the same section of script.py where you defined the other exam vectors
    - Where do you think the vector will point to? And how similar is the vector for Alena’s scores to Xavier’s and Niko’s?
```python
import numpy as np
import matplotlib.pyplot as plt

# define score vectors
scores_xavier = np.array([88,92])
scores_niko = np.array([94,87])
scores_alena = np.array([90,48])

# plot vectors
try:
  plt.arrow(0, 0, scores_xavier[0], scores_xavier[1], width=1, color='blue')
except:
  pass
try:
  plt.arrow(0, 0, scores_niko[0], scores_niko[1], width=1, color='orange')
except:
  pass
try:
  plt.arrow(0, 0, scores_alena[0], scores_alena[1], width=1, color='purple')
except:
  pass
plt.axis([0, 100, 0, 100])
plt.show()
```
## What is a Word Embedding?
- Now that you have an understanding of vectors, let’s jump back to word embeddings
- Word embeddings are vector representations of a word

- They allow us to take all the information that is stored in a word
    - like its meaning and its part of speech
    - and convert it into a numeric form that is more understandable to a computer

- For example, we could look at a word embedding for the word “peace”
```
[5.2907305, -4.20267, 1.6989858, -1.422668, -1.500128, ...]
```
- Here “peace” is represented by a 96-dimension vector, with just the first five dimensions shown
    - Each dimension of the vector is capturing some information about how the word “peace” is used
    - We can also look at a word embedding for the word “war”:
```
[7.2966490, -0.52887750, 0.97479630, -2.9508233, -3.3934135, ...]
```
- By converting the words “war” and “peace” into their numeric vector representations
    - we are able to have a computer more easily compare the vectors and understand their similarities and differences

- We can load a basic English word embedding model using spaCy as follows:
```python
nlp = spacy.load('en')
```
- Note: the convention is to load spaCy models into a variable named `nlp`

- To get the vector representation of a word, we call the model with the desired word as an argument and can use the `.vector` attribute
```python
nlp('love').vector
```
- But how do we compare these vectors? And how do we arrive at these numeric representations?
```python
import spacy

# load word embedding model
nlp = spacy.load('en')

# define word embedding vectors
happy_vec = nlp('happy').vector
print(happy_vec)
sad_vec = nlp('sad').vector
print(sad_vec)
angry_vec = nlp('angry').vector
print(angry_vec)

# find vector length here
vector_length = len(happy_vec)
print(vector_length)
```
## Distance
- The key at the heart of word embeddings is distance
- Before we explain why, let’s dive into how the distance between vectors can be measured

- There are a variety of ways to find the distance between vectors, and here we will cover three
- The first is called Manhattan distance

- In Manhattan distance, also known as city block distance, distance is defined as the sum of the differences across each individual dimension of the vectors
- Consider the vectors [1,2,3] and [2,4,6]
- We can calculate the Manhattan distance between them as shown below:
```
manhattan distance = ∣1−2∣+∣2−4∣+∣3−6∣=1+2+3=6
```
- Another common distance metric is called the Euclidean distance, also known as straight line distance
- With this distance metric, we take the square root of the sum of the squares of the differences in each dimension

```
euclidean distance = sqrroot((1-2)^2+(2-4)^2+(3-6)^2)=sqrroot(14)=3.74
```
- The final distance we will consider is the cosine distance
    - Cosine distance is concerned with the angle between two vectors, rather than by looking at the distance between the points, or ends, of the vectors
    - Two vectors that point in the same direction have no angle between them, and have a cosine distance of 0
    - Two vectors that point in opposite directions, on the other hand, have a cosine distance of 1
    - We would show you the calculation, but we don’t want to scare you away! For the mathematically adventurous, you can read up on the calculation [here](https://en.wikipedia.org/wiki/Cosine_similarity#Definition)

- We can easily calculate the Manhattan, Euclidean, and cosine distances between vectors using helper functions from [SciPy](https://docs.scipy.org/doc/scipy-0.14.0/reference/index.html):
```python
from scipy.spatial.distance import cityblock, euclidean, cosine
 
vector_a = np.array([1,2,3])
vector_b = np.array([2,4,6])
 
# Manhattan distance:
manhattan_d = cityblock(vector_a,vector_b) # 6
 
# Euclidean distance:
euclidean_d = euclidean(vector_a,vector_b) # 3.74
 
# Cosine distance:
cosine_d = cosine(vector_a,vector_b) # 0.0
```
- When working with vectors that have a large number of dimensions
    - such as word embeddings, the distances calculated by Manhattan and Euclidean distance can become rather large
- Thus, calculations using cosine distance are preferred!
```python
import numpy as np
from scipy.spatial.distance import cityblock, euclidean, cosine
import spacy

# load word embedding model
nlp = spacy.load('en')

# define word embedding vectors
happy_vec = nlp('happy').vector
sad_vec = nlp('sad').vector
angry_vec = nlp('angry').vector

# calculate Manhattan distance
man_happy_sad = cityblock(happy_vec, sad_vec)
man_sad_angry = cityblock(sad_vec, angry_vec)
print(man_happy_sad, man_sad_angry)

# calculate Euclidean distance
euc_happy_sad = euclidean(happy_vec, sad_vec)
euc_sad_angry = euclidean(sad_vec, angry_vec)
print(euc_happy_sad, euc_sad_angry)

# calculate cosine distance
cos_happy_sad = cosine(happy_vec, sad_vec)
cos_sad_angry = cosine(sad_vec, angry_vec)
print(cos_happy_sad, cos_sad_angry)
```
## Word Embeddings Are All About Distance
- The idea behind word embeddings is a theory known as the __distributional hypothesis__
    - This hypothesis states that words that co-occur in the same contexts tend to have similar meanings
    - With word embeddings, we map words that exist with the same context
        - to similar places in our vector space (math-speak for the area in which our vectors exist)

- The numeric values that are assigned to the vector representation of a word are not important in their own right
    - but gather meaning from how similar or not words are to each other

- Thus the __cosine distance__ between words with similar contexts will be small
    - and the cosine distance between words that have very different contexts will be large

- The literal values of a word’s embedding have no actual meaning
    - We gain value in word embeddings from comparing the different word vectors and seeing how similar or different they are
    - Encoded in these vectors, however, is latent information about how they are used
## Word2vec
- You might be asking yourself a question now
    - How did we arrive at the vector values that define a word vector?
    - And how do we ensure that the values chosen place the vectors for words with similar context close together
    - and the vectors for words with different usages far apart?

- Step in word2vec! Word2vec is a statistical learning algorithm that develops word embeddings from a corpus of text
    - Word2vec uses one of two different model architectures to come up with the values that define a collection of word embeddings

- One method is to use the continuous bag-of-words (CBOW) representation of a piece of text
- The word2vec model goes through each word in the training corpus, in order
    - and tries to predict what word comes at each position based on applying bag-of-words to the words that surround the word in question
- In this approach, the order of the words does not matter!

- The other method word2vec can use to create word embeddings is continuous skip-grams
- Skip-grams function similarly to n-grams
    - except instead of looking at groupings of n-consecutive words in a text
    - we can look at sequences of words that are separated by some specified distance between them

- For example, consider the sentence `"The squids jump out of the suitcase"`
    - The 1-skip-2-grams includes all the bigrams (2-grams) as well as the following subsequences:
```
(The, jump), (squids, out), (jump, of), (out, the), (of, suitcase)
```
- When using continuous skip-grams, the order of context is taken into consideration!
- Because of this, the time it takes to train the word embeddings is slower than when using continuous bag-of-words
- The results, however, are often much better!

- With either the continuous bag-of-words or continuous skip-grams representations as training data
    - word2vec then uses a shallow, 2-layer neural network to come up with the values
    - that place words with a similar context in vectors near each other
    - and words with different contexts in vectors far apart from each other
- Let’s take a closer look to see how continuous bag-of-words and continuous skip-grams work!
```python
from sklearn.feature_extraction.text import CountVectorizer

sentence = "It was the best of times, it was the worst of times."
print(sentence)

# preprocessing
sentence_lst = [word.lower().strip(".") for word in sentence.split()]

# set context_length
context_length = 3

# function to get cbows
def get_cbows(sentence_lst, context_length):
  cbows = list()
  for i, val in enumerate(sentence_lst):
    if i < context_length:
      pass
    elif i < len(sentence_lst) - context_length:
      context = sentence_lst[i-context_length:i] + sentence_lst[i+1:i+context_length+1]
      vectorizer = CountVectorizer()
      vectorizer.fit_transform(context)
      context_no_order = vectorizer.get_feature_names()
      cbows.append((val,context_no_order))
  return cbows

# define cbows here:
cbows = get_cbows(sentence_lst, context_length)

# function to get cbows
def get_skip_grams(sentence_lst, context_length):
  skip_grams = list()
  for i, val in enumerate(sentence_lst):
    if i < context_length:
      pass
    elif i < len(sentence_lst) - context_length:
      context = sentence_lst[i-context_length:i] + sentence_lst[i+1:i+context_length+1]
      skip_grams.append((val, context))
  return skip_grams

# define skip_grams here:
skip_grams = get_skip_grams(sentence_lst, context_length)

try:
  print('\nContinuous Bag of Words')
  for cbow in cbows:
    print(cbow)
except:
  pass
try:
  print('\nSkip Grams')
  for skip_gram in skip_grams:
    print(skip_gram)
except:
  pass
```

## Gensim
- Depending on the corpus of text we select to train a word embedding model
    - different word embeddings will be created according to the context of the words in the given corpus
- The larger and more generic a corpus, however, the more generalizable the word embeddings become

- When we want to train our own word2vec model on a corpus of text, we can use the gensim package!

- In previous exercises, we have been using pre-trained word embedding models stored in spaCy
- These models were trained, using word2vec, on blog posts and news articles collected by the Linguistic Data Consortium at the University of Pennsylvania
- With gensim, however, we are able to build our own word embeddings on any corpus of text we like

- To easily train a word2vec model on our own corpus of text, we can use gensim’s Word2Vec() function
```python
model = gensim.models.Word2Vec(corpus, size=100, window=5, min_count=1, workers=2, sg=1)
```
    - `corpus` is a list of lists, where each inner list is a document in the corpus and each element in the inner lists is a word token
    - `size` determines how many dimensions our word embeddings will include. Word embeddings often have upwards of 1,000 dimensions! Here we will create vectors of 100-dimensions to keep things simple.
    - don’t worry about the rest of the keyword arguments here!

- To view the entire vocabulary used to train the word embedding model, we can use the `.wv.vocab.items()` method
```python
vocabulary_of_model = list(model.wv.vocab.items())

- When we train a word2vec model on a smaller corpus of text, we pick up on the unique ways in which words of the text are used

- For example, if we were using scripts from the television show Friends as a training corpus
    - the model would pick up on the unique ways in which words are used in the show
- While the generalized vectors in a spaCy model might not place the vectors for “Ross” and “Rachel” close together
    - a gensim word embedding model trained on Friends’ scrips would place the vectors for words like “Ross” and “Rachel”
    - two characters that have a continuous on and off-again relationship throughout the show, very close together!

- To easily find which vectors gensim placed close together in its word embedding model, we can use the .most_similar() method.
```python
model.most_similar("my_word_here", topn=100)
```
    - `"my_word_here"` is the target word token we want to find most similar words to
    - `topn` is a keyword argument that indicates how many similar word vectors we want returned

- One last gensim method we will explore is a rather fun one: `.doesnt_match()`
```python
model.doesnt_match(["asia", "mars", "pluto"])
```
    - when given a list of terms in the vocabulary as an argument, .doesnt_match() returns which term is furthest from the others.
- Let’s play around with gensim word2vec models to explore the word embeddings defined on our own corpus of training data!

## Gensim
- Depending on the corpus of text we select to train a word embedding model
    - different word embeddings will be created according to the context of the words in the given corpus
- The larger and more generic a corpus, however, the more generalizable the word embeddings become

- When we want to train our own word2vec model on a corpus of text, we can use the [gensim package!](https://radimrehurek.com/gensim/)

- In previous exercises, we have been using pre-trained word embedding models stored in spaCy
- These models were trained, using word2vec, on blog posts and news articles collected by the [Linguistic Data Consortium](https://catalog.ldc.upenn.edu/LDC2013T19) at the University of Pennsylvania
- With gensim, however, we are able to build our own word embeddings on any corpus of text we like

- To easily train a word2vec model on our own corpus of text, we can use gensim’s `Word2Vec()` function
```python
model = gensim.models.Word2Vec(corpus, size=100, window=5, min_count=1, workers=2, sg=1)
```
    - `corpus` is a list of lists, where each inner list is a document in the corpus and each element in the inner lists is a word token
    - `size` determines how many dimensions our word embeddings will include
        - Word embeddings often have upwards of 1,000 dimensions!
        - Here we will create vectors of 100-dimensions to keep things simple
    - don’t worry about the rest of the keyword arguments here!
- To view the entire vocabulary used to train the word embedding model, we can use the `.wv.vocab.items()` method
```python
vocabulary_of_model = list(model.wv.vocab.items())
```
- When we train a word2vec model on a smaller corpus of text, we pick up on the unique ways in which words of the text are used

- For example, if we were using scripts from the television show Friends as a training corpus
    - the model would pick up on the unique ways in which words are used in the show
- While the generalized vectors in a spaCy model might not place the vectors for “Ross” and “Rachel” close together
    - a gensim word embedding model trained on Friends’ scrips would place the vectors for words like “Ross” and “Rachel”
    - two characters that have a continuous on and off-again relationship throughout the show, very close together!

- To easily find which vectors gensim placed close together in its word embedding model, we can use the `.most_similar()` method
```python
model.most_similar("my_word_here", topn=100)
```
    - `"my_word_here"` is the target word token we want to find most similar words to
    - `topn` is a keyword argument that indicates how many similar word vectors we want returned

- One last gensim method we will explore is a rather fun one: `.doesnt_match()`
```python
model.doesnt_match(["asia", "mars", "pluto"])
```
    - when given a list of terms in the vocabulary as an argument, `.doesnt_match()` returns which term is furthest from the others

- Let’s play around with gensim word2vec models to explore the word embeddings defined on our own corpus of training data!
