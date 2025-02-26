# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull.sum()
df.info()
df.describe()

sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
Which City has Highest profit?

df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()

sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)

df["Sales"].corr(df["Profit"])

df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()

sns.pairplot(df_corr, kind="scatter")
plt.show()

grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()


grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()


grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```
# OUPUT
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/e6bb6101-75bb-4097-a38b-a22430438fb0)

![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/66bbdd8b-df45-4484-a02e-7af7f57ee4d8)

![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/900d9e44-a386-46c1-85c5-227c592eb416)

![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/2be7df83-5cee-4c94-bd8c-ede57fc3e9a4)

### Which Segment has Highest sales?
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/4f6d2dd8-e0e5-4b4c-9cdf-8e556e997ea6)

![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/34a96b76-f781-48e5-ad02-7eaf7dd2e8a4)
### Which City has Highest profit?
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/d3095078-edc5-4825-9b9f-ab984910bb2e)
### Which ship mode is profitable?
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/25511194-706d-4f8b-88ef-766f8e2fce51)
### Sales of the product based on region
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/6f74ce9d-e8af-4f8a-9cf1-7cf879bec524)
### Find the relation between sales and profit
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/1b0dddfc-2c39-4892-b388-5921aa2ad2df)
### Find the relation between sales and profit based on the following category.
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/5f340d52-3073-4eaa-a434-56a69c98b9ed)
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/fdf82085-f11b-4d33-957e-40e81e84bc9f)
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/14d88616-4ba8-4208-b994-c55672f4f086)
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/0ff69e2f-0c99-4d9f-93aa-628fff6374ec)
![image](https://github.com/SandhiyaR1/Ex-08-Data-Visualization-/assets/113497571/075702db-cdf3-481e-81aa-a7ddc95b4cb6)
# Result:
Thus, Data Visualization is performed on the given dataset and save the data to a file.
