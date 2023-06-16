# Mini-Project
# ABOUT PROJECT:
Weather forecasting is the task of forecasting weather
conditions for a given location and time. With the use of
weather data and algorithms, it is possible to predict
weather conditions for the next n number of days.
# CODE:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

data = pd.read_csv("DailyDelhiClimateTrain.csv")
print(data.head())
print(data.describe
print(data.info())
figure = px.line(data, x="date", 
                 y="meantemp", 
                 title='Mean Temperature in Delhi Over the Years')
figure.show()
figure = px.line(data, x="date", 
                 y="humidity", 
                 title='Humidity in Delhi Over the Years')
figure.show()
figure = px.line(data, x="date", 
                 y="wind_speed", 
                 title='Wind Speed in Delhi Over the Years')
figure.show()
figure = px.scatter(data_frame = data, x="humidity",
                    y="meantemp", size="meantemp", 
                    trendline="ols", 
                    title = "Relationship Between Temperature and Humidity")
figure.show()
data["date"] = pd.to_datetime(data["date"], format = '%Y-%m-%d')
data['year'] = data['date'].dt.year
data["month"] = data["date"].dt.month
print(data.head())
plt.style.use('fivethirtyeight')
plt.figure(figsize=(15, 10))
plt.title("Temperature Change in Delhi Over the Years")
sns.lineplot(data = data, x='month', y='meantemp', hue='year')
plt.show()
forecast_data = data.rename(columns = {"date": "ds", 
                                       "meantemp": "y"})
print(forecast_data)
from prophet import Prophet
from prophet.plot import plot_plotly, plot_components_plotly
model = Prophet()
model.fit(forecast_data)
forecasts = model.make_future_dataframe(periods=365)
predictions = model.predict(forecasts)
plot_plotly(model, predictions)

# OUTPUT:
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/711e27d9-
e8c0-4bc4-99ba-48ed863e02cd)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/1f37847e-2803-4988-b5b1-c0b7553d02aa)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/1b0cc615-c90f-4608-b0c7-9a874157f6ad)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/70dd5b44-cb98-461c-b308-bce73096893a)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/e57f960e-4409-4ac0-9dbe-c9af7149e410)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/6afc2b81-e153-404f-8cda-1d06bd7ec3ce)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/0dc59fad-e0e6-4cab-bdcb-773dba074f94)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/e693258c-9fcb-416e-b8fd-e11528164e0d)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/5d028430-f383-4445-8d44-f62b0ff32e45)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/65a0dfe1-8e00-478e-a27e-7d465c474a2a)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/6003d706-3ef7-4fd3-b9e5-f929ee38168b)
![image](https://github.com/VaishaliBalamurugan22008813/Mini-Project/assets/119390134/0bf84f96-b437-4a7b-85f3-0cf4d2c030e0)

