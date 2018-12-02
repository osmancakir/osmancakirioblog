---
title: "Linear Regression Ecommerce Consultation"
author: "Osman Cakir"
date: 2018-12-02
description: "Consulting an Ecommerce Company on optimizing their development efforts "
type: technical_note
draft: false
---
Assume you just signed a contract with an E-commerce company based in Munich. Customers can buy clothes either on a mobile app or a website for the clothes they want. The company has also a styling store where customers can come and have sessions with a personal stylist.

The company is trying to decide whether to focus their efforts on their mobile app experience or their website. Your job is to help them figure it out.

The customer data presented here is fake. So don’t worry about the emails or credit card numbers.

Let’s start!


## Importing the necessary libraries

** set %matplotlib inline to see the graphs on the notebook**


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

## Get the Data

Get the Data

The data is given to us by the company in a csv format. It has Customer info, such as Email, Address, and their color Avatar. It also has numerical value columns:

Avg. Session Length: Average session of in-store style advice sessions.
Time on App: Average time spent on App in minutes.
Time on Website: Average time spent on Website in minutes.
Length of Membership: How many years the customer has been a member.


```python
customers = pd.read_csv("Ecommerce Customers")
```

**Getting to know the data:**


```python
customers.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Email</th>
      <th>Address</th>
      <th>Avatar</th>
      <th>Avg. Session Length</th>
      <th>Time on App</th>
      <th>Time on Website</th>
      <th>Length of Membership</th>
      <th>Yearly Amount Spent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>mstephenson@fernandez.com</td>
      <td>835 Frank Tunnel\nWrightmouth, MI 82180-9605</td>
      <td>Violet</td>
      <td>34.497268</td>
      <td>12.655651</td>
      <td>39.577668</td>
      <td>4.082621</td>
      <td>587.951054</td>
    </tr>
    <tr>
      <th>1</th>
      <td>hduke@hotmail.com</td>
      <td>4547 Archer Common\nDiazchester, CA 06566-8576</td>
      <td>DarkGreen</td>
      <td>31.926272</td>
      <td>11.109461</td>
      <td>37.268959</td>
      <td>2.664034</td>
      <td>392.204933</td>
    </tr>
    <tr>
      <th>2</th>
      <td>pallen@yahoo.com</td>
      <td>24645 Valerie Unions Suite 582\nCobbborough, D...</td>
      <td>Bisque</td>
      <td>33.000915</td>
      <td>11.330278</td>
      <td>37.110597</td>
      <td>4.104543</td>
      <td>487.547505</td>
    </tr>
    <tr>
      <th>3</th>
      <td>riverarebecca@gmail.com</td>
      <td>1414 David Throughway\nPort Jason, OH 22070-1220</td>
      <td>SaddleBrown</td>
      <td>34.305557</td>
      <td>13.717514</td>
      <td>36.721283</td>
      <td>3.120179</td>
      <td>581.852344</td>
    </tr>
    <tr>
      <th>4</th>
      <td>mstephens@davidson-herman.com</td>
      <td>14023 Rodriguez Passage\nPort Jacobville, PR 3...</td>
      <td>MediumAquaMarine</td>
      <td>33.330673</td>
      <td>12.795189</td>
      <td>37.536653</td>
      <td>4.446308</td>
      <td>599.406092</td>
    </tr>
  </tbody>
</table>
</div>




```python
customers.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg. Session Length</th>
      <th>Time on App</th>
      <th>Time on Website</th>
      <th>Length of Membership</th>
      <th>Yearly Amount Spent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>500.000000</td>
      <td>500.000000</td>
      <td>500.000000</td>
      <td>500.000000</td>
      <td>500.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>33.053194</td>
      <td>12.052488</td>
      <td>37.060445</td>
      <td>3.533462</td>
      <td>499.314038</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.992563</td>
      <td>0.994216</td>
      <td>1.010489</td>
      <td>0.999278</td>
      <td>79.314782</td>
    </tr>
    <tr>
      <th>min</th>
      <td>29.532429</td>
      <td>8.508152</td>
      <td>33.913847</td>
      <td>0.269901</td>
      <td>256.670582</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>32.341822</td>
      <td>11.388153</td>
      <td>36.349257</td>
      <td>2.930450</td>
      <td>445.038277</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>33.082008</td>
      <td>11.983231</td>
      <td>37.069367</td>
      <td>3.533975</td>
      <td>498.887875</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>33.711985</td>
      <td>12.753850</td>
      <td>37.716432</td>
      <td>4.126502</td>
      <td>549.313828</td>
    </tr>
    <tr>
      <th>max</th>
      <td>36.139662</td>
      <td>15.126994</td>
      <td>40.005182</td>
      <td>6.922689</td>
      <td>765.518462</td>
    </tr>
  </tbody>
</table>
</div>




```python
customers.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 500 entries, 0 to 499
    Data columns (total 8 columns):
    Email                   500 non-null object
    Address                 500 non-null object
    Avatar                  500 non-null object
    Avg. Session Length     500 non-null float64
    Time on App             500 non-null float64
    Time on Website         500 non-null float64
    Length of Membership    500 non-null float64
    Yearly Amount Spent     500 non-null float64
    dtypes: float64(5), object(3)
    memory usage: 31.3+ KB


## Exploratory Data Analysis

**Let's explore the data!**
___

**Compare the Time on Website and Yearly Amount Spent columns to see whether the correlation make sense.**


```python
sns.set_palette("GnBu_d")
sns.set_style('whitegrid')
```


```python
# More time on site, more money spent.
sns.jointplot(x='Time on Website',y='Yearly Amount Spent',data=customers)
```




    <seaborn.axisgrid.JointGrid at 0x120bfcc88>




![png](linear_regression_ecommerce_consultation_12_1.png)


** Do the same analysis but with the Time on App column instead. **


```python
sns.jointplot(x='Time on App',y='Yearly Amount Spent',data=customers)
```




    <seaborn.axisgrid.JointGrid at 0x132db5908>




![png](linear_regression_ecommerce_consultation_14_1.png)


** Use jointplot to create a 2D hex bin plot comparing Time on App and Length of Membership.**

What about Time Spent on App vs. Lenght of Membership?


```python
sns.jointplot(x='Time on App',y='Length of Membership',kind='hex',data=customers)
```




    <seaborn.axisgrid.JointGrid at 0x130edac88>




![png](linear_regression_ecommerce_consultation_17_1.png)


Ok, maybe it is better to see the whole picture by considering the relationships across the entire data set.


```python
sns.pairplot(customers)
```




    <seaborn.axisgrid.PairGrid at 0x132fb3da0>




![png](linear_regression_ecommerce_consultation_19_1.png)


**Based off this plot, Length of Membership looks to be the most correlated feature with Yearly Amount Spent. Let’s create a linear model to explore it deeper.**


```python
# Length of Membership 
```


```python
sns.lmplot(x='Length of Membership',y='Yearly Amount Spent',data=customers)
```




    <seaborn.axisgrid.FacetGrid at 0x13538d0b8>




![png](linear_regression_ecommerce_consultation_22_1.png)


## Training and Testing Data

**Now that we’ve completed the EDA we can move on to the actual analysis.**

Set features of the customers and the label: “Yearly Amount Spent” column.
Split the data into training and testing sets.


```python
y = customers['Yearly Amount Spent']
```


```python
X = customers[['Avg. Session Length', 'Time on App','Time on Website', 'Length of Membership']]
```


```python
from sklearn.model_selection import train_test_split
```


```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=101)
```

## Training the Model


```python
from sklearn.linear_model import LinearRegression
```


```python
lm = LinearRegression()
```


```python
lm.fit(X_train,y_train)
```




    LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)



**Now, it is time to see our coefficients:**


```python
# The coefficients
print('Coefficients: \n', lm.coef_)
```

    Coefficients: 
     [ 25.98154972  38.59015875   0.19040528  61.27909654]


## Predicting Test Data

Let’s see how we perform on the test data and evaluate our model.


```python
predictions = lm.predict( X_test)
```


```python
plt.scatter(y_test,predictions)
plt.xlabel('Y Test')
plt.ylabel('Predicted Y')
```




    <matplotlib.text.Text at 0x135546320>




![png](linear_regression_ecommerce_consultation_36_1.png)


## Evaluating the Model

We’ll evaluate our model performance by calculating the residual sum of squares and the explained variance score (R^2).

**Calculate the Mean Absolute Error, Mean Squared Error, and the Root Mean Squared Error.**


```python
# calculate these metrics by hand!
from sklearn import metrics

print('MAE:', metrics.mean_absolute_error(y_test, predictions))
print('MSE:', metrics.mean_squared_error(y_test, predictions))
print('RMSE:', np.sqrt(metrics.mean_squared_error(y_test, predictions)))
```

    MAE: 7.22814865343
    MSE: 79.813051651
    RMSE: 8.93381506698


## Residuals

Seems like we have a very good model with a good fit. Let’s quickly explore the residuals to make sure everything was okay with our data. **We want to make sure the residuals looks normally distributed.**



```python
sns.distplot((y_test-predictions),bins=50);
```


![png](linear_regression_ecommerce_consultation_40_0.png)


## Concluding Remarks


Our original question was, should the company focus its efforts on mobile app or website development? Or maybe this decision doesn’t even really matter, and Membership Time is what is really important. The coefficients can give us an idea.

** Recreate the dataframe below. **


```python
coeffecients = pd.DataFrame(lm.coef_,X.columns)
coeffecients.columns = ['Coeffecient']
coeffecients
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Coeffecient</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Avg. Session Length</th>
      <td>25.981550</td>
    </tr>
    <tr>
      <th>Time on App</th>
      <td>38.590159</td>
    </tr>
    <tr>
      <th>Time on Website</th>
      <td>0.190405</td>
    </tr>
    <tr>
      <th>Length of Membership</th>
      <td>61.279097</td>
    </tr>
  </tbody>
</table>
</div>



**Interpreting the coefficients:**

Holding all other features fixed:
A 1 unit increase in Avg. Session Length is associated with an increase of 25.98 total dollars spent.
A 1 unit increase in Time on App is associated with an increase of 38.59 total dollars spent.
A 1 unit increase in Time on Website is associated with an increase of 0.19 total dollars spent.
A 1 unit increase in Length of Membership is associated with an increase of 61.27 total dollars spent.

Now there are two different approaches to this result. As the data scientist, our suggestion would depend on what does the management wants. If the company wants its website to catch up to the performance of the mobile app, then it should focus on that. Or the company can focus on the development of the mobile app since it is already performing well.

## Well Done
