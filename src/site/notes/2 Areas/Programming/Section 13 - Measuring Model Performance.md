---
{"dg-publish":true,"permalink":"/2-areas/programming/section-13-measuring-model-performance/"}
---

### Signal Detection Theory
- Terminology that might be used ![Pasted image 20230320140536.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020230320140536.png)
- Alternate terms ![Pasted image 20230320140624.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020230320140624.png)aka. **Confusion Matrix**
- Accuracy does not reveal sensitivity, and might be biased


### Metrics
![Pasted image 20230320153456.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020230320153456.png)
- Accuracy just tell overall model performance
- Precision: True positives / total of "yes" prediction
	- ไว้จัดการกับ **"yes" biases** -> จะเด่นขึ้นมาเมื่อตอบ YES บ่อยเกินไป
	- Useful when false positive are bad like **cancer detection**
- Recall: True positive / total number of present (aka. **sensitivity**)
	- ไว้จัดการกับ **'no' biases** -> จะเด่นขึ้นมาเมื่อตอบ NO บ่อยเกินไป
	- Useful when false negatives are bad like covid19
- F1 Score: balance between precision and recall ![Pasted image 20230320153542.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020230320153542.png)
	- มันดูเหมือนว่ามันไม่ได้ใส่ true negative เข้าไปด้วย แต่จริง ๆ มันใส่เข้าไปแล้วแบบเนียน ๆ
- Ex. ถ้า precision น้อยกว่า recall แปลว่า model มัน bias ที่จะตอบ yes
- Ex. ถ้า precision น้อย แสดงว่ามัน bias ที่จะตอบ yes

PPV = Precision = **ที่ทำนายว่าถูก** ถูกจริงป่าว
NPV = **ที่ทำนายว่าผิด** ผิดจริงป่าว
Recall = Sensitivity **ที่ควรถูก** ได้ถูกแค่ไหน
Specficity = **ที่ควรผิด** ได้ผิดแค่ไหน

![Pasted image 20240226193319.png|475](/img/user/3%20Resources/Attachment/Pasted%20image%2020240226193319.png)


## APRF Implementation in scikitlearn
``` python
# NEW! using scikitlearn to compute ARPF

import sklearn.metrics as skm

# initialize vectors

train_metrics = [0,0,0,0]
test_metrics  = [0,0,0,0]

# training

train_metrics[0] = skm.accuracy_score (train_loader.dataset.tensors[1],train_predictions>0)
train_metrics[1] = skm.precision_score(train_loader.dataset.tensors[1],train_predictions>0)
train_metrics[2] = skm.recall_score   (train_loader.dataset.tensors[1],train_predictions>0)
train_metrics[3] = skm.f1_score       (train_loader.dataset.tensors[1],train_predictions>0)

# test

test_metrics[0] = skm.accuracy_score (test_loader.dataset.tensors[1],test_predictions>0)
test_metrics[1] = skm.precision_score(test_loader.dataset.tensors[1],test_predictions>0)
test_metrics[2] = skm.recall_score   (test_loader.dataset.tensors[1],test_predictions>0)
test_metrics[3] = skm.f1_score       (test_loader.dataset.tensors[1],test_predictions>0)
```
- ใน argument ของ function มันเป็นการใส่ labels ก่อนแล้วค่อยใส่ predicted นะ
``` python
#Confusion matrices

trainConf = skm.confusion_matrix(train_loader.dataset.tensors[1],train_predictions>0)

testConf  = skm.confusion_matrix(test_loader.dataset.tensors[1], test_predictions>0)

  

fig,ax = plt.subplots(1,2,figsize=(10,4))

  

# confmat during TRAIN

ax[0].imshow(trainConf,'Blues',vmax=len(train_predictions)/2)

ax[0].set_xticks([0,1])

ax[0].set_yticks([0,1])

ax[0].set_xticklabels(['bad','good'])

ax[0].set_yticklabels(['bad','good'])

ax[0].set_xlabel('Predicted quality')

ax[0].set_ylabel('True quality')

ax[0].set_title('TRAIN confusion matrix')

  

# add text labels

ax[0].text(0,0,f'True negatives:\n{trainConf[0,0]}' ,ha='center',va='center')

ax[0].text(0,1,f'False negatives:\n{trainConf[1,0]}',ha='center',va='center')

ax[0].text(1,1,f'True positives:\n{trainConf[1,1]}' ,ha='center',va='center')

ax[0].text(1,0,f'False positives:\n{trainConf[0,1]}',ha='center',va='center')

  
  
  
  

# confmat during TEST

ax[1].imshow(testConf,'Blues',vmax=len(test_predictions)/2)

ax[1].set_xticks([0,1])

ax[1].set_yticks([0,1])

ax[1].set_xticklabels(['bad','good'])

ax[1].set_yticklabels(['bad','good'])

ax[1].set_xlabel('Predicted quality')

ax[1].set_ylabel('True quality')

ax[1].set_title('TEST confusion matrix')

  

# add text labels

ax[1].text(0,0,f'True negatives:\n{testConf[0,0]}' ,ha='center',va='center')

ax[1].text(0,1,f'False negatives:\n{testConf[1,0]}',ha='center',va='center')

ax[1].text(1,1,f'True positives:\n{testConf[1,1]}' ,ha='center',va='center')

ax[1].text(1,0,f'False positives:\n{testConf[0,1]}',ha='center',va='center')

plt.show()

  

trainConf
```
- ใน scikitlearn confusion matrix จะเอา true positive ไปอยู่มุมขวาล่าง!