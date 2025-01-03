# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
```
1. Load the dataset from a CSV file and separate the features and target variable, encoding any categorical variables as needed.
2.Scale the features using a standard scaler to normalize the data.
3.Initialize model parameters (theta) and add an intercept term to the feature set.
4.Train the linear regression model using gradient descent by iterating through a specified number of iterations to minimize the cost function.
5.Make predictions on new data by transforming it using the same scaling and encoding applied to the training data. 
```
## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: MITHUN S
RegisterNumber: 24901037
*/
```
```
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler

def linear_regression(X1, y, learning_rate=0.01, num_iters=1000):
    X = np.c_[np.ones(len(X1)), X1]
    theta = np.zeros(X.shape[1]).reshape(-1, 1)
    for _ in range(num_iters):
        predictions = (X).dot(theta).reshape(-1, 1)
        errors = (predictions - y).reshape(-1, 1)
        theta -= learning_rate * (1 / len(X1)) * X.T.dot(errors)
    return theta

data = pd.read_csv('50_Startups.csv', header=None)
X = (data.iloc[1:, :-2].values)
X1 = X.astype(float)
scaler = StandardScaler()
y = (data.iloc[1:, -1].values).reshape(-1, 1)
X1_Scaled = scaler.fit_transform(X1)
Y1_Scaled = scaler.fit_transform(y)
theta = linear_regression(X1_Scaled, Y1_Scaled)

new_data = np.array([165349.2, 136897.8, 471784.1]).reshape(-1, 1)
new_Scaled = scaler.fit_transform(new_data)
prediction = np.dot(np.append(1, new_Scaled), theta)
prediction = prediction.reshape(-1, 1)
pre = scaler.inverse_transform(prediction)

print(f"Predicted value: {pre}")
```

## Output:
![image](https://github.com/user-attachments/assets/7f789801-c296-4e77-b244-8c0a80deb7d6)
![image](https://github.com/user-attachments/assets/9f305b2d-e3e2-407a-a010-1521dcf8724a)



## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
