# Ex.No: 13 Learning – Use Supervised Learning  
### DATE: 25-10-2025                                                                           
### REGISTER NUMBER : 212223040007
### AIM: 
To write a program to train a Random Forest Regressor model for Chennai Weather Prediction using supervised learning, in order to predict the maximum temperature based on previous day’s temperature and rainfall data.
###  Algorithm:
1. **Import** the necessary libraries such as `pandas`, `sklearn`, `seaborn`, and `matplotlib`.  
2. **Load** the dataset `chennai-temp-rains.csv` using `pandas`.  
3. **Preprocess** the data — clean missing values, convert data types, and sort by date.  
4. **Create** lag features (`TempMax_lag1`, `TempMin_lag1`, `Rain_lag1`) for previous day’s data.  
5. **Split** the dataset into training and testing sets using `train_test_split()`.  
6. **Train** the model using **Random Forest Regressor** on the training data.  
7. **Predict** the maximum temperature using the test data.  
8. **Evaluate** the model using **Mean Squared Error (MSE)** and **R² Score**.  
9. **Visualize** the actual vs predicted values and temperature distribution using plots.  
### Program:
```
# Program to implement a Random Forest model for Chennai Weather Prediction
# Developed by: ADITYA S
# RegisterNumber: 212223040007

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score
import seaborn as sns
import matplotlib.pyplot as plt

data = pd.read_csv("chennai-temp-rains.csv")

data.rename(columns={'Temp Max':'TempMax','Temp Min':'TempMin','Rain':'Rain','Date':'Date'}, inplace=True)
data.replace('-----', None, inplace=True)

data['Date'] = pd.to_datetime(data['Date'], format='%d-%m-%Y', errors='coerce')
data['TempMax'] = pd.to_numeric(data['TempMax'], errors='coerce')
data['TempMin'] = pd.to_numeric(data['TempMin'], errors='coerce')
data['Rain'] = pd.to_numeric(data['Rain'], errors='coerce')

data = data.dropna(subset=['Date','TempMax','TempMin','Rain'])
data = data.sort_values('Date').reset_index(drop=True)

data['TempMax_lag1'] = data['TempMax'].shift(1)
data['TempMin_lag1'] = data['TempMin'].shift(1)
data['Rain_lag1'] = data['Rain'].shift(1)
data = data.dropna()

X = data[['TempMax_lag1','TempMin_lag1','Rain_lag1']]
y = data['TempMax']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, shuffle=False, random_state=42)

model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print("Mean Squared Error:", mse)
print("R2 Score:", r2)

plt.figure(figsize=(8,5))
sns.scatterplot(x=y_test, y=y_pred, alpha=0.7, color='green')
plt.xlabel("Actual TempMax")
plt.ylabel("Predicted TempMax")
plt.title("Actual vs Predicted Temperature using Random Forest")
plt.grid(True)
plt.show()

plt.figure(figsize=(8,5))
sns.kdeplot(y_test, label='Actual', fill=True)
sns.kdeplot(y_pred, label='Predicted', fill=True, color='red')
plt.title("Temperature Distribution Comparison (Random Forest)")
plt.legend()
plt.show()
```

### Output:
<img width="1268" height="575" alt="image" src="https://github.com/user-attachments/assets/6c1184f2-91be-4c88-b29f-289c0297e348" />
<img width="1249" height="561" alt="image" src="https://github.com/user-attachments/assets/14246f3b-7f93-46be-8002-ce7c545ee96c" />


### Result:
Thus the system was trained successfully and the prediction was carried out.
