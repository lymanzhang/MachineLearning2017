import numpy as np
import pandas as pd

# Load the dataset
X = pd.read_csv('titanic_data.csv')
# Limit to categorical data
X = X.select_dtypes(include=[object])

from sklearn.preprocessing import LabelEncoder
from sklearn.preprocessing import OneHotEncoder

le = LabelEncoder()

for feature in X:
    X[feature] = le.fit_transform(X[feature])

ohe = OneHotEncoder()

xt = ohe.fit_transform(X)

onehotlabels = xt

print onehotlabels.toarray()

    输出结果如下：  

        [[ 0.  0.  0. ...,  0.  0.  1.]
         [ 0.  0.  0. ...,  1.  0.  0.]
         [ 0.  0.  0. ...,  0.  0.  1.]
         ..., 
        [ 0.  0.  0. ...,  0.  0.  1.]
         [ 0.  0.  0. ...,  1.  0.  0.]
         [ 0.  0.  0. ...,  0.  1.  0.]]
        Your one hot encoded data has the following shape:  (891, 1726)