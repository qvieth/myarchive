# datacamp machine learning scientist
- COME BACK STATS COURSE OF DATACAMP
- supervised :
    - classify : target values is discrete
    - regression : target values is continuous
- target varibles = response variables
- train = `.fit(features)`
- `predict(target_variable)`
- train/test split -> - measuring performance metric :
    - classfication - accuracy
- `.reshape()` : Getting the feature and target variable arrays into the right format for scikit-learn

```
sns.heatmap(df.corr(), square=True, cmap='RdYlGn')
```

## regrssion
- line : y=ax+b
- define an error functions (aka cost or lost function)for any given line
- choose the line that minimizes the error function
- ordinary least squares (OLS) : minimize sum of squares of residuals
- regularization I: lasso
- regularization II : ridge
- metrics : confusion matrix - precision - recall - F1score - threshholds
- logistic regrssion -> for classification problem(discrete)
- tune hyperparemter -> improve performance
- preprocessing data

# unsupervised learning
- k-means :
    - inertia
