# Ex.No: 13 Learning – Use Supervised Learning  
### DATE: 22.04.2024                                                                           
### REGISTER NUMBER : 212221040015
### AIM: 
To write a program to train the classifier for Diabetes .
###  Algorithm:
Step 1: Import packages 
Step 2: Get the data 
Step 3: Split the data 
Step 4: Scale the data 
Step 5: Instantiate model 
Step 6: Create a function for gradio 
Step 7: Print Result

### Program:
```
import numpy as np
import pandas as pd
pip install gradio
pip install typing-extensions --upgrade
pip install --upgrade typing
pip install typing-extensions --upgrade
import gradio as gr
data = pd.read_csv('/content/diabetes.csv')
data.head()
print(data.columns)
x = data.drop(['Outcome'], axis=1)
y = data['Outcome']
print(x[:5])
#split data
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test= train_test_split(x,y)

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
x_train_scaled = scaler.fit_transform(x_train)
x_test_scaled = scaler.fit_transform(x_test)

from sklearn.neural_network import MLPClassifier
model = MLPClassifier(max_iter=1000, alpha=1)
model.fit(x_train, y_train)
print("Model Accuracy on training set:", model.score(x_train, y_train))
print("Model Accuracy on Test Set:", model.score(x_test, y_test))

def diabetes(Pregnancies, Glucose, Blood_Pressure, SkinThickness, Insulin, BMI,Diabetes_Pedigree, Age):
    x = np.array([Pregnancies,Glucose,Blood_Pressure,SkinThickness,Insulin,BMI,Diabetes_Pedigree,Age])
    prediction = model.predict(x.reshape(1, -1))
    if(prediction==0):
      return "NO"
    else:
      return "YES"

outputs = gr.Textbox()
app = gr.Interface(fn=diabetes, inputs=['number','number','number','number','number','number','number','number'], outputs=outputs,description="Detection of Diabeties")
app.launch(share=True)

```

### Output:
# 1. Dataset
![image](https://github.com/Vijayananthperumal22/AI_Lab_2023-24/assets/107705127/3467b06e-8fce-4c48-b097-b86dd45beac5)
# 2. Accuracy
![image](https://github.com/Vijayananthperumal22/AI_Lab_2023-24/assets/107705127/e26327cc-1d4a-4802-bc39-162f2d56e423)
# 3.Output Result
![image](https://github.com/Vijayananthperumal22/AI_Lab_2023-24/assets/107705127/0e4b6278-3fb5-434b-b875-af6a847c3b22)


### Result:
Thus the system was trained successfully and the prediction was carried out.
