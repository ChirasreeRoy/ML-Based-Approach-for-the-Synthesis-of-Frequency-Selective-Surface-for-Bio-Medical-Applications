Code Snippet for Decision Tree

import pandas as pd
from sklearn.tree import DecisionTreeRegressor

#Load dataset
data = pd.read_csv("D:\VS code\FSS_project\FSS\Dataset_ML.csv")
#Split into features and labels
X = data[['Length', 'Width', 'Breadth']]
y = data.iloc[:, 3:] # select all columns starting from the 4th column

#Train decision tree model 
clf = DecisionTreeRegressor() 
clf.fit(X, y)
length = float(input("Enter the length: "))
width = float(input("Enter the width: ")) 
breadth = float(input("Enter the Breadth: "))

#Predict S21 values for a new input 
new_input = [[length, width, breadth]] 
prediction = clf.predict(new_input)
print(prediction)

#Create a new DataFrame with the predicted S21 values 
s21_pred = pd.DataFrame(prediction, columns=y.columns)

#Write the DataFrame to an Excel file 
s21_pred.to_excel("DT_pred.xlsx", index=False)
