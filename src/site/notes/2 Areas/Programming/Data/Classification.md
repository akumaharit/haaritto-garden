---
{"dg-publish":true,"permalink":"/2-areas/programming/data/classification/","created":"2023-02-12T22:00:51.160+07:00","updated":"2025-09-02T23:21:31.034+07:00"}
---

1. Build a model
2. Model learns from the labeled data we pass into i 
	- labeled data ก็จะเหมือน training data นั่นเอง
3. Pass unlabeled data to the model as input
4. Model predict labels of the unseen data

## k-Nearest Neighbors (KNN)
- Famous for classification problem
- Predict the label of a datapoint by
	- looking at the `k` closest labeled datapoints
	- Taking a majority votes (based on majority label)
- this one we labeled as red if k = 3 (the blue circle) because there are 2 red and 1 blue (red is a majority)
	- ![Pasted image 20220710152751.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020220710152751.png)
	- ![Pasted image 20220710152738.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020220710152738.png)
- Importing KNN Model
```python 
from sklearn.neighbors import KNeighborsClassifier
X = churn_df[["total_day_charges", "total_eve_charge"]].values #features
y = churn_df["churn"].values #churn status

#the array must -> each row = each observation and each column = each features
#the target must be a single column with the same number of observation as the feature data

print(X.shape, y.shape)
#will return
(3333, 2), (3333,)

knn = KNeighborsClassifier(n_neighbors=15) #instantiate the model and set k as 15 and then assign to the knn variable
knn.fit(x,y) #fit training data

X_new = np.array([[56.8, 17.5]
				  [24.4, 24.1]
				  [50.1,10.9]])
#this is a unlabeled data with 2 features and 3 observations
predictions = knn.predict(X_new)
print('Predictions: {}'.format(predictions))

```
- Dataframe consist of the three attribute -> 
