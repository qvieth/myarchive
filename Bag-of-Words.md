# Bag of Words language model
- [Working with Text Data | Scikit-learn](https://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html#extracting-features-from-text-files) : learn about the scikit-learn tools for generating language models like __bag-of-words__ using text data
- http://archive.ics.uci.edu/ml/index.php
- Review of Bag-of-Words
- You made it! And you’ve learned plenty about the bag-of-words language model along the way:
    - Bag-of-words (BoW) — also referred to as the unigram model — is a statistical language model based on word count
    - There are loads of real-world applications for BoW
    - BoW can be implemented as a Python dictionary with each key set to a word and each value set to the number of times that word appears in a text
    - For BoW, training data is the text that is used to build a BoW model
    - BoW test data is the new text that is converted to a BoW vector using a trained features dictionary
    - A feature vector is a numeric depiction of an item’s salient features
    - Feature extraction (or vectorization) is the process of turning text into a BoW vector
    - A features dictionary is a mapping of each unique word in the training data to a unique index
        - This is used to build out BoW vectors
    - BoW has less data sparsity than other statistical models
        - It also suffers less from overfitting
    - BoW has higher perplexity than other models, making it less ideal for language prediction
    - One solution to overfitting is language smoothing, in which a bit of probability is taken from known words and allotted to unknown words
- The spam data for this lesson were taken from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/sms%20spam%20collection) 
<!-- vim-markdown-toc GFM -->

* [Bag-of-What? : n-gram with n = 1 : unigram](#bag-of-what--n-gram-with-n--1--unigram)
* [BoW Dictionaries](#bow-dictionaries)
* [Introducing BoW Vectors](#introducing-bow-vectors)
* [Building a Features Dictionary](#building-a-features-dictionary)
* [Building a BoW Vector](#building-a-bow-vector)
* [It's All in the Bag](#its-all-in-the-bag)
* [Spam A Lot No More](#spam-a-lot-no-more)
* [BoW Wow](#bow-wow)
* [BoW Ow](#bow-ow)
* [review](#review)

<!-- vim-markdown-toc -->
- “A bag-of-words is all you need,” some NLPers have decreed
- The bag-of-words language model is a simple-yet-powerful tool
    - to have up your sleeve when working on natural language processing (NLP)
- The model has many, many __use cases__ including:
    - determining topics in a song
    - filtering spam from your inbox
    - finding out if a tweet has positive or negative sentiment
    - creating word clouds
- spam filter
```python
from spam_data import training_spam_docs, training_doc_tokens, training_labels
from sklearn.naive_bayes import MultinomialNB
from preprocessing import preprocess_text

# Add your email text to test_text between the triple quotes:
test_text = """
Add your email text here
Have you ever wondered how an email ends up in the spam folder?
Or how customer service phone systems are able to understand what you're saying?
From a cleaner inbox to faster customer service and virtual assistants that can tell you the weather
the number of applications using natural language processing (NLP) is rapidly growing
NLP is all about how computers work with human language
Learn how to create your own powerful NLP programs with this new course!

Start Now
 
Happy coding,
Codecademy
"""
test_tokens = preprocess_text(test_text)

def create_features_dictionary(document_tokens):
  features_dictionary = {}
  index = 0
  for token in document_tokens:
    if token not in features_dictionary:
      features_dictionary[token] = index
      index += 1
  return features_dictionary

def tokens_to_bow_vector(document_tokens, features_dictionary):
  bow_vector = [0] * len(features_dictionary)
  for token in document_tokens:
    if token in features_dictionary:
      feature_index = features_dictionary[token]
      bow_vector[feature_index] += 1
  return bow_vector

bow_sms_dictionary = create_features_dictionary(training_doc_tokens)
training_vectors = [tokens_to_bow_vector(training_doc, bow_sms_dictionary) for training_doc in training_spam_docs]
test_vectors = [tokens_to_bow_vector(test_tokens, bow_sms_dictionary)]

spam_classifier = MultinomialNB()
spam_classifier.fit(training_vectors, training_labels)

predictions = spam_classifier.predict(test_vectors)

print("Looks like a normal email!" if predictions[0] == 0 else "You've got spam!")
```
## Bag-of-What? : n-gram with n = 1 : unigram
- __Bag-of-words (BoW)__ is a statistical language model based on word count. Say what?

- Let’s start with that first part: a statistical language model is a way for computers to make sense of language based on probability
    - For example, let’s say we have the text:
“Five fantastic fish flew off to find faraway functions
    Maybe find another five fantastic fish?”

- A statistical language model focused on the starting letter for words might take this text
    - and predict that words are most likely to start with the letter “f” because 11 out of 15 words begin that way
- A different statistical model that pays attention to word order might tell us that the word “fish” tends to follow the word “fantastic”

- Bag-of-words does not give a flying fish about word starts or word order though
- its sole concern is word count — how many times each word appears in a document

- If you’re already familiar with statistical language models
    - you may also have heard BoW referred to as the __unigram model__

- It’s technically a special case of another __statistical model__
    - the __n-gram model__, with n (__the number of words in a sequence__) set to 1

- If you have no idea what n-grams are, don’t worry — we’ll dive deeper into them in another lesson

## BoW Dictionaries
- One of the most common ways to implement the BoW model in Python is
    - as a dictionary with each __key__ set to a __word__
    - and each __value__ set to the __number of times__ that word appears
- Take the example below:
    - "The squids jumped out of the suitcases"
- The words from the sentence go into the bag-of-words and come out as a dictionary of words with their corresponding counts
- For statistical models, we call __the text that we use to build the model__ our __training data__
- Usually, we need to prepare our text data by breaking it up into documents (shorter strings of text, generally sentences)

- Let’s build a function that converts a given training text into a bag-of-words!
    1. Define a function text_to_bow() that accepts some_text as a variable
        - Inside the function, set bow_dictionary equal to an empty dictionary and return it from the function
        - This is where we’ll be collecting the words and their counts
    2.  Above the return statement, call the `preprocess_text()` function we created for you on `some_text` and assign the result to the variable `tokens`
        - Text preprocessing allows us to count words like “game” and “Games” as the same word token
    3.  Still above the `return`, iterate over each `token` in `tokens` and check if `token` is already in the `bow_dictionary`
        - If it is, increment that token’s count by 1
            - (Remember that each token‘s count is its corresponding value within the bow_dictionary.)
        - Otherwise, set the count equal to 1 because this is the first time the model has seen that word token
```python
from preprocessing import preprocess_text
# Define text_to_bow() below:
def text_to_bow(some_text):
  bow_dictionary = {}
  tokens = preprocess_text(some_text)
  for token in tokens:
    if token in bow_dictionary:
      bow_dictionary[token] += 1
    else:
      bow_dictionary[token] = 1
  return bow_dictionary

print(text_to_bow("I love fantastic flying fish. These flying fish are just ok, so maybe I will find another few fantastic fish..."))
```
## Introducing BoW Vectors
- Sometimes a dictionary just won’t fit the bill
- __Topic modelling__ applications, for example, require an implementation of bag-of-words that is a bit more mathematical: __feature vectors__
- A __feature vector__ is a numeric representation of an item’s important features
- Each feature has its own column
- If the feature exists for the item, you could represent that with a `1`
- If the feature does not exist for that item, you could represent that with a `0`
- A few monsters could be represented as vectors like so:

|          | has_fangs | melts_in_water | hates_sunlight | has_fur |
|----------|-----------|----------------|----------------|---------|
| vampire  | 1         | 0              | 1              | 0       |
| werewolf | 1         | 0              | 0              | 1       |
| witch    | 0         | 1              | 0              | 0       |

- For bag-of-words, instead of monsters you would have documents and the features would be different words
- And we don’t just care if a word is present in a document
    - we want to know how many times it occurred!
    - Turning text into a BoW vector is known as __feature extraction__ or __vectorization__

- But how do we know which vector index corresponds to which word?
    - When building BoW vectors, we generally create a __features dictionary__ of all vocabulary in our training data (usually several documents) mapped to indices

- For example, with “Five fantastic fish flew off to find faraway functions
- Maybe find another five fantastic fish?” our dictionary might be:
```python
{'five': 0,
'fantastic': 1,
'fish': 2,
'fly': 3,
'off': 4,
'to': 5,
'find': 6,
'faraway': 7,
'function': 8,
'maybe': 9,
'another': 10}
```
- Using this dictionary, we can convert new documents into vectors using a vectorization function
- For example, we can take a brand new sentence “Another five fish find another faraway fish” 
- __test data__ — and convert it to a vector that looks like:
```python
[1, 0, 2, 0, 0, 0, 1, 1, 0, 0, 2]
```
- The word ‘another’ appeared twice in the test data
- If we look at the feature dictionary for ‘another’, we find that its index is `10`
- So when we go back and look at our vector, we’d expect the number at index `10` to be `2`

## Building a Features Dictionary
- Now that you know what a bag-of-words vector looks like, you can create a function that builds them!
- First, we need a way of generating a features dictionary from a list of training documents
- We can build a Python function to do that for us…


1. Define a function `create_features_dictionary()` that takes one argument, documents
    - This will be the list of string documents that we pass in like :
        - ["All the cool fish love to fly high"
        - "Nobody knows why the fish fly so high"
        - "Those cool fish sure are spry."]
    - Inside the function, set features_dictionary equal to an empty dictionary
    - This is where we’ll map all of our terms to index numbers
    - For now, return features_dictionary from the function
2. Above the return statement, merge the documents into a string joined together by spaces and assign the result to merged
    - Now that the documents are all in a single string, call `preprocess_text()` on merged and assign the result to tokens
    - Return tokens from the function in addition to `features_dictionary`
3. Above the return statement, assign index a value of 0
    - This will correspond to the first word’s vector index
4. The words are prepared, the empty dictionary is prepared, and we have an index number we can use
    - it’s time to get the words into the dictionary and link each to a vector index number!
        - Above the return, loop through each token in tokens
        - In the loop, check if token is NOT in features_dictionary
        - If it’s a new word, add token as a key to features_dictionary with a value of index
5.  After adding token to `features_dictionary`, increment index by 1 so that each new word has its own index
6.  Uncomment the print statement to test out the function!

```python
from preprocessing import preprocess_text
# Define create_features_dictionary() below:


training_documents = ["Five fantastic fish flew off to find faraway functions.", "Maybe find another five fantastic fish?", "Find my fish with a function please!"]

#print(create_features_dictionary(training_documents)[0])
```
```python
from preprocessing import preprocess_text
# Define create_features_dictionary() below:
def create_features_dictionary(documents):
  features_dictionary = {}
  merged = " ".join(documents)
  tokens = preprocess_text(merged)
  index = 0
  for token in tokens:
    if token not in features_dictionary:
      features_dictionary[token] = index
      index += 1
  return features_dictionary, tokens

training_documents = ["Five fantastic fish flew off to find faraway functions.", "Maybe find another five fantastic fish?", "Find my fish with a function please!"]

print(create_features_dictionary(training_documents)[0])
```

## Building a BoW Vector
- Nice work! Time to put that dictionary of vocabulary to good use
    - and build a bag-of-words vector from a new document
    - ![feature vector vs feature dictionary](https://content.codecademy.com/courses/NLP/Building_vector.gif)
- In Python, we can use a list to represent a vector
- Each index in the list will correspond to a word and be set to its count 
- challenge : 
1. Define a function text_to_bow_vector() with two parameters:
    - some_text (the document we pass in to vectorize)
    - features_dictionary (the dictionary of vocabulary we generated in the previous exercise)
- Create a list of 0s the length of features_dictionary and assign it to the variable bow_vector
- Each 0 represents a word’s count within the vector
- Return bow_vector from the function.
2.  Above the return statement, preprocess the some_text document using the preprocess_text() function we built for you and assign the result to the variable tokens
    - Add tokens as a second return value for the function
3. Still above the return statement, loop through each token in tokens
    - Determine which index the token has within features_dictionary and assign the value to a new variable feature_index
        - (Take a look at the gif. If token is the word fish, then we would want feature_index to be 2.)
    - Now that you have the word’s index, access the word count index within the bow_vector and increment that count by 1
4. Uncomment the print statement to test out the function!

```python
from preprocessing import preprocess_text
# Define text_to_bow_vector() below:


features_dictionary = {'function': 8, 'please': 14, 'find': 6, 'five': 0, 'with': 12, 'fantastic': 1, 'my': 11, 'another': 10, 'a': 13, 'maybe': 9, 'to': 5, 'off': 4, 'faraway': 7, 'fish': 2, 'fly': 3}

text = "Another five fish find another faraway fish."
#print(text_to_bow_vector(text, features_dictionary)[0])
```
```python
from preprocessing import preprocess_text
# Define text_to_bow_vector() below:
def text_to_bow_vector(some_text, features_dictionary):
  bow_vector = [0] * len(features_dictionary)
  tokens = preprocess_text(some_text)
  for token in tokens:
    feature_index = features_dictionary[token]
    bow_vector[feature_index] += 1
  return bow_vector, tokens

features_dictionary = {'function': 8, 'please': 14, 'find': 6, 'five': 0, 'with': 12, 'fantastic': 1, 'my': 11, 'another': 10, 'a': 13, 'maybe': 9, 'to': 5, 'off': 4, 'faraway': 7, 'fish': 2, 'fly': 3}

text = "Another five fish find another faraway fish."
print(text_to_bow_vector(text, features_dictionary)[0])
```
## It's All in the Bag
- Phew! That was a lot of work.
- It’s time to put `create_features_dictionary()` and `tokens_to_bow_vector()` together and use them in a spam filter we created that uses a Naive Bayes classifier
- We’ve slightly modified the two functions for this use case, but they should still look familiar

- Let’s see `create_features_dictionary()` and `tokens_to_bow_vector()` in action with real test data, helping fend off spam!

- comeback later

## Spam A Lot No More
- Amazing work! As is the case with many tasks in Python, there’s already a library that can do all of that work for you
- For `text_to_bow()`, you can approximate the functionality with the `collections` module’s `Counter()` function:
```python
from collections import Counter
 
tokens = ['another', 'five', 'fish', 'find', 'another', 'faraway', 'fish']
print(Counter(tokens))
 
# Counter({'fish': 2, 'another': 2, 'find': 1, 'five': 1, 'faraway': 1})
```
- For __vectorization__, you can use `CountVectorizer` from the machine learning library `scikit-learn`
    - You can use `fit()` to train the __features dictionary__ and then `transform()` to transform text into a vector:
```python
from sklearn.feature_extraction.text import CountVectorizer
 
training_documents = ["Five fantastic fish flew off to find faraway functions.", "Maybe find another five fantastic fish?", "Find my fish with a function please!"]
test_text = ["Another five fish find another faraway fish."]
bow_vectorizer = CountVectorizer()
bow_vectorizer.fit(training_documents)
bow_vector = bow_vectorizer.transform(test_text)
print(bow_vector.toarray())
# [[2 0 1 1 2 1 0 0 0 0 0 0 0 0 0]]
```
## BoW Wow
- As you can see, bag-of-words is pretty useful! BoW also has several advantages over other language models
- For one, it’s an easier model to get started with and a few Python libraries already have built-in support for it

- Because bag-of-words relies on single words, rather than sequences of words, there are more examples of each unit of language in the training corpus
- More examples means the model has less data sparsity (i.e., it has more training knowledge to draw from) than other statistical models

- Imagine you want to make a shirt to sell to people
    - If you have the shirt exactly tailored to someone’s body, it probably won’t fit that many people
    - But if you make a shirt that is just a giant bag with arm holes, you know that no one will buy it
    - What do you do? You loosely fit the shirt to someone’s body, leaving some extra room for different body shapes

- Overfitting (adapting a model too strongly to training data, akin to our highly tailored shirt) is a common problem for statistical language models
- While BoW still suffers from overfitting in terms of vocabulary
    - it overfits less than other statistical models, allowing for more flexibility in grammar and word choice

- The combination of low data sparsity and less overfitting makes the bag-of-words model more reliable with smaller training data sets than __other statistical models__

## BoW Ow
- Alas, there is a trade-off for all the brilliance BoW brings to the table
- Unless you want sentences that look like “the a but for the”, BoW is NOT a great primary model for text prediction
- If that sort of “sentence” isn’t your bag, it’s because bag-of-words has high perplexity
    - meaning that it’s not a very accurate model for language prediction
- The probability of the following word is always just the most frequently used words

- If your BoW model finds “good” frequently occurring in a text sample
    - you might assume there’s a positive sentiment being communicated in that text…
    - but if you look at the original text you may find that in fact every “good” was preceded by a “not ”

- Hmm, that would have been helpful to know
- The BoW model’s word tokens lack context, which can make a word’s intended meaning unclear

- Perhaps you are wondering
    - “What happens if the model comes across a new word that wasn’t in the training data?”
    - As mentioned, like all statistical models, BoW suffers from overfitting when it comes to vocabulary

- There are several ways that NLP developers have tackled this issue
- A common approach is through language smoothing in which some probability is siphoned from the known words and given to unknown words
## review
- Feel free to play around with the spam data using your new BoW knowledge. You can also use this workspace to try out other bag-of-words use cases
```python
from spam_data import training_spam_docs, training_doc_tokens, training_labels, training_docs
from sklearn.naive_bayes import MultinomialNB
from sklearn.feature_extraction.text import CountVectorizer

test_text = """
Play around with the spam classifier!
"""

bow_vectorizer = CountVectorizer()

training_vectors = bow_vectorizer.fit_transform(training_docs)
test_vectors = bow_vectorizer.transform([test_text])

spam_classifier = MultinomialNB()
spam_classifier.fit(training_vectors, training_labels)

predictions = spam_classifier.predict(test_vectors)

print("Looks like a normal email!" if predictions[0] == 0 else "You've got spam!")
```
