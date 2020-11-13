# Natural Language Processing
- Check out how much you’ve learned about natural language processing!
    - Natural language processing combines computer science, linguistics, and artificial intelligence to enable computers to process human languages
    - NLTK is a Python library used for NLP
    - Text preprocessing is a stage of NLP focused on cleaning and preparing text for other NLP tasks
    - Parsing is a stage of NLP concerned with breaking up text based on syntax
    - Language models are probabilistic machine models of language use for NLP comprehension tasks
        - Common models include bag-of-words, n-gram models, and neural language modeling
    - Topic modeling is the NLP process by which hidden topics are identified given a body of text
    - Text similarity is a facet of NLP concerned with semblance between instances of language
    - Language prediction is an application of NLP concerned with predicting language given preceding language
    - There are many social and ethical considerations to take into account when designing NLP tools
```python
# plagiarism classifier 
import nltk
# Levenshtein distance:
from nltk.metrics import edit_distance

# an arbitrary plagiarism classifier:
def is_plagiarized(text1, text2):
  n = 7
  if edit_distance(text1.lower(), text2.lower()) > ((len(text1) + len(text2)) / n):
    return False
  return True

doc1 = "is this plagiarized"
doc2 = "maybe it's plagiarized"

print(is_plagiarized(doc1, doc2))
```
<!-- vim-markdown-toc GFM -->

* [Intro to NLP](#intro-to-nlp)
* [Text Preprocessing](#text-preprocessing)
* [Parsing Text](#parsing-text)
* [Language Models - Bag-of-Words Approach](#language-models---bag-of-words-approach)
* [Language Models - N-Grams and NLM](#language-models---n-grams-and-nlm)
* [Topic Models](#topic-models)
* [Text Similarity](#text-similarity)
* [Language Prediction & Text Generation](#language-prediction--text-generation)
* [Advanced NLP Topics](#advanced-nlp-topics)
* [Challenges and Considerations](#challenges-and-considerations)

<!-- vim-markdown-toc -->
- Analyze text data more efficiently and effectively with natural language processing techniques
- Natural language processing developed as its own field __in parallel to data science and machine learning__
    - but there is a lot of overlap between these fields
- The goal of this unit is to analyze text data more efficiently and effectively with natural language processing techniques
- After this unit, you will be able to:
    - Understand what natural language processing is and how it can be used
    - Use __NLTK__ and __regular expressions__ to preprocess text data in preparation for various NLP tasks
    - Apply the __Bag-of-Words language model__ to your __corpus__ of text using __scikit-learn__
    - Analyze text for word importance using __tf-idf__
    - Create word embeddings to map words in relation to one another

## Intro to NLP
- Look at the technologies around us:
    - Spellcheck and autocorrect
    - Auto-generated video captions
    - Virtual assistants like Amazon’s Alexa
    - Autocomplete
    - Your news site’s suggested articles
- What do they have in common?
- All of these handy technologies exist because of natural language processing! Also known as NLP, the field is at the intersection of linguistics, artificial intelligence, and computer science
- The goal? Enabling computers to interpret, analyze, and approximate the generation of human languages (like English or Spanish)

- NLP got its start around 1950 with Alan Turing’s test for artificial intelligence
    - evaluating whether a computer can use language to fool humans into believing it’s human

- But approximating human speech is only one of a wide range of applications for NLP!
    - Applications from detecting spam emails
    - or bias in tweets to improving accessibility for people with disabilities
        - all rely heavily on natural language processing techniques

- NLP can be conducted in several programming languages
- However, Python has some of the most extensive open-source NLP libraries, including the Natural Language Toolkit or NLTK
- Because of this, you’ll be using Python to get your first taste of NLP

## Text Preprocessing
>    "You never know what you have... until you clean your data."
~ Unknown (or possibly made up)

- Cleaning and preparation are crucial for many tasks, and NLP is no exception
- __Text preprocessing__ is usually the first step you’ll take when faced with an NLP task

- Without preprocessing, your computer interprets `"the"`, `"The"`, and `"<p>The"` as entirely different words
- There is a LOT you can do here, depending on the formatting you need
- Lucky for you, Regex and NLTK will do most of it for you! Common tasks include:
    - __Noise removal__ — stripping text of formatting (e.g., HTML tags)
    - __Tokenization__ — breaking text into individual words
    - __Normalization__ — cleaning text data in any other way:
        - __Stemming__ is a blunt axe to chop off word prefixes and suffixes
            - “booing” and “booed” become “boo”, but “sing” may become “s” and “sung” would remain “sung”
        - __Lemmatization__ is a scalpel to bring words down to their root forms
            - For example, NLTK’s savvy lemmatizer knows “am” and “are” are related to “be”
        - Other common tasks include lowercasing, [stopwords](https://en.wikipedia.org/wiki/Stop_word) removal, spelling correction, etc.
- code challenge :
```python
 # regex for removing punctuation!
import re
# nltk preprocessing magic
import nltk
from nltk.tokenize import word_tokenize
from nltk.stem import PorterStemmer
from nltk.stem import WordNetLemmatizer
# grabbing a part of speech function:
from part_of_speech import get_part_of_speech

text = "So many squids are jumping out of suitcases these days that you can barely go anywhere without seeing one burst forth from a tightly packed valise. I went to the dentist the other day, and sure enough I saw an angry one jump out of my dentist's bag within minutes of arriving. She hardly even noticed."

cleaned = re.sub('\W+', ' ', text)
tokenized = word_tokenize(cleaned)

stemmer = PorterStemmer()
stemmed = [stemmer.stem(token) for token in tokenized]

## -- CHANGE these -- ##
lemmatizer = None
lemmatized = []

print("Stemmed text:")
print(stemmed)
print("\nLemmatized text:")
print(lemmatized) 
```
1. We used NLTK’s PorterStemmer to normalize the text — run the code to see how it does. (It may take a few seconds for the code to run.)
2. In the output terminal you’ll see our program counts "go" and "went" as different words! Also, what’s up with "mani" and "hardli"? A lemmatizer will fix this. Let’s do it.
    - Where lemmatizer is defined, replace None with WordNetLemmatizer().
    - Where we defined lemmatized, replace the empty list with a list comprehension that uses lemmatizer to lemmatize() each token in tokenized.

(Don’t know Python that well? No problem. Just check the hints for help throughout the lesson.)
```hint
lemmatized = [lemmatizer.lemmatize(token) for token in tokenized]
```
3. Why are the lemmatized verbs like "went" still conjugated? By default lemmatize() treats every word as a noun
    - Give lemmatize() a second argument: get_part_of_speech(token). This will tell our lemmatizer what part of speech the word is.

Run your code again to see the result!
- code answer
```python
# regex for removing punctuation!
import re
# nltk preprocessing magic
import nltk
from nltk.tokenize import word_tokenize
from nltk.stem import PorterStemmer
from nltk.stem import WordNetLemmatizer
# grabbing a part of speech function:
from part_of_speech import get_part_of_speech

text = "So many squids are jumping out of suitcases these days that you can barely go anywhere without seeing one burst forth from a tightly packed valise. I went to the dentist the other day, and sure enough I saw an angry one jump out of my dentist's bag within minutes of arriving. She hardly even noticed."

cleaned = re.sub('\W+', ' ', text)
tokenized = word_tokenize(cleaned)

stemmer = PorterStemmer()
stemmed = [stemmer.stem(token) for token in tokenized]

## -- CHANGE these -- ##
lemmatizer = WordNetLemmatizer()
lemmatized = [lemmatizer.lemmatize(token, get_part_of_speech(token)) for token in tokenized]

print("Stemmed text:")
print(stemmed)
print("\nLemmatized text:")
print(lemmatized)
```

## Parsing Text
- You now have a preprocessed, clean list of words
- Now what? It may be helpful to know how the words relate to each other and the underlying syntax (grammar)
- __Parsing__ is a stage of NLP concerned with segmenting text based on syntax

- You probably do not want to be doing any parsing by hand and NLTK has a few tricks up its sleeve to help you out:
    - __Part-of-speech tagging (POS tagging)__ identifies parts of speech (verbs, nouns, adjectives, etc.)
        - NLTK can do it faster (and maybe more accurately) than your grammar teacher
    - __Named entity recognition (NER)__ helps identify the proper nouns (e.g., “Natalia” or “Berlin”) in a text
        - This can be a clue as to the topic of the text and NLTK captures many for you
    - __Dependency grammar__ trees help you understand the relationship between the words in a sentence
        - It can be a tedious task for a human, so the Python library spaCy is at your service, even if it isn’t always perfect

- In English we leave a lot of ambiguity, so syntax can be tough, even for a computer program
- Take a look at the following sentence:
> I saw a cow under a tree with binoculars.

- Do I have the binoculars? Does the cow have binoculars? Does the tree have binoculars?

- __Regex parsing__, using Python’s re library, allows for a bit more nuance
    - When coupled with POS tagging, you can identify specific phrase chunks
    - On its own, it can find you addresses, emails, and many other common patterns within large chunks of text

- code challenge :
```python
import spacy
from nltk import Tree
from squids import squids_text

dependency_parser = spacy.load('en')

parsed_squids = dependency_parser(squids_text)

# Assign my_sentence a new value:
my_sentence = "Your sentence goes here!"
my_parsed_sentence = dependency_parser(my_sentence)

def to_nltk_tree(node):
  if node.n_lefts + node.n_rights > 0:
    parsed_child_nodes = [to_nltk_tree(child) for child in node.children]
    return Tree(node.orth_, parsed_child_nodes)
  else:
    return node.orth_

for sent in parsed_squids.sents:
  to_nltk_tree(sent.root).pretty_print()
  
for sent in my_parsed_sentence.sents:
 to_nltk_tree(sent.root).pretty_print()
```

1.  Run the code to see the silly squid sentences parsed into dependency trees visually!
2.  Change `my_sentence` to a sentence of your choosing and run the code again to see it parsed out as a tree!

## Language Models - Bag-of-Words Approach
- How can we help a machine make sense of a bunch of word tokens?
    - We can help computers make predictions about language by training a language model on a corpus (a bunch of example text)

- Language models are __probabilistic computer models__ of language
    - We __build__ and use these __models__ to figure out the likelihood that a given sound, letter, word, or phrase will be used
    - Once a __model__ has been __trained__, it can be tested out on new texts

- One of the most common language models is the __unigram model__, a statistical language model commonly known as __bag-of-words__
- As its name suggests, __bag-of-words__ does not have much order to its chaos! What it does have is a tally count of each instance for each word
- Consider the following text example:
> The squids jumped out of the suitcases
- Provided some initial preprocessing, bag-of-words would result in a mapping like:
```python
{"the": 2, "squid": 1, "jump": 1, "out": 1, "of": 1, "suitcase": 1}
```
- Now look at this sentence and mapping: “Why are your suitcases full of jumping squids?”
```python
{"why": 1, "be": 1, "your": 1, "suitcase": 1, "full": 1, "of": 1, "jump": 1, "squid": 1}
```
- You can see how even with different word order and sentence structures, “jump,” “squid,” and “suitcase” are shared topics between the two examples
- __Bag-of-words__ can be an excellent way of looking at language when you want to __make predictions__ concerning topic or sentiment of a text
- When grammar and word order are irrelevant, this is probably a good model to use

- code challenge :
```python
# importing regex and nltk
import re, nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from nltk.stem import WordNetLemmatizer
# importing Counter to get word counts for bag of words
from collections import Counter
# importing a passage from Through the Looking Glass
from looking_glass import looking_glass_text
# importing part-of-speech function for lemmatization
from part_of_speech import get_part_of_speech

# Change text to another string:
text = looking_glass_text

cleaned = re.sub('\W+', ' ', text).lower()
tokenized = word_tokenize(cleaned)

stop_words = stopwords.words('english')
filtered = [word for word in tokenized if word not in stop_words]

normalizer = WordNetLemmatizer()
normalized = [normalizer.lemmatize(token, get_part_of_speech(token)) for token in filtered]
# Comment out the print statement below
print(normalized)

# Define bag_of_looking_glass_words & print:
```
1. We’ve turned a passage from Through the Looking Glass by Lewis Carroll into a list of words (aside from stopwords, which we’ve removed) using nltk preprocessing
    - Run your code to see the full list.
2.  Now let’s turn this list into a bag-of-words using `Counter()`!
    - Comment out the print statement and set `bag_of_looking_glass_words` equal to a call of `Counter()` on `normalized`
    - Print `bag_of_looking_glass_words`
    - What are the most common words?
- hint: bag_of_looking_glass_words = Counter(normalized)
1.  Try changing text to another string of your choosing and see what happens!

```python
# importing regex and nltk
import re, nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from nltk.stem import WordNetLemmatizer
# importing Counter to get word counts for bag of words
from collections import Counter
# importing a passage from Through the Looking Glass
from looking_glass import looking_glass_text
# importing part-of-speech function for lemmatization
from part_of_speech import get_part_of_speech

# Change text to another string:
text = "Such an excellent bag of words and an excellent word 'bags'."

cleaned = re.sub('\W+', ' ', text).lower()
tokenized = word_tokenize(cleaned)

stop_words = stopwords.words('english')
filtered = [word for word in tokenized if word not in stop_words]

normalizer = WordNetLemmatizer()
normalized = [normalizer.lemmatize(token, get_part_of_speech(token)) for token in filtered]
# Comment out the print statement below
#print(normalized)

# Define bag_of_looking_glass_words & print:
bag_of_looking_glass_words = Counter(normalized)
print(bag_of_looking_glass_words)
```

## Language Models - N-Grams and NLM
- For parsing entire phrases or conducting language prediction, you will want to use a model that pays attention to each word’s neighbors
- Unlike bag-of-words
    - the __n-gram__ model considers a sequence of some number (n) units
    - and calculates the probability of each unit in a body of language
    - given the preceding sequence of length n
- Because of this, n-gram probabilities with larger n values can be impressive at language prediction

- Take a look at our revised squid example:
    - “The squids jumped out of the suitcases. The squids were furious.”

- A bigram model (where n is 2) might give us the following count frequencies:
```
{('', 'the'): 2, ('the', 'squids'): 2, ('squids', 'jumped'): 1, ('jumped', 'out'): 1, ('out', 'of'): 1, ('of', 'the'): 1, ('the', 'suitcases'): 1, ('suitcases', ''): 1, ('squids', 'were'): 1, ('were', 'furious'): 1, ('furious', ''): 1}
```
- There are a couple problems with the __n gram__ model:
    - How can your language model make sense of the sentence “The cat fell asleep in the mailbox”
        - if it’s never seen the word “mailbox” before?
        - During training, your model will probably come across test words
        - that it has never encountered before (this issue also pertains to bag of words)
        - A tactic known as language smoothing can help adjust probabilities for unknown words, but it isn’t always ideal
    - For a model that more accurately predicts human language patterns
        - you want __n (your sequence length)__ to be as large as possible
        - That way, you will have more natural sounding language, right?
        - Well, as the sequence length grows, the number of examples of each sequence within your training corpus shrinks
        - With too few examples, you won’t have enough data to make many predictions
- Enter __neural language models (NLM)!__
    - Much recent work within NLP has involved __developing and training neural networks__
        - to approximate the approach our human brains take towards language
    - This __deep learning__ approach allows computers a much more adaptive tack to processing human language
- code challenge : 
```python
import nltk, re
from nltk.tokenize import word_tokenize
# importing ngrams module from nltk
from nltk.util import ngrams
from collections import Counter
from looking_glass import looking_glass_full_text

cleaned = re.sub('\W+', ' ', looking_glass_full_text).lower()
tokenized = word_tokenize(cleaned)

# Change the n value to 2:
looking_glass_bigrams = ngrams(tokenized, 1)
looking_glass_bigrams_frequency = Counter(looking_glass_bigrams)

# Change the n value to 3:
looking_glass_trigrams = ngrams(tokenized, 1)
looking_glass_trigrams_frequency = Counter(looking_glass_trigrams)

# Change the n value to a number greater than 3:
looking_glass_ngrams = ngrams(tokenized, 1)
looking_glass_ngrams_frequency = Counter(looking_glass_ngrams)

print("Looking Glass Bigrams:")
print(looking_glass_bigrams_frequency.most_common(10))

print("\nLooking Glass Trigrams:")
print(looking_glass_trigrams_frequency.most_common(10))

print("\nLooking Glass n-grams:")
print(looking_glass_ngrams_frequency.most_common(10))
```
1. If you run the code, you’ll see the 10 most commonly used words in Through the Looking Glass parsed with NLTK’s ngrams module 
    - if you’re thinking this looks like a bag of words, that’s because it is one!
2.  What do you think the most common phrases in the text are? Let’s find out…
    - Where `looking_glass_bigrams` is defined, change the second argument to `2` to see bigrams
    - Change `n` to `3` for `looking_glass_trigrams` to see trigrams
- hint : The ngrams() function takes two arguments: the text you want to use and the n value
1.  Change n to a number greater than 3 for looking_glass_ngrams
    - Try increasing the number
    - At what n are you just getting lines from poems repeated in the text?
    - This is where there may be too few examples of each sequence
        - within your training corpus to make any helpful predictions
- code answer:
```python
import nltk, re
from nltk.tokenize import word_tokenize
# importing ngrams module from nltk
from nltk.util import ngrams
from collections import Counter
from looking_glass import looking_glass_full_text

cleaned = re.sub('\W+', ' ', looking_glass_full_text).lower()
tokenized = word_tokenize(cleaned)

# Change the n value to 2:
looking_glass_bigrams = ngrams(tokenized, 2)
looking_glass_bigrams_frequency = Counter(looking_glass_bigrams)

# Change the n value to 3:
looking_glass_trigrams = ngrams(tokenized, 3)
looking_glass_trigrams_frequency = Counter(looking_glass_trigrams)

# Change the n value to a number greater than 3:
looking_glass_ngrams = ngrams(tokenized, 7)
looking_glass_ngrams_frequency = Counter(looking_glass_ngrams)

print("Looking Glass Bigrams:")
print(looking_glass_bigrams_frequency.most_common(10))

print("\nLooking Glass Trigrams:")
print(looking_glass_trigrams_frequency.most_common(10))

print("\nLooking Glass n-grams:")
print(looking_glass_ngrams_frequency.most_common(10))
```

## Topic Models
- We’ve touched on the idea of finding topics within a body of language
- But what if the text is long and the topics aren’t obvious?

- __Topic modeling__ is an area of NLP dedicated to uncovering latent, or hidden, topics within a body of language
- For example, one Codecademy curriculum developer [used topic modeling to discover patterns within Taylor Swift songs](https://news.codecademy.com/taylor-swift-lyrics-machine-learning/) related to love and heartbreak over time

- A common technique is to
    - deprioritize the most common words
    - and prioritize less frequently used terms
        - as topics in a process known as __term frequency-inverse document frequency (tf-idf)__
- Say what?! This may sound counter-intuitive at first
    - Why would you want to give more priority to less-used words?
    - Well, when you’re working with a lot of text
    - it makes a bit of sense if you don’t want your topics filled with words like “the” and “is”
- The Python libraries `gensim` and `sklearn` have modules to handle tf-idf

- Whether you
    - use your plain bag of words (which will give you __term frequency__)
    - or run it through __tf-idf__
- the next step in your topic modeling journey is often __latent Dirichlet allocation (LDA)__
    - LDA is a statistical model that takes your documents
    - and determines which words keep popping up together in the same contexts (i.e., documents)
    - We’ll use `sklearn` to tackle this for us.

- If you have any interest in visualizing your newly minted topics
    - __word2vec__ is a great technique to have up your sleeve
        - __word2vec__ can map out your topic model results spatially as vectors
        - so that similarly used words are closer together
    - In the case of a language sample consisting of
    - “The squids jumped out of the suitcases. The squids were furious. Why are your suitcases full of jumping squids?”
    - we might see that “suitcase”, “jump”, and “squid” were words used within similar contexts
    - This word-to-vector mapping is known as a __word embedding__

- code challenge
```python
import nltk, re
from sherlock_holmes import bohemia_ch1, bohemia_ch2, bohemia_ch3, boscombe_ch1, boscombe_ch2, boscombe_ch3
from preprocessing import preprocess_text
from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer
from sklearn.decomposition import LatentDirichletAllocation

# preparing the text
corpus = [bohemia_ch1, bohemia_ch2, bohemia_ch3, boscombe_ch1, boscombe_ch2, boscombe_ch3]
preprocessed_corpus = [preprocess_text(chapter) for chapter in corpus]

# Update stop_list:
stop_list = []
# filtering topics for stop words
def filter_out_stop_words(corpus):
  no_stops_corpus = []
  for chapter in corpus:
    no_stops_chapter = " ".join([word for word in chapter.split(" ") if word not in stop_list])
    no_stops_corpus.append(no_stops_chapter)
  return no_stops_corpus
filtered_for_stops = filter_out_stop_words(preprocessed_corpus)

# creating the bag of words model
bag_of_words_creator = CountVectorizer()
bag_of_words = bag_of_words_creator.fit_transform(filtered_for_stops)

# creating the tf-idf model
tfidf_creator = TfidfVectorizer(min_df = 0.2)
tfidf = tfidf_creator.fit_transform(preprocessed_corpus)

# creating the bag of words LDA model
lda_bag_of_words_creator = LatentDirichletAllocation(learning_method='online', n_components=10)
lda_bag_of_words = lda_bag_of_words_creator.fit_transform(bag_of_words)

# creating the tf-idf LDA model
lda_tfidf_creator = LatentDirichletAllocation(learning_method='online', n_components=10)
lda_tfidf = lda_tfidf_creator.fit_transform(tfidf)

print("~~~ Topics found by bag of words LDA ~~~")
for topic_id, topic in enumerate(lda_bag_of_words_creator.components_):
  message = "Topic #{}: ".format(topic_id + 1)
  message += " ".join([bag_of_words_creator.get_feature_names()[i] for i in topic.argsort()[:-5 :-1]])
  print(message)

print("\n\n~~~ Topics found by tf-idf LDA ~~~")
for topic_id, topic in enumerate(lda_tfidf_creator.components_):
  message = "Topic #{}: ".format(topic_id + 1)
  message += " ".join([tfidf_creator.get_feature_names()[i] for i in topic.argsort()[:-5 :-1]])
  print(message)
```
1. Check out how the bag of words model and tf-idf models stack up when faced with a new Sherlock Holmes text!
    - Run the code as is to see what topics they uncover…
2.  Tf-idf has some interesting findings, but the regular bag of words is full of words that tell us very little about the topic of the texts!
- Let’s fix this
    - Add some words to `stop_list` that don’t tell you much about the topic and then run your code again
    - Do this until you have at least 10 words in `stop_list` so that the bag of words LDA model has some interesting topics
```python
import nltk, re
from sherlock_holmes import bohemia_ch1, bohemia_ch2, bohemia_ch3, boscombe_ch1, boscombe_ch2, boscombe_ch3
from preprocessing import preprocess_text
from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer
from sklearn.decomposition import LatentDirichletAllocation

# preparing the text
corpus = [bohemia_ch1, bohemia_ch2, bohemia_ch3, boscombe_ch1, boscombe_ch2, boscombe_ch3]
preprocessed_corpus = [preprocess_text(chapter) for chapter in corpus]

# Update stop_list:
stop_list = ["say", "see", "holmes", "shall", "say", "man", "upon", "know", "quite", "one", "well", "could", "would", "take", "may", "think", "come", "go", "little", "must", "look"]
# filtering topics for stop words
def filter_out_stop_words(corpus):
  no_stops_corpus = []
  for chapter in corpus:
    no_stops_chapter = " ".join([word for word in chapter.split(" ") if word not in stop_list])
    no_stops_corpus.append(no_stops_chapter)
  return no_stops_corpus
filtered_for_stops = filter_out_stop_words(preprocessed_corpus)

# creating the bag of words model
bag_of_words_creator = CountVectorizer()
bag_of_words = bag_of_words_creator.fit_transform(filtered_for_stops)

# creating the tf-idf model
tfidf_creator = TfidfVectorizer(min_df = 0.2)
tfidf = tfidf_creator.fit_transform(preprocessed_corpus)

# creating the bag of words LDA model
lda_bag_of_words_creator = LatentDirichletAllocation(learning_method='online', n_components=10)
lda_bag_of_words = lda_bag_of_words_creator.fit_transform(bag_of_words)

# creating the tf-idf LDA model
lda_tfidf_creator = LatentDirichletAllocation(learning_method='online', n_components=10)
lda_tfidf = lda_tfidf_creator.fit_transform(tfidf)

print("~~~ Topics found by bag of words LDA ~~~")
for topic_id, topic in enumerate(lda_bag_of_words_creator.components_):
  message = "Topic #{}: ".format(topic_id + 1)
  message += " ".join([bag_of_words_creator.get_feature_names()[i] for i in topic.argsort()[:-5 :-1]])
  print(message)

print("\n\n~~~ Topics found by tf-idf LDA ~~~")
for topic_id, topic in enumerate(lda_tfidf_creator.components_):
  message = "Topic #{}: ".format(topic_id + 1)
  message += " ".join([tfidf_creator.get_feature_names()[i] for i in topic.argsort()[:-5 :-1]])
  print(message)
```

## Text Similarity
- Most of us have a good autocorrect story
- Our phone’s messenger quietly swaps one letter for another as we type
    - and suddenly the meaning of our message has changed (to our horror or pleasure)
- However, addressing __text similarity__ 
    - including spelling correction 
    - is a major challenge within natural language processing

- Addressing word similarity and misspelling for spellcheck or autocorrect
    - often involves considering the __Levenshtein distance__
    - or minimal edit distance between two words
- The distance is calculated through the minimum number of
    - insertions
    - deletions
    - and substitutions
        - that would need to occur for one word to become another
- For example, turning “bees” into “beans” would require
    - one substitution (“a” for “e”)
    - and one insertion (“n”)
    - so the Levenshtein distance would be two.

- __Phonetic similarity__ is also a major challenge within speech recognition
    - English-speaking humans can easily tell from context whether someone said “euthanasia” or “youth in Asia”
        - but it’s a far more challenging task for a machine!
    - More advanced autocorrect and spelling correction technology additionally considers
        - key distance on a keyboard
        - and phonetic similarity (how much two words or phrases sound the same)

- It’s also helpful to find out if texts are the same to guard against plagiarism
    - which we can identify through __lexical similarity__ (the degree to which texts use the same vocabulary and phrases)
    - Meanwhile, __semantic similarity__ (the degree to which documents contain similar meaning or topics)
        - is useful when you want to find (or recommend) an article or book similar to one you recently finished
- code challenge :
```python
import nltk
# NLTK has a built-in function
# to check Levenshtein distance:
from nltk.metrics import edit_distance

def print_levenshtein(string1, string2):
  print("The Levenshtein distance from '{0}' to '{1}' is {2}!".format(string1, string2, edit_distance(string1, string2)))

# Check the distance between
# any two words here!
print_levenshtein("fart", "target")

# Assign passing strings here:
three_away_from_code = ""

two_away_from_chunk = ""

print_levenshtein("code", three_away_from_code)
print_levenshtein("chunk", two_away_from_chunk)
```
1. Assign the variable `three_away_from_code` a word with a Levenshtein distance of `3` from “code”
    - Assign `two_away_from_chunk` a word with a Levenshtein distance of `2` from “chunk”
- hint : Each insertion, deletion, or substitution counts as an edit distance of `1`
```python
import nltk
# NLTK has a built-in function
# to check Levenshtein distance:
from nltk.metrics import edit_distance

def print_levenshtein(string1, string2):
  print("The Levenshtein distance from '{0}' to '{1}' is {2}!".format(string1, string2, edit_distance(string1, string2)))

# Check the distance between
# any two words here!
print_levenshtein("fart", "target")

# Assign passing strings here:
three_away_from_code = "cloud"

two_away_from_chunk = "dunk"

print_levenshtein("code", three_away_from_code)
print_levenshtein("chunk", two_away_from_chunk)
```
## Language Prediction & Text Generation
- How does your favorite search engine complete your search queries?
- How does your phone’s keyboard know what you want to type next?
- __Language prediction__ is an application of NLP concerned with predicting text given preceding text
- Autosuggest, autocomplete, and suggested replies are common forms of language prediction.

- Your first step to language prediction is picking a language model
- Bag of words alone is generally not a great model for language prediction
    - no matter what the preceding word was
    - you will just get one of the most commonly used words from your training corpus

- If you go the n-gram route
    - you will most likely rely on __Markov chains__
    - to predict the statistical likelihood of each following word (or character)
    - based on the training corpus
- __Markov chains__ are memory-less and make statistical predictions based entirely on the current n-gram on hand

- For example, let’s take a sentence beginning, “I ate so many grilled cheese”
- Using a trigram model (where n is 3)
    - a Markov chain would predict the following word as “sandwiches”
        - based on the number of times the sequence “grilled cheese sandwiches” has appeared in the training data
        - out of all the times “grilled cheese” has appeared in the training data

- A more advanced approach, using a __neural language model__, is the __Long Short Term Memory (LSTM)__ model
- LSTM uses __deep learning__ with a network of artificial “cells” that manage memory
    - making them better suited for text prediction than __traditional neural networks__
- code challenge :
```python
script.py
import nltk, re, random
from nltk.tokenize import word_tokenize
from collections import defaultdict, deque
from document1 import training_doc1
from document2 import training_doc2
from document3 import training_doc3

class MarkovChain:
  def __init__(self):
    self.lookup_dict = defaultdict(list)
    self._seeded = False
    self.__seed_me()

  def __seed_me(self, rand_seed=None):
    if self._seeded is not True:
      try:
        if rand_seed is not None:
          random.seed(rand_seed)
        else:
          random.seed()
        self._seeded = True
      except NotImplementedError:
        self._seeded = False
    
  def add_document(self, str):
    preprocessed_list = self._preprocess(str)
    pairs = self.__generate_tuple_keys(preprocessed_list)
    for pair in pairs:
      self.lookup_dict[pair[0]].append(pair[1])
  
  def _preprocess(self, str):
    cleaned = re.sub(r'\W+', ' ', str).lower()
    tokenized = word_tokenize(cleaned)
    return tokenized

  def __generate_tuple_keys(self, data):
    if len(data) < 1:
      return

    for i in range(len(data) - 1):
      yield [ data[i], data[i + 1] ]
      
  def generate_text(self, max_length=50):
    context = deque()
    output = []
    if len(self.lookup_dict) > 0:
      self.__seed_me(rand_seed=len(self.lookup_dict))
      chain_head = [list(self.lookup_dict)[0]]
      context.extend(chain_head)
      
      while len(output) < (max_length - 1):
        next_choices = self.lookup_dict[context[-1]]
        if len(next_choices) > 0:
          next_word = random.choice(next_choices)
          context.append(next_word)
          output.append(context.popleft())
        else:
          break
      output.extend(list(context))
    return " ".join(output)

my_markov = MarkovChain()
my_markov.add_document(training_doc1)
my_markov.add_document(training_doc2)
my_markov.add_document(training_doc3)
generated_text = my_markov.generate_text()
print(generated_text)
```
```document1
document1.py document2.py document3.py
raining_doc1 = """

"""
```

1.  Add three short stories by your favorite author
- or the lyrics to three songs by your favorite artist
- to document1.py, document2.py, and document3.py
- Then run script.py to see a short example of text prediction
- Does it look like something by your favorite author or artist?
- If you accidentally close one of the files
- just click the file folder in the top left corner of the code editor to find the file and re-open it

## Advanced NLP Topics
- Believe it or not, you’ve just scratched the surface of natural language processing
- There are a slew of advanced topics and applications of NLP, many of which rely on __deep learning__ and __neural networks__
    - [Naive Bayes classifiers](https://www.codecademy.com/learn/paths/machine-learning) are supervised machine learning algorithms that leverage a probabilistic theorem to make predictions and classifications
        - They are widely used for
            - sentiment analysis (determining whether a given block of language expresses negative or positive feelings)
            - and spam filtering
    - We’ve made enormous gains in __machine translation__
        - but even the most advanced translation software using neural networks and LSTM still has far to go in accurately translating between languages
    - Some of the most life-altering applications of NLP are focused on improving __language accessibility__ for people with disabilities
        - __Text-to-speech functionality__ and __speech recognition__ have improved rapidly
            - thanks to __neural language models__, making digital spaces far more accessible places
    - NLP can also be used to detect bias in writing and speech
        - Feel like a political candidate, book, or news source is biased but can’t put your finger on exactly how?
        - Natural language processing can help you identify the language at issue.
- code challenge :
```python
from reviews import counter, training_counts
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

# Add your review:
review = ""
review_counts = counter.transform([review])

classifier = MultinomialNB()
training_labels = [0] * 1000 + [1] * 1000

classifier.fit(training_counts, training_labels)
  
neg = (classifier.predict_proba(review_counts)[0][0] * 100).round()
pos = (classifier.predict_proba(review_counts)[0][1] * 100).round()

if pos > 50:
  print("Thank you for your positive review!")
elif neg > 50:
  print("We're sorry this hasn't been the best possible lesson for you! We're always looking to improve.")
else:
  print("Naive Bayes cannot determine if this is negative or positive. Thank you or we're sorry?")

  
print("\nAccording to our trained Naive Bayes classifier, the probability that your review was negative was {0}% and the probability it was positive was {1}%.".format(neg, pos))
```

1.  Assign `review` a string with a brief review of this lesson so far
- Next, run your code. Is the Naive Bayes Classifier accurately classifying your review?

## Challenges and Considerations
- As you’ve seen, there are a vast array of applications for NLP
- However, as they say, “with great language processing comes great responsibility” (or something along those lines)
- When working with NLP, we have several important considerations to take into account:
    - Different NLP tasks may be more or less difficult in different languages
        - Because so many NLP tools are built by and for English speakers, these tools may lag behind in processing other languages
        - The tools may also be programmed with cultural and linguistic biases specific to English speakers
    - What if your Amazon Alexa could only understand wealthy men from coastal areas of the United States?
        - English itself is not a homogeneous body
        - English varies by person, by dialect, and by many sociolinguistic factors
        - When we build and train NLP tools, are we only building them for one type of English speaker?
    - You can have the best intentions and still inadvertently program a bigoted tool
        - While NLP can limit bias, it can also propagate bias
        - As an NLP developer, it’s important to consider biases, both within your code and within the training corpus
        - A machine will learn the same biases you teach it, whether intentionally or unintentionally
    - As you become someone who builds tools with natural language processing
        - it’s vital to take into account your users’ privacy
        - There are many powerful NLP tools that come head-to-head with privacy concerns
        - Who is collecting your data? How much data is being collected and what do those companies plan to do with your data?
```python
from reviews import counter, training_counts
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

# Add your review:
review = "It was fun!"
review_counts = counter.transform([review])

classifier = MultinomialNB()
training_labels = [0] * 1000 + [1] * 1000

classifier.fit(training_counts, training_labels)

neg = (classifier.predict_proba(review_counts)[0][0] * 100).round()
pos = (classifier.predict_proba(review_counts)[0][1] * 100).round()

if pos > 50:
  print("Naive Bayes classifies this as positive.")
elif neg > 50:
  print("Naive Bayes classifies this as negative.")
else:
  print("Naive Bayes cannot determine if this is negative or positive.")
  

print("\nAccording to our trained Naive Bayes classifier, the probability that your review was negative was {0}% and the probability it was positive was {1}%.".format(neg, pos))
```

1.  Test out different slang on the Naive Bayes Classifier! What happens when you use the word “lit” to mean “wonderful” or “fun”?
- Is the sentiment prediction accurate? Test out different slang
