import streamlit as st  
import pandas as pd  
from sklearn.linear_model import LinearRegression  
  
# Training data  
data = {  
    "water": [20, 30, 40, 50, 60, 70, 80],  
    "height": [5, 7, 9, 12, 14, 16, 19]  
}  
  
df = pd.DataFrame(data)  
  
# Train model  
X = df[["water"]]  
y = df["height"]  
  
model = LinearRegression()  
model.fit(X, y)  
  
# Website  
st.title("🌱 Plant Growth Predictor")  
  
st.write("Predict plant height based on daily water intake.")  
  
water = st.number_input(  
    "Enter water amount (ml/day)",  
    min_value=0.0,  
    value=50.0  
)  
  
if st.button("Predict"):  
    prediction = model.predict(  
        pd.DataFrame({"water": [water]})  
    )  
  
    st.success(  
        f"Predicted plant height: {prediction[0]:.2f} cm"  
    )  
