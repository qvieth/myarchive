# Introduction: Data Acquisition
- __Data acquisition__ (__data mining__) is the step of the __Data Science Life Cycle__
- understand __Data Science Life Cycle__ first
<!-- vim-markdown-toc GFM -->

* [data mining methods :](#data-mining-methods-)
    * [Public & Private Data](#public--private-data)
        * [Public Data](#public-data)
        * [Private Data](#private-data)
    * [Web Scraping](#web-scraping)
    * [APIs](#apis)
    * [Manual Data Acquisition](#manual-data-acquisition)
    * [BI tools](#bi-tools)

<!-- vim-markdown-toc -->
- After this unit, you will be able to:
    - Recognize __which channels__ of data acquisition are best suited to different situations
    - Query data from relational databases using __SQL__
    - Integrate SQL queries into Python programs
    - Conduct __web scraping__ with BeautifulSoup

# data mining methods :
- __business understanding__ comes before __data mining__
- __Methods__ that we will cover :
    - Public & Private Data
    - Web Scraping
    - APIs
    - Manual Data Acquisition
    - BI Tools

## Public & Private Data
- One of the most accessible methods for __obtaining data__ is through __publicly__ or __privately__ stored datasets found __online__

### Public Data
- There are several __open source datasets__ that are __hosted online__
- that allow you to freely download data collected by others
- These public sources of data are often suitable for __small to medium sized__ machine learning projects, concept validation, and research purposes
- Some of the most commonly visited are:
    - GitHub
    - Kaggle
    - KDnuggets
    - UCI Machine Learning Repository
    - US Government’s Open Data
    - Five Thirty Eight
    - Amazon Web Services
- It is relatively easy to access a __dataset__ from one of these sites with Python
- You can download it directly to your local machine or use the __Pandas__ library to __download__ directly from a URL
- __Pandas(Panel Data)__ is one of the most commonly used Python libraries because it is so efficient for tasks such as __data cleaning__ and __pre-processing__:
```python
# Import pandas with alias
import pandas as pd

# Assign the dataset url as a variable
url = "https://raw.githubusercontent.com/shrikant-temburwar/Iris-Dataset/master/Iris.csv"

# Define the column names of dataset as a list
columns = ["sepal_length", "sepal_width", "petal_length", "petal_width", "class"]

# Use read_csv to read in data as a pandas dataframe
df = pd.read_csv(url, names=columns)

# Check head of dataframe
print(df.head())
```
### Private Data
- There are also a number of __private datasets__ that businesses curate themselves and are under ownership of the company
- For instance, Netflix’s __database of user preferences__ powers their immense __recommendation systems__
- There are also services that allow you to __purchase datasets__ such as data markets like __Data & Sons__
- or __crowd-sourcing marketplaces__ such as __Amazon’s Mechanical Turks__
- where one can outsource their data acquisition needs like data validation and research to survey participation
- Often we will find usage of private data within a __large production scale__ setting
- Pros:
    - Time: Readily available datasets that can quickly move a project to the next phase of the __Data Science Life Cycle__
    - Cost: __Public datasets__ : cut costs of collecting data down to zero.
- Cons:
    - Messy: Data can often come in forms that require intensive cleaning and modification.
    - Cost: __Private services__ : high costs in acquiring data.

## Web Scraping
- __Web scraping__ can be __one of the most potent methods__ of __data acquisition__ when used effectively
- Web scraping at its core is the act of __extracting__ or __copying information__ directly from a __website__
- This data can then be stored within a __dataframe__ or __spreadsheet__ and used in the same manner as any __other dataset__
- There are __2 general methods__ for __web scraping__ :
    - __manually scrape__ the data from a web page
    - employ a __web crawler__ or __bot__ that automates the process of extracting data from a website

- Python has useful libraries that allow you to implement both methods of web scraping
- some of the most commonly used are __BeautifulSoup, Selenium, and Scrapy__
- Web scraping is best used when the data you need is not available as a public or private dataset, but present on a web page
- We typically employ web scraping techniques to acquire data for small to medium sized projects
- but rarely in production as this can raise ownership and copyright issues
- A unique aspect of web scraping is that, as it involves referencing a website’s source code
- one should have some familiarity with the language that the website is written in
- For example :
    - when viewing the code for Codecademy’s home page we can see it is written in HTML
    - and if we would like to scrape information from the site we would need to understand the architecture and various tags of the site

- Let’s try a simple implementation of web scraping in Python to demonstrate it’s efficiency for acquiring data
- Note that we scraped Codecademy’s home page in September 2020. The homepage might look different now!
```python
# Import libraries 
import pandas as pd
from bs4 import BeautifulSoup
import requests

# Assign URL to variable
url = "https://www.codecademy.com/"

# Send request to download the data from URL
response = requests.request("GET", url)

# Create BeautifulSoup object
# Use HTML parser to parse the page's text
data = BeautifulSoup(response.text, 'html.parser')

# Print the first header of the page
print(data.html.h1)

# Instantiate list to append some content
content = []

# Use BeautifulSoup's find_all method to find all paragraph tags
words = data.find_all('p')

# Iterate through all paragraph tags
# append text to list with for loop
for word in words:
    content.append(word.text)

# Check content
print(content)

# Create dataframe of content with pandas DataFrame method
df = pd.DataFrame(content, columns= ['Text'])

# Check scraped dataframe
print(df)
```
```
Index 	Text
0 	Black Lives Matter. Find Resources or Show Your Support
1 	By signing up for Codecademy, you agree to Codecademy’s Terms of Service & Privacy Policy.
2 	No need to worry, we’ll help you make sense of it all.
3 	From building websites to analyzing data, the choice is yours. Not sure where to start? We’ll point you in the right direction.
4 	No matter your experience level, you’ll be writing real, working code in minutes.
5 	Your code is tested as soon as you submit it, so you always know if you’re on the right track.
6 	Apply your learning with real-world projects and test your knowledge with tailor-made quizzes.
7 	Coding skills have never been more in-demand. Learn everything you need to take your career to the next level.
```
- It’s important to note that web scraping is still considered to be in a gray area when it comes to ethics and legalities
- Typically companies prefer not to be scraped as it can lead to web infrastructure costs
- As such you may find barriers to web scraping
- like CAPTCHA
- For these reasons when conducting web scraping ensure it is done in a way that does not negatively impact the website being scraped
- Pros:
    - Versatile: Highly adaptable method for acquiring data from the internet.
    - Scalable: Distributed bots can be coordinated to retrieve large quantities of data.
- Cons:
    - Language Barrier: Multiple languages are involved when scraping and require a knowledge of languages not typically used for data science.
    - Legality: Excessive or improper web-scraping can be illegal, disrupt a website’s functionality, and lead to your IP address being black listed from the site

## APIs
- APIs is achieved in the form of an HTTP Request/Response Cycle
    - where a client(you) __sends a request__ to a website’s server for data through an __API call__
    - The server then searches __within its databases__ for the particular data requested and __responds back__ to the client either with the data
- Suppose we would like to access recent weather data of the US for analysis
- there are several weather related APIs such as __OpenWeatherMap, AccuWeather, and National Weather Service API__ that we can acquire the data from
- If we used OpenWeatherMap for example
    - we would create an account on their site to __receive an API key__
    - and subscribe for their free tier subscription which allows for up to 60 API calls per minute
- With that we would be able to use Python to access OpenWeatherMaps’s forecast data and analyze it
- Pros:
    - User & Site Friendly: APIs allow security and management of resources for sites that data is being requested from
    - Scalable: API’s can allow for various amounts of data to be requested, up to production scale volumes
- Cons:
    - Limited: Some functions or data may not be accessed via an API
    - Cost: Some API calls can be quite expensive, leading to limitations of certain functions and projects

## Manual Data Acquisition
- when the data we need is __not present on the internet__ or __able to be outsourced__
- and there are many tools available to do so :
    - __Google Forms__ : a free way to create surveys to acquire data related to a __particular population__ , downloaded in CSV file
    - __Google Surveys__ : a paid service that allows a wider range of respondents and gives you more control in targeting audience
    - __Nvidia’s Jetson Nano__ and __Arduino’s Uno boards__ : create __sensor systems__ that can __harvest data__ from local environment
    - __machine learning models__ : acquire even more complex data about the environment

- Pros
    - Bespoke: Data acquired manually can be made to address all of the business objective’s needs, and can need little to no cleaning to be effective.
    - Community: Manually acquired data can be useful in advancing the fields of data science and machine learning, and be further explored by others.
- Cons
    - Time: Manually acquired data can take more time than other methods, especially when dealing with large datasets.
    - Cost: Some services and devices used to manually acquire data can be expensive and can be limiting for certain projects.

## BI tools
- methods we have covered can be used in business context, as long as they __bring some value__ to the organization
- businesses need to utilize data acquisition to __uncover__ actionable __insights__
- that improve __internal processes__ or the __services or goods__ that they offer
- and it is true that __creative data acquisition__ is the source of success for many of the largest corporations
- The data that these corporations maintain are so complex, they are referred to as __Big Data__
- Data of this __magnitude__ needs __tools__ that can manage it, some most popular : 
    - Google Analytics
    - Tableau
    - Looker
- __Structured Query Language (SQL)__ is another __essential tool__ for the scale of data that businesses collect
