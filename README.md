# Diwali Sales Data Analysis

Hello! I'm Sonal M. Khobragde, and I'm excited to share my journey into data analysis with this project focused on Diwali sales data. This endeavor has been both educational and insightful, and I hope it provides value to fellow beginners in the field.

![image](https://github.com/user-attachments/assets/e28ecfa5-c0c5-4005-9f17-9a29ff5e3032)

## Project Overview

This project delves into the Diwali sales dataset to uncover trends and patterns, particularly focusing on sales variations across different demographics. The primary objectives include:

- **Data Cleaning**: Streamlining the dataset by removing unnecessary columns and addressing missing values to ensure accuracy.
- **Exploratory Data Analysis (EDA)**: Investigating the data to extract meaningful insights, such as sales trends based on gender and age groups.

## Dataset

The dataset comprises sales records from the Diwali festival period, including details like customer demographics, product categories, and purchase amounts. Key attributes include:

- `User_ID`: Unique customer identifier
- `Cust_name`: Customer name
- `Product_ID`: Unique product identifier
- `Gender`: Customer gender
- `Age Group`: Age range classification
- `Age`: Customer's age
- `Marital_Status`: Marital status (0 = unmarried, 1 = married)
- `State`: State of residence
- `Zone`: Regional classification (e.g., Western, Southern)
- `Occupation`: Occupation type
- `Product_Category`: Category of the purchased product
- `Orders`: Number of orders placed
- `Amount`: Total transaction amount

## Tools and Libraries

Throughout this project, I utilized several Python libraries that are instrumental in data analysis:

- **pandas**: For data manipulation and cleaning
- **seaborn**: For data visualization
- **matplotlib**: For plotting graphs and charts
- **numpy**: For numerical operations



#  insights


## Gender-Based Sales Distribution:


import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

data = pd.read_csv('Diwali Sales Data.csv', encoding='ISO-8859-1')

gender_sales = data.groupby('Gender')['Amount'].sum().reset_index()

plt.figure(figsize=(8, 5))
sns.barplot(x='Gender', y='Amount', data=gender_sales, palette='viridis')
plt.title('Total Sales Amount by Gender')
plt.xlabel('Gender')
plt.ylabel('Total Sales Amount')
plt.show()




## Age Group vs. Total Sales:


age_sales = data.groupby('Age Group')['Amount'].sum().reset_index()

 Plot
plt.figure(figsize=(10, 6))
sns.barplot(x='Age Group', y='Amount', data=age_sales, palette='magma')
plt.title('Total Sales Amount by Age Group')
plt.xlabel('Age Group')
plt.ylabel('Total Sales Amount')
plt.show()

## Sales by State:


state_sales = data.groupby('State')['Amount'].sum().sort_values().reset_index()


plt.figure(figsize=(12, 8))
sns.barplot(x='Amount', y='State', data=state_sales, palette='coolwarm')
plt.title('Total Sales Amount by State')
plt.xlabel('Total Sales Amount')
plt.ylabel('State')
plt.show()


## Monthly Sales Trend:


data['Date'] = pd.to_datetime(data['Date'], errors='coerce')


data['Month'] = data['Date'].dt.month
data['Year'] = data['Date'].dt.year


monthly_sales = data.groupby(['Year', 'Month'])['Amount'].sum().reset_index()


monthly_sales['Year-Month'] = monthly_sales['Year'].astype(str) + '-' + monthly_sales['Month'].astype(str)


plt.figure(figsize=(12, 6))
sns.lineplot(x='Year-Month', y='Amount', data=monthly_sales, marker='o')
plt.title('Monthly Sales Trend')
plt.xlabel('Year-Month')
plt.ylabel('Total Sales Amount')
plt.xticks(rotation=45)
plt.show()






