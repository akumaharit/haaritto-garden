---
{"dg-publish":true,"permalink":"/2-areas/programming/data/machine-learning-with-scikit-learn/","created":"2023-02-12T22:00:51.287+07:00","updated":"2025-09-02T23:21:31.028+07:00"}
---


- Unsupervised learning
	- learn to group without knowing what is it (we might use clustering)
- Supervised learning
	- predicted values are know -> aim to predict the target values of unseen data


Supervised Learning
	- Classification
	- Regression

Feature = predicictor variable = independent variable
target variable = dependent variable = response variable

Requirements
	- No missing value
	- data in numeric format
	- data stored in pandas dataframe or numpy array
	- should perform exploratory data analysis first (EDA)

scikit-learn syntax
```python
from sklearn.module import Model #we import a model which is a type of algorithm for our supervised problem ex. k-nearest neighbors model uses distance between observations to predict labels or value
model = Model() #instantitate the model to model variable
model.fit(X, y) #we fit model to the data (so it can learn, X = array of our features and y = array of our target variable values)
predictions = model.predict(X_new) #X_new contain the data we want to try to predict
print(predictions)

```


## Model
- binary classification model
	- only two value (0 and 1)


## Model Evaluation
- Accurary is commonly used
- does not indicate ability to generalize of the model
``` python
#spilting data for training and test
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state = 21, stratify=y)
#testsize = test data size (which should reflect the target label proportion)
#random_state = random seed so we can reproduce the extact split
#stratify=y will make the SPLIT DATA in the proportion same as parameter stated in stratify
#it return 4 array = training data, test data, training labels, test labels


knn = KNeighborsClassifier(n_neighbors = 6)
knn.fit(X_train, y_train)
print(knn.score(X_test, y_test))
```
- ![Pasted image 20220716163845.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020220716163845.png)
- Increasing k cause the model to be less complex (เพราะข้อมูลแต่ละตัว ส่งผลต่อ decision boundaries น้อยลง) ทำให้ simple model แต่มันอาจไม่แสดงถึงความสัมพันธ์ต่อ dataset ได้อย่างชัดเจน จึงอาจเกิด underfitting
	- Decreasing k ทำให้ more complex และอาจ overfitting เพราะได้รับผลกระทบจากพวก noise (sensitive to noise) ทำให้ไม่ reflect general trends อาจเกิด overfitting
		- we can interpret k using model complexity curve
		  ```python
		  train_accuracies = {}
		  test_accuracies = {}
		  neighbors = np.arrage(1,26)
		  for neighbor in neighbors:
			  knn = KNeighborsClassifier(n_neighbors=neighbor)
			  knn.fit(X_train, y_train)
			  train_accuracies[neighbor] = knn.score(X_train, y_train) #ถ้าเอา model มาใช้กับ train data ที่ใช้ในการ fit เทียบกับคำตอบที่ใช้ train ไปจะได้คะแนนเท่าไหร่
			  test_accuracies[neighbor] = knn.score(X_test, y_test) #ถ้าเอา model มาใช้กับ test data (ที่ไม่เคยเจอมาก่อน) เทียบกับคำตอบที่มีในใจ มันจะได้คะแนนเท่าไหร่
	
		  ```
		  หลังจากนั้นลอง plot กราฟได้มาเป็น
		  ![Pasted image 20220716164842.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020220716164842.png)
