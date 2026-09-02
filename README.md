### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

df = pd.read_csv("/content/clustervisitor.csv")

print(df)

data = df[['Age']].values

k = 3

np.random.seed(42)
centers = data[np.random.choice(len(data), k, replace=False)]

for i in range(10):

    clusters = []

    for point in data:
        distance = [abs(point[0] - center[0]) for center in centers]
        clusters.append(distance.index(min(distance)))

    clusters = np.array(clusters)

    for j in range(k):
        if len(data[clusters == j]) > 0:
            centers[j] = np.mean(data[clusters == j], axis=0)

df['Segment'] = clusters

print("\nVisitor Segmentation:")
print(df)

plt.figure(figsize=(8,6))

plt.scatter(df['Age'], df['Segment'], s=100)

plt.xlabel("Age")
plt.ylabel("Segment")
plt.title("Visitor Segmentation using Clustering")

plt.grid(True)
plt.show()



```
### Output:
<img width="617" height="508" alt="image" src="https://github.com/user-attachments/assets/1957551e-019a-4299-84d4-7c3c6c947da5" />
<img width="752" height="608" alt="image" src="https://github.com/user-attachments/assets/340152e4-7756-4d80-be82-ac8de002bdf9" />

<img width="900" height="607" alt="image" src="https://github.com/user-attachments/assets/5417085d-94df-47ae-b677-06ce40bc5407" />

### Visualization:
```
visitor_counts = []

age_groups = {
    "Young": df[df['Age'] <= 30],
    "Middle": df[(df['Age'] > 30) & (df['Age'] <= 50)],
    "Old": df[df['Age'] > 50]
}

for group, visitors in age_groups.items():
    visitor_counts.append(len(visitors))

age_group_labels = list(age_groups.keys())

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

<img width="892" height="617" alt="image" src="https://github.com/user-attachments/assets/fad75fa3-f669-48e1-9012-c426e5712729" />

### Result:
Thus, cluster and Visitor Segmentation for Navigation patterns have been implemented successfully.

.

















.

























.



























.






























.



























.



























.































.















































.





















































.
