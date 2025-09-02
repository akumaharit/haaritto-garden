---
{"dg-publish":true,"permalink":"/2-areas/programming/deep-learning/understanding-the-model-optimization/","created":"2023-02-12T22:00:51.410+07:00","updated":"2025-09-02T23:21:30.889+07:00"}
---

## Why optimization is hard?
- Why optimization is hard?
	- เรา update weight พร้อมกันหลาย ๆ weight
	- learning rate น้อยไปก็ช้า เยอะไปก็อาจเกินค่า optimize ได้
	- การใช้ adam ก็ช่วยแต่มันอาจไม่ได้ทำให้ model improve meaningfully
	- เราสามารถหา learning rate ที่เหมาะได้โดยการใช้ SGD
		- `optimzer = SGD(lr=lr)` กำหนด learning rate ด้วย lr argument แล้วเอา optimizer ไปใส่ตอน compile model `model.compile(optimzer = optimzer)`
- dying neuron problem
{ #fb2124}

	- เช่นการใช้ relu แล้ว node รับแต่ค่าติดลบ ทำให้มันได้ค่าออกมาเป็น - เสมอ ซึ่ง slope ของ weight ที่เข้าหาตัวมันก็จะเป้น 0 ทำให้ไม่มีการอัพเดทใด ๆ และ node นั้นเมื่อรับค่าลบมาแล้ว มันมักจะเป็นลบไปนาน ๆ เลยด้วย
- the vanishing gradient problem
{ #532b72}

	- การพยายามแก้ [[#^fb2124|dying neuron problem]] เช่นการใช้ tanh แต่สุดท้ายแล้ว ค่าของมันที่อัพเดทไปใกล้เคียง 0 หากดูลักษณะกราฟของมัน ด้วยเหตุนี้หากมันมีหลาย hidden layer ตอน backprop มันจะอัพเดทน้อยมาก
- ปัญหาทั้งสองอันนี้ [[#^fb2124|dying neuron problem]] และ [[#^532b72|the vanishing gradient problem]] ยังเป็นปัญหาที่ยัง active อยู่ หลายฝ่ายกำลังหาทางแก้ เช่น relu variation แต่เบื้องต้นให้แก้ activation function ก่อน ก็อาจจะพอช่วยได้ และก็อย่าลืมปัญหาสองอันนี้ ถ้าหาก model ไม่ค่อยพัฒนา

## Model Validation
- ใน deep learn จะใช้ validation spilt มากกว่า k-fold cross validaiton
	- เพราะข้อมูลมีค่อนข้างเยอะ k-fold cross validation มันจะใช้เวลาค่อนข้างมากในการทำ
	- ![Pasted image 20221025222231.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221025222231.png)
	- อันนี้คือภาพ k-fold cross validation
	- validation spilt คือการแบ่งข้อมูลเป็น test data โดยเฉพาะแล้วทดสอบอันนั้นไปเลย โดยข้อดีของการทำวิธีนี้คือ keras มันมีให้ใส่เป็น argument เลยตอนรัน model.fit นั่นก็คือการใส่ argument ว่า validation_split=0.3 ฯลฯ
	- เมื่อ validation score หยุดพัฒนา หรือเพิ่มดีขึ้นแล้ว เราจะหยุดโดยใช้ **early stopping**
		- ![Pasted image 20221025222716.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221025222716.png)
		- patience หมายถึงเราจะทน 2 epoch ที่ model ไม่พัฒนาแล้ว ปกติจะใช้ 2-3 เพราะบางทีมันกลับมาพัฒนา
		- callbacks ใส่เป็น list เพราะมันใส่ได้หลายอย่างซึ่งค่อนเรียนรู้ต่อในอนาคต
		- ปกติ keras จะ train 10 epoch แต่การใส่ ~~nb_epoch~~ ใช้เป็น epochs แล้ว!!! [ref](https://github.com/keras-team/keras/issues/14135) จะเป็นการกำหนดว่าให้มัน train กี่ epoch
	- การหา model ที่เหมาะสมคือการใช้ดวงทำเล่นๆทำไปทำมานั่นแหละจนมันจะดี
		- ![Pasted image 20221025223056.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221025223056.png)
		- การตั้ง `verbose = False` ใน argument ตอน fit หมายถึงมันจะไม่อัพเดทมาใน console (เผื่อในกรณีที่เราจะดูจากกราฟแทน)

## Model Capacity
![Pasted image 20221025225237.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221025225237.png)
- อีกชื่อ = network capacity
- มันคือ model's ability to capture predictive patterns in your data.
- คล้าย underfitting / overfitting
	- overfitting = มันจับ pattern ของ training data ได้ค่อนข้างเยอะเกินไป ทำให้มันเอาไปใช้กับ validation / new data ไม่ได้
	- underfitting = มันจับ pattern ของ training data ที่สำคัญ ๆ ไม่ได้ ทำให้มันเอาไปใช้กับ validation / new data ไม่ได้อยู่ดี
- การเพิ่ม layer / เพิ่ม size of layer จะทำให้ model capacity เพิ่มขึ้น
- ให้ทำ small network ก่อนแล้วค่อย ๆ เพิ่ม capacity โดยจะเพิ่มจำนวน node หรือ layer ก็ได้
	- ![Pasted image 20221025225447.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221025225447.png)

## Stepping up to image
- MNIST = database for handwriting

- https://en.wikipedia.org/wiki/List_of_datasets_for_machine-learning_research
- Kaggle
- ลองฝึกทำนายของพื้นฐานดูแล้วค่อยขยับไป image (using CNN), sound ไรงี้ หรือแล้วแต่เราสนใจ
- keras.io
- keras and tensorflow repositories on github ก็ดี
- ถ้ามันเริ่มช้า อาจจะใช้ tensorflow ได้แต่ต้องใช้ GPU ที่มี CUDA compatibility โดย NVIDIA มักจะ compat
	- ถ้าไม่ได้ก็ https://www.datacamp.com/tutorial/deep-learning-jupyter-aws