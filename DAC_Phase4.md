**PRODUCT SALES ANALYSIS**

In this part of project: 

- Analysis by creating visualizations and generating actionable insights. 
- Design interactive dashboards and reports that display insights such as top-selling products, sales trends, and customer preferences. 
- Derive insights from the visualizations, such as identifying products with the highest sales, peak sales periods, and customer preferences for specific products. 


**Load the dataset  and print summary statistics:**

import pandas as pd

df = pd.read\_csv('statsfinal.csv')

print(df.head())

print(df.describe())

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.001.png)

**Visualizing Product Sales Over Time:**

import pandas as pd

import matplotlib.pyplot as plt

\# Step 1: Import the Data

data = pd.read\_csv('statsfinal.csv')

\# Step 2: Data Exploration

\# Display basic statistics

print(data.describe())

\# Check for missing values

print(data.isnull().sum())![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.002.png)

\# Convert 'Date' column to datetime

data['Date'] = pd.to\_datetime(data['Date'])

\# Set the 'Date' column as the index

data.set\_index('Date', inplace=True)\

\# Create subplots for each product

fig, axes = plt.subplots(4, 1, figsize=(12, 16), sharex=True)

\# Plot total unit sales for each product

products = ['Q-P1', 'Q-P2', 'Q-P3', 'Q-P4']

product\_labels = ['Product 1', 'Product 2', 'Product 3', 'Product 4']

for i, product in enumerate(products):

`    `axes[i].plot(data.index, data[product], label=product\_labels[i], marker='o')

`    `axes[i].set\_ylabel('Total Unit Sales')

`    `axes[i].set\_title(f'{product\_labels[i]} Sales Over Time')

`    `axes[i].legend()

\# Set a common x-axis label and add a title

axes[-1].set\_xlabel('Date')

plt.tight\_layout()

plt.show()

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.003.png) 

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.004.png)

**Visualize Revenue Over Time:**

\# Create subplots for each product's total revenue

fig, axes = plt.subplots(4, 1, figsize=(12, 16), sharex=True)

\# Plot total revenue for each product

products = ['S-P1', 'S-P2', 'S-P3', 'S-P4']

product\_labels = ['Product 1', 'Product 2', 'Product 3', 'Product 4']

for i, product in enumerate(products):

`    `axes[i].plot(data.index, data[product], label=product\_labels[i], marker='o')

`    `axes[i].set\_ylabel('Total Revenue')

`    `axes[i].set\_title(f'{product\_labels[i]} Revenue Over Time')

`    `axes[i].legend()

\# Set a common x-axis label and add a title

axes[-1].set\_xlabel('Date')

plt.tight\_layout()

plt.show()

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.005.png)

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.006.png)

**Visualize data for First Date:**

\# Get the data for the first date

first\_date\_data = data.iloc[0]

\# List of products and their labels

products = ['Product 1', 'Product 2', 'Product 3', 'Product 4']

\# Extract total unit sales and total revenue for the first date

unit\_sales = [first\_date\_data['Q-P1'], first\_date\_data['Q-P2'], first\_date\_data['Q-P3'], first\_date\_data['Q-P4']]

revenue = [first\_date\_data['S-P1'], first\_date\_data['S-P2'], first\_date\_data['S-P3'], first\_date\_data['S-P4']]

\# Create a bar chart for total unit sales

plt.figure(figsize=(12, 6))

plt.bar(products, unit\_sales, color='blue', alpha=0.7, label='Total Unit Sales')

plt.xlabel('Product')

plt.ylabel('Total Unit Sales')

plt.title('Total Unit Sales for the First Date')

plt.legend(loc='upper right')

\# Create a grouped bar chart for total revenue

plt.figure(figsize=(12, 6))

bar\_width = 0.35

index = range(len(products))

plt.bar(index, revenue, bar\_width, color='cyan', alpha=0.7, label='Total Revenue')

plt.xlabel('Product')

plt.ylabel('Total Revenue')

plt.title('Total Revenue for the First Date')

plt.xticks([i + bar\_width / 2 for i in index], products)

plt.legend(loc='upper right')

plt.show()

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.007.png)

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.008.png)

**Visualize Total Sales and Revenue over time:**

\# Calculate the cumulative sum of total unit sales and total revenue

data['Total Unit Sales'] = data[['Q-P1', 'Q-P2', 'Q-P3', 'Q-P4']].sum(axis=1)

data['Total Revenue'] = data[['S-P1', 'S-P2', 'S-P3', 'S-P4']].sum(axis=1)

\# Create an area chart for total unit sales

plt.figure(figsize=(12, 6))

plt.fill\_between(data.index, data['Total Unit Sales'], color='blue', alpha=0.5, label='Total Unit Sales')

plt.xlabel('Date')

plt.ylabel('Total Unit Sales')

plt.title('Total Unit Sales Over Time')

plt.legend(loc='upper left')

\# Create an area chart for total revenue

plt.figure(figsize=(12, 6))

plt.fill\_between(data.index, data['Total Revenue'], color='cyan', alpha=0.5, label='Total Revenue')

plt.xlabel('Date')

plt.ylabel('Total Revenue')

plt.title('Total Revenue Over Time')

plt.legend(loc='upper left')

plt.show()

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.009.png)

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.010.png)

**Total Unit Sale for All Time:**

\# Sum the total unit sales for each product over all time

total\_sales = [

`    `data['Q-P1'].sum(),

`    `data['Q-P2'].sum(),

`    `data['Q-P3'].sum(),

`    `data['Q-P4'].sum()

]

\# List of products and their labels

products = ['Product 1', 'Product 2', 'Product 3', 'Product 4']

\# Create a bar chart for total unit sales over all time

plt.figure(figsize=(10, 6))

plt.bar(products, total\_sales, color='blue', alpha=0.7)

plt.xlabel('Product')

plt.ylabel('Total Unit Sales')

plt.title('Total Unit Sales for All Time')

plt.show()

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.011.png)

**Total Revenue  for  All Time:**

\# Sum the total revenue for each product over all time

total\_revenue = [

`    `data['S-P1'].sum(),

`    `data['S-P2'].sum(),

`    `data['S-P3'].sum(),

`    `data['S-P4'].sum()

]

\# List of products and their labels

products = ['Product 1', 'Product 2', 'Product 3', 'Product 4']

\# Create a bar chart for total revenue over all time

plt.figure(figsize=(10, 6))

plt.bar(products, total\_revenue, color='cyan', alpha=0.7)

plt.xlabel('Product')

plt.ylabel('Total Revenue')

plt.title('Total Revenue for All Time')

plt.show()

![](Aspose.Words.4f6c875a-a008-4dc3-8af1-d619b0c0b47d.012.png)
