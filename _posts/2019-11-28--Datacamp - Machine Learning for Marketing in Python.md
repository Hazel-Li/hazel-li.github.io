---
title: "Datacamp Course Note - Machine Learning for Marketing in Python"
layout: post
date: 2019-11-28 21:12
image: /assets/images/datacamp.png
headerImage: true
tag:
- Datacamp
star: true
category: blog
author: yitingli
description: 
---

## Datacamp - Machine Learning for Marketing in Python

### Types of machine learning

**Supervised learning**

1. Given X, can we predict Y?

2. Classication - when Y is categorical (e.g. Churned/Not-churned, Yes/No, Fish/Dog/Cat).

3. Regression - when Y is continuous (e.g. Purchases, Clicks, Time Spent on Website)

**Unsupervised learning**

Given X, can we detect patterns and clusters that are homogenous

**Reinforcement learning**

Given a current state and a number potential actions, which path maximizes the reward

### Preprocessing

#### Exploring churn distribution

```python
telcom.groupby(['Churn']).size() / telcom.shape[0] * 100
```

#### Separate features and target variables

```python
target  = ['Churn']
custid  = ['customerID']
cols    = [col for col in telcom.columns if col notin custid + target
```

### Feature Engineering

**Aggregation**

```python
# Define the snapshot date
NOW = dt.datetime(2011,11,1)

# Calculate recency by subtracting current date from the latest InvoiceDate
features = online_X.groupby('CustomerID').agg({
  'InvoiceDate': lambda x: (NOW - x.max()).days,
  # Calculate frequency by counting unique number of invoices
  'InvoiceNo': pd.Series.nunique,
  # Calculate monetary value by summing all spend values
  'TotalSum': np.sum,
  # Calculate average and total quantity
  'Quantity': ['mean', 'sum']}).reset_index()

# Rename the columns
features.columns = ['CustomerID', 'recency', 'frequency', 'monetary', 'quantity_avg', 'quantity_total']
```

**Pivot_table**

```python
# Build a pivot table counting invoices for each customer monthly
cust_month_tx = pd.pivot_table(data=online, 
                               values='InvoiceNo',
                               index=['CustomerID'], 
                               columns=['InvoiceMonth'],
                               aggfunc=pd.Series.nunique, fill_value=0)
```

### Supervise ML : Implementing Linear Regression

#### Key Metrics

1. RMSE

2. MAE

3. R-square

![formula](/assets/images/formula.jpg)

#### OLS Rpeort

```python
# Import `statsmodels.api` module
import statsmodels.api as sm

# Initialize model instance on the training data
olsreg = sm.OLS(train_Y, train_X)

# Fit the model
olsreg = olsreg.fit()

# Print model summary
print(olsreg.summary())
```

### Unsupervised ML : Implementing K means

#### Unskew the data

1. log-transformation

2. Box-Cox transformation

#### Scale the data

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(wholesale_boxcox)
wholesale_scaled = scaler.transform(wholesale_boxcox) wholesale_scaled_df = pd.DataFrame(data=wholesale_scaled,
index=wholesale_boxcox.index,
columns=wholesale_boxcox.columns) wholesale_scaled_df.agg(['mean','std']).round()
```

```python
from sklearn.cluster import KMeans
kmeans=KMeans(n_clusters=k)
kmeans.fit(wholesale_scaled_df)
wholesale_kmeans4 = wholesale.assign(segment = kmeans.labels_)kmeans4_averages = wholesale_kmeans4.groupby(['segment']).mean().round(0) print(kmeans4_averages)
sns.heatmap(kmeans4_averages.T, cmap='YlGnBu') plt.show()
```

![heatmap.png](/assets/images/heatmap.png)

