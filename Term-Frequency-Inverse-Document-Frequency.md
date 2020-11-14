# Term Frequency-Inverse Document Frequency
- is a numerical statistic used to indicate how important a word is to each document in a collection of documents
- [use scikit-learn to conduct tf-idf](https://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html#from-occurrences-to-frequencies) : This is helpful if you are trying to determine topics or themes within text data
```
tfidf(t,d)=tf(t,d)∗idf(t,corpus)
```
    - `tf(t,d)` is the term frequency of term `t` in document `d`
    - `idf(t,corpus)` is the inverse document frequency of a term `t` across `corpus`
- tf-idf consists of two components, term frequency and inverse document frequency
    - term frequency is how often a word appears in a document
        - This is the same as bag-of-words’ word count
    - inverse document frequency is a measure of how often a word appears across all documents of a corpus
    - tf-idf is calculated as the term frequency multiplied by the inverse document frequency

    - `term frequency`, `inverse document frequency`, and `tf-idf`
        - can be calculated in __scikit-learn__ using the `CountVectorizer`, `TfidfTransformer`, and `TfidfVectorizer` objects, respectively

- Tf-idf is another powerful tool in your NLP toolkit that has a variety of use cases included:
    - ranking results in a search engine
    - text summarization
    - building smarter chatbots
![tf-idf](https://content.codecademy.com/programs/chatbots/tfidf/tfidf-transformer.gif)

<!-- vim-markdown-toc GFM -->

* [What is Tf-idf?](#what-is-tf-idf)
* [Breaking It Down Part I: Term Frequency](#breaking-it-down-part-i-term-frequency)
* [Breaking It Down Part II: Inverse Document Frequency](#breaking-it-down-part-ii-inverse-document-frequency)
* [Putting It All Together: Tf-idf](#putting-it-all-together-tf-idf)
* [Converting Bag-of-Words to Tf-idf](#converting-bag-of-words-to-tf-idf)

<!-- vim-markdown-toc -->

## What is Tf-idf?
- Term frequency-inverse document frequency is a numerical statistic used to indicate
    - how important a word is to each document in a collection of documents, or a corpus

- When applying tf-idf to a __corpus__
    - each word is given a tf-idf score for each document
    - representing the relevance of that word to the particular document
- A higher tf-idf score indicates a term is more important to the corresponding document

- Tf-idf has many similarities with the bag-of-words language model
    - which if you recall is concerned with word count 
    - how many times each word appears in a document

- While tf-idf can be used in any situation bag-of-words can be used
    - there is a key difference in how it is calculated

- Tf-idf relies on two different metrics in order to come up with an overall score:
    - term frequency, or how often a word appears in a document
        - This is the same as bag-of-words’ word count
    - inverse document frequency, which is a measure of how often a word appears in the overall corpus
        - By penalizing the score of words that appear throughout a corpus
        - tf-idf can give better insight into how important a word is to a particular document of a corpus

- We will dig into each component of tf-idf in the next two exercises

```python
from preprocessing import preprocess_text
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer

# sample documents
document_1 = "This is a sample piece of text!"
document_2 = "This is my second sentence of text."
document_3 = "Is this my third sentence of text?"

# corpus of documents
corpus = [document_1, document_2, document_3]

# preprocess documents
processed_corpus = [preprocess_text(doc) for doc in corpus]

# initialize and fit TfidfVectorizer
vectorizer = TfidfVectorizer(norm=None)
tf_idf_scores = vectorizer.fit_transform(processed_corpus)

# get vocabulary of terms
feature_names = vectorizer.get_feature_names()
corpus_index = [n for n in processed_corpus]

# create pandas DataFrame with tf-idf scores
df_tf_idf = pd.DataFrame(tf_idf_scores.T.todense(), index=feature_names, columns=corpus_index)
print(df_tf_idf)
```
## Breaking It Down Part I: Term Frequency
- The first component of tf-idf is term frequency, or how often a word appears in a document within the corpus
- The value for the term frequency is the same as if applying the bag-of-words language model to a document
- If you have previously studied bag-of-words, this will all be familiar! If not, have no fear

- Term frequency indicates how often each word appears in the document
- The intuition for including term frequency in the tf-idf calculation is that
    - the more frequently a word appears in a __single document__ the more important that term is to the document

- Consider the stanza from Emily Dickinson’s poem I’m Nobody! Who are you? below:
```python
stanza = '''I'm nobody! Who are you?
Are you nobody, too?
Then there's a pair of us — don't tell!
They'd banish us, you know.'''
```
- The term frequency for “you” is `3`, “nobody” is `2`, “are” is `2`, “us” is `2`, and the rest of the terms have a frequency of `1`
- We can get a general sense of what this stanza is about by the most frequently used words.

Term frequency can be calculated in Python using scikit-learn’s `CountVectorizer`, as shown below:
```python
vectorizer = CountVectorizer()
 
term_frequencies = vectorizer.fit_transform([stanza])
```
    - A `CountVectorizer` object is initialized
    - The `CountVectorizer` object is fit (trained) and transformed (applied) on the corpus of data, returning the term frequencies for each term-document pair

```python
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer
from preprocessing import preprocess_text

poem = '''
Success is counted sweetest
By those who ne'er succeed.
To comprehend a nectar
Requires sorest need.

Not one of all the purple host
Who took the flag to-day
Can tell the definition,
So clear, of victory,

As he, defeated, dying,
On whose forbidden ear
The distant strains of triumph
Break, agonized and clear!'''

# define clear_count:
clear_count = 2

# preprocess text
processed_poem = preprocess_text(poem)

# initialize and fit CountVectorizer
vectorizer = CountVectorizer()
term_frequencies = vectorizer.fit_transform([processed_poem])

# get vocabulary of terms
feature_names = vectorizer.get_feature_names()

# create pandas DataFrame with term frequencies
try:
  df_term_frequencies = pd.DataFrame(term_frequencies.T.todense(), index=feature_names, columns=['Term Frequency'])
  print(df_term_frequencies)
except:
  pass
```

## Breaking It Down Part II: Inverse Document Frequency
- The inverse document frequency component of the tf-idf score penalizes terms that appear more frequently across a corpus
- The intuition is that words that appear more frequently in the __corpus__
    - give less insight into the topic or meaning of an individual document, and should thus be deprioritized

- For example, terms like “the” or “go” are used all over the place, so in a bag-of-words model
    - they would be given priority even though they don’t provide much meaning; tf-idf would deprioritize these sorts of common words

- We can calculate the inverse document frequency for some term t across a corpus using the below equation
- Don’t be scared if you aren’t a math person!
```
log(Total number of documents/Number of documents with term t)
```
- The important take away from the equation is that as the number of documents with the term t increases
- the inverse document frequency decreases (due to the nature of the log function)
- The more frequently a term appears across the corpus, the less important it becomes to an individual document

- Inverse document frequency can be calculated on a group of documents using scikit-learn’s `TfidfTransformer`:
```python
transformer = TfidfTransformer(norm=None)
transformer.fit(term_frequencies)
inverse_doc_frequency = transformer.idf_
```
    - a `TfidfTransformer` object is initialized
        - Don’t worry about the norm=None keyword argument for now, we will dig into this in the next exercise
    - the `TfidfTransformer` is fit (trained) on a term-document matrix of term frequencies
    - the `.idf_` attribute of the `TfidfTransformer` stores the inverse document frequencies of the terms as a NumPy array

## Putting It All Together: Tf-idf
- Now that we understand how term frequency and inverse document frequency are calculated, let’s put it all together to calculate tf-idf!

- Tf-idf scores are calculated on a term-document basis
- That means there is a tf-idf score for each word, for each document
- The tf-idf score for some term t in a document d in some corpus is calculated as follows:
```
tfidf(t,d)=tf(t,d)∗idf(t,corpus)
```
    - `tf(t,d)` is the term frequency of term `t` in document `d`
    - `idf(t,corpus)` is the inverse document frequency of a term `t` across `corpus`

- We can easily calculate the tf-idf values for each term-document pair in our corpus using scikit-learn’s `TfidfVectorizer`:
```python
vectorizer = TfidfVectorizer(norm=None)
tfidf_vectorizer = vectorizer.fit_transform(corpus)
```
    - a `TfidfVectorizer` object is initialized
        - The `norm=None` keyword argument prevents scikit-learn from modifying the multiplication of term frequency and inverse document frequency
    - the `TfidfVectorizer` object is fit and transformed on the corpus of data, returning the tf-idf scores for each term-document pair

## Converting Bag-of-Words to Tf-idf
- In addition to directly calculating the tf-idf scores for a set of terms across a corpus
    - you can also convert a bag-of-words model you have already created into tf-idf scores

- Scikit-learn’s `TfidfTransformer` is up to the task of converting your bag-of-words model to tf-idf
- You begin by initializing a `TfidfTransformer` object
```python
tf_idf_transformer = TfidfTransformer(norm=False)
```
- Given a bag-of-words matrix `count_matrix`, you can now multiply the term frequencies by their inverse document frequency to get the tf-idf scores as follows:
```python
tf_idf_scores = tfidf_transformer.fit_transform(count_matrix)
```
- This is very similar to how we calculated inverse document frequency
    - except this time we are fitting and transforming the `TfidfTransformer`
    - to the term frequencies/bag-of-words vectors rather than just fitting the `TfidfTransformer` to them
