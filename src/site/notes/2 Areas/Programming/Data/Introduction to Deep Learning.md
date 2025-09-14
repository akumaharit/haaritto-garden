---
{"dg-publish":true,"permalink":"/2-areas/programming/data/introduction-to-deep-learning/","created":"2023-02-12T22:00:51.245+07:00","updated":"2025-09-02T23:21:30.995+07:00"}
---

**Topic:** Introduction to Deep Learning
**Alias:**
**Tags:** #deeplearn 
**Creation Date**: 2022-10-16 17:52
**Modification Date:** 2022-10-16 17:52

## Machine Learning to Deep Learning
- มันเป็นสมการคณิตศาสตร์แหละ **y**=f(**x**)
	- x และ y เป็น vector ก็เลยตัวหนาไว้
	- x อาจจะหมายถึง pixels ภาพไรงี้ หรือ genome sequence
	- ปกติก็จะสร้าง function ด้วยตัวเอง แต่การที่ทำ machine learning หมายถึง กรให้คอมมันสร้าง function ที่เหมาะสมขึ้นมา โดยการคิดว่าค่า **parameters** ควรจะเป็นค่าอะไร
### Linear Models
- **y = Mx+b**
	- M คือ matrix (อาจเรียกว่า weights)
	- b หมายถึง bias
	- ถ้า x = T และ y = S ตัว 
		- M จะหมายถึง S x T matrix
		- b เป็น vector ของ length S
		- ทั้งหมดพวกนี้รวมกันแล้วก็จะกลายเป็น parameters ของ model
	- parameters คือ M และ b
	- สิ่งนี้เรียกว่า perceptons เป็นโมเดล ML แรก ๆ
	- ข้อจำกัดของมันคือ linearity ซึ่งมันไม่ตอบอะไรที่มัน nonlinear จึงมีการคิดค้นวิธีการขึ้นมา เพื่อให้แค่การคิดค่า parameter โดยคอมพิวเตอร์ สามารถช่วยตอบโจทย์ nonlinear ได้
### Multilayer Perceptrons
- ![[2285FF41-8085-473F-B79E-80200E4D2BD7.jpeg\|2285FF41-8085-473F-B79E-80200E4D2BD7.jpeg]]
- ไอ function ที่เป็นค่าของ x ของ linear มันคือ activation function ซึ่งการใสใ่มันทำให้กลายเป็น non-linear ได้ และการใส่ต่อไปเรื่อย ๆ แบบนี้มันจะเพิ่ม "[[#^5cf0fb|Depth]]"
- ทางแก้ Nonlinear ก็คือการใช้ linear หลาย ๆ อันมาต่อกัน และให้มันผ่าน nonlinear function เข้า โดย function อีกอันที่ใส่เข้าไปเราเรียกว่า activation function
- เราสามารถใส่หลายชั้นได้ โดยแต่ละชั้นมันก็จะมีค่า parameter ของมัน เพราะ nonlinearity อาจต่างกัน
- activation function ที่ใช้บ่อยคือ
{ #eeec6f}

	- ![[75B38FF2-4D90-4F2F-BEB1-73FA2AD94600.jpeg\|75B38FF2-4D90-4F2F-BEB1-73FA2AD94600.jpeg]]
	- rectified linear unit (ReLU)
	- hyperbolic tanget (tanh(x))
	- logistic sigmoid .. *เขียนไม่เป็น*
- Depth หมายถึงจำนวนชั้น ถ้ามีชั้นเดียวเรามักจะเรียกว่า shallow และการที่มันมีหลายชั้นนี่แหละเลยเป็นที่มาของคำว่า **deep learning**
{ #5cf0fb}


#todo
อย่าลืมใส่ส่วนของ validation, regularization, gradient descent? ลองไปดูคลิปในยูทูปก่อน ที่มันอธิบายเกี่ยวกับ neural network

### Hyperparameter Optimization