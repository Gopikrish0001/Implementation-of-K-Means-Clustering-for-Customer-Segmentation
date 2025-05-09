# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1..Import dataset and print head,info of the dataset
2.check for null values
3.Import kmeans and fit it to the dataset
4.Plot the graph using elbow method
5.Print the predicted array
6.Plot the customer segments 


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Gopikrishnan M
RegisterNumber:212223043001 
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

data = pd.read_csv("Mall_Customers.csv")

print(data.head())
print(data.info())
print(data.isnull().sum())

wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", random_state=42)
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

km = KMeans(n_clusters=5, init="k-means++", random_state=42)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])
print(y_pred)

data["cluster"] = y_pred

df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="cluster 4")

plt.legend()
plt.title("Customer Segments")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.show()
```
## Output:

1.DATA.HEAD():
![image](https://github.com/user-attachments/assets/baf06b97-8a6b-43e7-af08-b0a2a3bc095a)

2.DATA.INFO():
![image](https://github.com/user-attachments/assets/d56e550e-9cd0-41c2-aa08-aa9af544947c)

3.DATA.INSULL().SUM():
![image](https://github.com/user-attachments/assets/d0d1ba31-7e9c-4345-ab76-1bd8f4dd54fe)

4.POLT.USING ELBOW METHOD:
![image](https://github.com/user-attachments/assets/1599201c-6b97-4b80-a4ea-6ef931a30e63)

5.K_MEANS CLUSTREING:
![image](https://github.com/user-attachments/assets/c54f951f-c7d9-4d71-8cb4-354ab9f2abd0)

6.Y_PRED ARRAY:
![image](https://github.com/user-attachments/assets/457a6942-14d1-43ae-944e-ea2572faea8c)

7.CUSTOMER SEGMENT:
![image](https://github.com/user-attachments/assets/f9cc1fa6-5e01-4de4-aaa3-6ae9f1d719fa)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
