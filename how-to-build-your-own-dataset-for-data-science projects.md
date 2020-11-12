# [How to build your own dataset for data science projects](https://towardsdatascience.com/how-to-build-your-own-dataset-for-data-science-projects-7f4ad0429de4)

<!-- vim-markdown-toc GFM -->

* [Introduction To Data Types in Data Science](#introduction-to-data-types-in-data-science)
    * [Numerical Data](#numerical-data)
        * [Discrete Data](#discrete-data)
        * [Continuous Data](#continuous-data)
        * [Interval Data](#interval-data)
        * [Ratio Data](#ratio-data)
    * [Categorical Data](#categorical-data)
        * [Nominal Data](#nominal-data)
        * [Ordinal Data](#ordinal-data)
* [other types of data that can be use in data science](#other-types-of-data-that-can-be-use-in-data-science)
    * [Image](#image)
        * [BYOD](#byod)
        * [web scraping](#web-scraping)
    * [Audio](#audio)
    * [Video](#video)
    * [Text](#text)

<!-- vim-markdown-toc -->

- When I started my Data Science journey
- it was the Chicago Crime Dataset or Wine Quality or Walmart sales — the common project datasets that I could get my hands on
- Next, when I did __IBM Data Science Professional Certification__, I learned about __APIs__ and __access to robust datasets__, but that comes with a price!

- For a beginner data scientist, the dilemma would surely be — what to do after learning the theory?
- Sure there are plenty of datasets available
- but the free ones rarely give you a __pragmatic insight__ into solving actual problems
- or sometimes they are too small to use for __deep learning applications__

- You want to : 
    - begin with a project
    - construct a model 
    - run for the results
    - actively looking for a dataset?

- Why not build your own dataset?
- The __first option__ has to be __web scraping__, that goes without saying
- So, in this story, I will start by introducing __data types__ and __accepted data formats__ for Data Science projects and next
- I will illustrate a quirky way of scrapping Google for your exclusive dataset (a project in itself!)
- NOTE: This requires working knowledge of Python and understanding of reading and writing different file formats in Python.

## Introduction To Data Types in Data Science
### Numerical Data
#### Discrete Data
- Discrete data has __distinct__ and __separate values__
- Example: number of heads in 100 coin flips
- Discrete data comes into picture only if it can take on definite values
- This type of data cannot be __measured__ but can be __counted__

#### Continuous Data
- Continuous Data represents data that __can be measured__, has units and therefore can be involved in math computations
- Examples: age, height, weight, salary
- Continuous data can be described using intervals on the real number line

#### Interval Data
- Interval values represent __ordered__ units that have the same difference __between two intervals__
- Therefore we speak of interval data when we have a variable that contains numeric values that are ordered and we know the exact differences between those values
- Example: The difference between 60 and 50 degrees is a measurable 10 degrees, as is the difference between 80 and 70 degrees
#### Ratio Data
- Ratio values are also ordered units that have the same difference
- Ratio values are the same as interval values, with the difference that they do have an absolute zero
- Good examples are height, weight, length etc.
- Ratio data can be added, subtracted, multiplied, divided, have measures of central tendency — mean, median, mode, standard deviation and coefficient of variation

### Categorical Data
- Categorical data represents __characteristics__ of the data
- It can be anything like a person’s gender, language, income ≥50K or <50K etc
- Categorical data can also take on numerical values like 1 for female and 0 for male

#### Nominal Data
- Nominal values represent __discrete__ and __unordered__ units and are used to label variables that have __no quantitative value__
- When I say unordered, that means nominal data that has no order
- Examples:
    - Colors — red, green, yellow, blue, orange
    - Seasons — Fall, Winter, Summer, Spring
    - Type of bank accounts — Checking, Savings
    - States — Chicago, New York, California, Michigan
- Therefore, even if you change the order of values for nominal data, the meaning remains unchanged
- A type of nominal data that contains only two categories (male and female) is called dichotomous
#### Ordinal Data
- Ordinal values represent discrete and ordered units
- It is therefore nearly the same as nominal data, except that it’s ordering matters
- Examples:
    - Letter Grade — A, B, C, D, F
    - Apparel size — XS, S, M, L , XL, XXL
    - Rankings — 1,2,3
    - Education — Elementary, High School, Bachelors, Master
- Because of orderliness, ordinal data is usually used when dealing with non-numeric features like happiness, customer satisfaction and similar

## other types of data that can be use in data science
### Image
#### BYOD
- I am sure each of us must have been a hoarder of images
- Puppies, cats, actors, exotic travel destinations. Anything works here 😄
- In a lifetime, you will run out of projects to do
- Problem Statements:
    - Identifies the breed of a pup
    - Detect mood of the pup
- Dig up your hard drive for all those puppy images you’ve had in your lifetime
- Begin with OpenCV, Python Imaging Library or matplotlib libraries to read the images
- Make sure to keep all the images in one file format: jpeg or png
- Once the images have been read, you can proceed as with any other model you’d build with a Googled dataset
- Divide as 70%–30% training and test dataset, use some for validation, you got your dataset!
- Ever thought of that?

#### web scraping
- Believe it or not, downloading a bunch of images is easy using google-image-downloader in Python
```
pip install googleimagedownloader
```
- Next, make sure you have Google Chrome
- Get the version of Chromedriver that corresponds to the version of Google Chrome that you are running 
- and use the following command line code to download images in batches from Google Chrome
```
$ googleimagesdownload -k "puppies" -s medium -l 200 -o dataset/train -i puppies -cd ~/chromedriver
```
- This command will scrape 200 images from Google Images using the keyword ‘puppies’
- It will output those images to: dataset/train/puppies/
- The -cd argument points to the location of the ‘chromedriver’ executable file we downloaded earlier
- Sound good?

### Audio
- Taylor Swift, Arijit Singh, Black Pink, BTS, J Balvin — choose your favorites from around the globe
- Problem Statement: Identify the language from an audio file
- For building your own audio dataset, collect songs (audio files) at one place
- The only thing tedious about this would be collecting enough number of songs to build a model on training data, validate it and test it
- Secondly, importing mp3 files in Python can be a task
- I would recommend starting by converting the mp3 files to WAV for ease
- You can follow the documentation on how to read and write WAV files in Python to kickstart your work
- The wave module provides a convenient interface to the WAV sound format
- One more way to have diverse audio is to source your files from soundcloud
- There are tools on the internet that you can use to download audio from Soundcloud in mp3
- That’s a long route for sure but once you have audio files, follow what you would ideally do with audio file projects in Python

### Video
- Guess any number of Play Date edits would work! 😛
- Problem Statements:
    - Identify if a person is wearing a mask
    - Identify if the social distancing measures are followed — distance between people
    - Home security system — is the person known?

- With video, the data science projects would mostly be facial recognition ones and given the extraordinary times
- many of the projects similar to above problem statements are bring built by data scientists from over the world
- To build a video dataset, your source can be your family videos, you pranking your siblings, basically anything with human figures and that moves
- OpenCV again would be your hero
- OpenCV provides a very simple interface to read, write and display a video
- The first step to reading a video file would be to create a VideoCapture object
- The video format accepted is mp4 and I believe it won’t require us format conversions unless shot on iPhones
- Next, you can apply the facial recognition algorithms to solve the problems

### Text
- Next up is acquiring data from your Fitbit or your iWatch
- In one of my blogs, I had a comment from a reader on this idea as a Data Science project and here I am writing about how to make a dataset of your own!
- If you use any wearables, that could make for an interesting dataset 
- companies that compile with General Data Protection Regulations should send over all your personal data in nicely (ish) formatted csv files
- And the next thing you know is analyzing your very own data!

- I’ve recently downloaded two years worth of my fitness data from Fitbit
- You can follow the process to export your Fitbit account data from here

- Thank you for reading! I hope you enjoyed the article
- Do let me know what datasets are you looking forward to building and working over the summer in your Data Science journey.

Happy Data Tenting!

Disclaimer: The views expressed in this article are my own and do not represent a strict outlook.
