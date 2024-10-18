# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. **Load Data**: Read the customer dataset.
2. **Explore Data**: Check the dataset structure and for missing values.
3. **Initialize K-Means**: Prepare to find optimal number of clusters using the Elbow Method.
4. **Calculate WCSS**: Iterate through a range of cluster numbers (1-10) to calculate Within-Cluster Sum of Squares (WCSS).
5. **Plot Elbow Graph**: Visualize WCSS against the number of clusters to identify the elbow point.
6. **Fit K-Means Model**: Choose optimal clusters (e.g., 5) and fit the model.
7. **Predict Clusters**: Assign cluster labels to the data points.
8. **Add Cluster Labels**: Add predicted cluster labels to the original dataset.
9. **Segment Data**: Create subsets of data for each cluster.
10. **Visualize Clusters**: Plot the clusters using a scatter plot of Annual Income vs. Spending Score.

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Ashwin Kumar A
RegisterNumber: 212223040021 
```
```py
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("Mall_Customers.csv")
df.head()
df.info()
df.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
y_pred = km.predict(df.iloc[:,3:])
print("Predicted values : ")
y_pred
df["cluster"] = y_pred
df0 = df[df["cluster"]==0]
df1 = df[df["cluster"]==1]
df2 = df[df["cluster"]==2]
df3 = df[df["cluster"]==3]
df4 = df[df["cluster"]==4]
df0.head()
df1.head()
df2.head()
df3.head()
df4.head()
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer segments")
```

## Output:

![image](https://github.com/user-attachments/assets/51fc26be-9a6c-44d7-b95e-a651a7a4e5b1)

![image](https://github.com/user-attachments/assets/02e9a122-09d1-4bf9-8bdf-3cdecc4894a8)

![image](https://github.com/user-attachments/assets/517d4bd7-2c0e-47af-8ad3-04e0e939a61a)

![image](https://github.com/user-attachments/assets/d9f22d7a-9e34-4dbe-b97f-032884e53b54)

![image](https://github.com/user-attachments/assets/5ef688e8-4a0a-4c79-9d46-5ab7741c2961)

![image](https://github.com/user-attachments/assets/413e34a9-cb6a-44e7-bb4b-bbff5cf9775f)

![image](https://github.com/user-attachments/assets/1e3f77eb-4ab8-49e7-b5b0-e381f6f44a1a)

![image](https://github.com/user-attachments/assets/8f878351-9ce3-4340-86cc-f8894eb63e1c)

![image](https://github.com/user-attachments/assets/f9ad2730-9a98-4ded-a4f4-583a8e8e11cd)

![image](https://github.com/user-attachments/assets/e05edd09-a33a-4022-be07-1126a78c9a92)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
