# Visual EDA
> In the video, Hugo used the `scatter_matrix()` for visual EDA

- However, you may have noticed in the previous exercise that __all the features__ in this dataset are __binary__ : either 0 or 1
- So a different type of plot would be more useful here, such as Seaborn's `countplot`

```python
plt.figure()
sns.countplot(x='education', hue='party', data=df, palette='RdBu')
plt.xticks([0,1], ['No', 'Yes'])
plt.show()
```

- In `sns.countplot()`, we specify
    - the x-axis data to be `'education'`
    - and hue to be `'party'`
    - Recall that `'party'` is also our __target variable__

- So the resulting plot shows the difference in voting behavior __between the two parties__ for the `'education'` bill
    - with each party colored differently
- We manually specified the color to be `'RdBu'`
    - Republican : red
    - Democratic : blue

- It seems like Democrats voted resoundingly against this bill, compared to Republicans
- __This is the kind of information that our machine learning model will seek to learn__
    - when we try to predict party affiliation solely based on voting behavior

- In the IPython Shell, explore the voting behavior further by generating __countplots__ for the `'satellite'` and `'missile'` bills
    - and answer the following question
        - Of these two bills
        - for which ones do Democrats vote resoundingly in favor of compared to Republicans?
        - Be sure to begin your plotting statements
            - for each figure with `plt.figure()` so that a new figure will be set up
- Otherwise, your plots will be overlayed onto the same figure
