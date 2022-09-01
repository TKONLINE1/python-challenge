# python-challenge
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns
df= pd.read_csv('budget_data.csv')
df.head()
df.info()
#The total number of months included in the dataset #date format is Jan-2010
df['Date'] = pd.to_datetime(df['Date'])
df['Date'] = df['Date'].dt.strftime('%m-%Y') #print the total number of months
print('Total number of months:', df['Date'].nunique())
df.head()
 #The total net amount of "Profit/Losses" over the entire period
total_net = df['Profit/Losses'].sum()
print('Total net amount of "Profit/Losses" over the entire period: $', total_net)
#The average of the changes in Profit/Losses over the entire period
df['Change'] = df['Profit/Losses'].diff()
avg_change = df['Change'].mean()
avg_change = round (avg_change,2) 
print(f'Average of the changes in Profit/Losses over the entire period: ${avg_change}') 
#The greatest increase in profits (date and amount) over the entire period
max_change = df['Change'].max()
max_change_date = df['Date'][df['Change'] == max_change].values[0]
print('Greatest increase in profits (date and amount) over the entire period:', max_change_date, '$', max_change)
#The greatest decrease in losses (date and amount) over the entire period
min_change = df['Change'].min()
min_change_date = df['Date'][df['Change'] == min_change].values[0]
print('Greatest decrease in losses (date and amount) over the entire period:', min_change_date, '$', min_change)

