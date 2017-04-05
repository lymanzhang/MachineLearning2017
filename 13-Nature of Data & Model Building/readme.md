    在这个部分，主要涉及到了OneHotEncoder的使用  
    这里涉及到sklearn中的一个函数OneHotEncoder，顺便扩展到容易混淆的另一个函数LabelEncoder。  

    OneHotEncoder  
http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html  

    LabelEncoder  
http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html  

    相关知识链接：  
Beyond One-Hot: an exploration of categorical variables  
http://www.kdnuggets.com/2015/12/beyond-one-hot-exploration-categorical-variables.html

    函数OneHotEncoder使用困惑  
http://discussions.youdaxue.com/t/one-hot-encoding-onehotencoder/6141  

```
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

```
    输出结果如下：  
```
[[ 0.  0.  0. ...,  0.  0.  1.]
[ 0.  0.  0. ...,  1.  0.  0.]
[ 0.  0.  0. ...,  0.  0.  1.]
..., 
[ 0.  0.  0. ...,  0.  0.  1.]
[ 0.  0.  0. ...,  1.  0.  0.]
[ 0.  0.  0. ...,  0.  1.  0.]]
Your one hot encoded data has the following shape:  (891, 1726)
```
