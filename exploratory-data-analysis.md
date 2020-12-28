# exploratory data analysis - supervised learning with scikit-learn

```python
import matlotlib.pyplot as plt
_ = plt.hist
_ = plt.xlabel('x')
_ = plt.ylabel('y')
```

- always label your axis
- The "square root rule" is a commonly-used rule of thumb for choosing number of bins :
    - choose the __number of bins__ to be the __square root__ of the __number of samples__


# Exploratory Data Analysis?
- Exploratory Data Analysis involves two fundamental steps :
    - Data Analysis (Data Pre processing, Cleaning and Manipulation)
    - Data Visualisation (Visualise relationships in data using different types of plots)

- Many people associate data science with fields like machine learning and artificial intelligence
- but EDA often takes up a larger percentage a data scientist’s day-to-day work! This is because:
    - Before fitting any sort of machine learning __model__
        - it is important to inspect a dataset and get to know it!
        - Often the best way to improve a __model__ is to spend more time thinking about the data itself
        - EDA can help you make decisions about what data to include, exclude, or transform
    - Sometimes a data scientist does not plan to fit a predictive model to their data at all
        - Instead, their goal may be to inspect and analyze existing data to answer questions like:
            - What proportion of visitors to a website made a purchase?
            - Or, how has the purchase rate changed over the last 6 months?
> EDA generally happens before __model fitting__!

### Techniques 
- The particular __graphical techniques__ employed in EDA are often quite simple, consisting of various techniques of:
    - Plotting the raw data such as :
        - data traces
        - histograms
        - bihistograms
        - probability plots
        - lag plots
        - block plots
        - and Youden plots
    - Plotting simple statistics such as :
        - mean plots
        - standard deviation plots
        - box plots
        - and main effects plots of the raw data
    - __Positioning__ such plots so as to maximize our natural pattern-recognition abilities
        - such as using multiple plots per page
