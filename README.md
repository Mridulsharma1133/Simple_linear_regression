# Simple Linear Regression

1. Simple Linear Regression is used to find a best fit line.
(image.png)

2. Best fit line basically drawn to minimize error between predicted output and actual output.

3. Line represents : y = mx + b where m is a slope and b is y-intecept.

4. To find the value of m and b . We use formula:
    (image-1.png)
  (image-2.png)

5. So, here we applied this mathematical computation and created our own simple linear regression model from scratch in python and we tried to compare it with sklearn.linearRegression

6. We took a simple data from kaggle dataset which consists of 30 rows and 3 col. We took years of experience as input and salary as output.

7. We perform data selection with the help of pandas library using iloc function to store input and output

import pandas as pd
import numpy as np
data = pd.read_csv("Salary_dataset.csv")
#input
x = data.iloc[:,1].values
#output
y = data.iloc[:,2].values

8. Then, we write our own simple linear class and created our own simple regression model using same mathematical formula.

class Simple_Lin_Reg:
    def __init__(self):
        self.m = None
        self.b = None
      
    def fit(self, X_train, y_train):
        num = 0
        den = 0
        for i in range(X_train.shape[0]):
            num = num + (X_train[i] - X_train.mean()) * (y_train[i] - y_train.mean())
            den = den + (X_train[i] - X_train.mean()) ** 2
        self.m = num/den
        self.b = y_train.mean() - (self.m * X_train.mean())
        print(self.m)
        print(self.b)
    
    def predict(self, X_test):
        print(X_test)
        return self.m * X_test + self.b


 model = Simple_Lin_Reg()

10. First, we trained our model using train,test split from sklearn 
X_train, X_test, y_train, y_test = train_test_split(x, y, test_size = 0.3, random_state = 2)

11. Then fit the model with trained data using fit function in our class
model.fit(X_train, y_train)

12. Then predicted the results using predict function in our class
print(model.predict(X_test))

13. Then we performed linear regression using sklearn as well.
from sklearn.linear_model import LinearRegression
m = LinearRegression()
m.fit(X_train.reshape(-1, 1), y_train.reshape(-1, 1))
m.predict(X_test.reshape(-1,1))




### Program.



