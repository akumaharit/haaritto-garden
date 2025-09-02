---
{"dg-publish":true,"permalink":"/2-areas/programming/deep-learning/optimizing-a-neural-network-with-backward-propagation/","created":"2023-02-12T22:00:51.370+07:00","updated":"2025-09-02T23:21:30.873+07:00"}
---

**Topic:** Optimizing a neural network with backward propagation
**Course:** Introduction to Deepe Learning in Python
**Link:**
**Alias:**
**Tags:** #deeplearn #python #datacamp
**Creation Date**: 2022-10-18 22:42


## The need for optimization
- การคำนวณไปข้างหน้าของ network จริง ๆ มันก็คือ "forward propagation"
- ตัวอย่าง Error แต่การแก้ค่า weight มันจะช่วย
	- ![Pasted image 20221018225010.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221018225010.png)  ![Pasted image 20221018225038.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221018225038.png)
- แต่ละ weight จะเกิด error อยู่แล้ว ดังนั้นการมี datapoint เยอะ มันก็ยิ่งยากเพราะจะต้องหาทางตั้ง weight ให้เหมาะ 
{ #817c58}

	- ![Pasted image 20221018225505.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221018225505.png)
- Loss Function
	- aggregate error ของแต่ละ datapoint มาเป็นค่าเดียวเพื่อวัด predictive performance
	- จะใช้ [[2 Areas/Programming/Deep Learning/Mean-Squared Error\|Mean-Squared Error]] ก็ได้ (ก็คือ square error แล้วหา mean ของมันทั้งหมดของแต่ละ datapoint) #tounderstand 
	- ค่าน้อยแปลว่าดี ดังนั้นเราต้องการ weight ที่ทำให้ค่า loss function lowest
	- ในที่นี้เราจะใช้ algorithm ที่ชื่อว่า gradient descent
		- มันก็เหมือนการขยับทีละนิด จนกว่าจะอยู่จุดต่ำสุด (loss function น้อยสุด) ถ้ามองเหมือนเราไปยืนอยู่บนกราฟของ[[#^817c58|กราฟนี้]]
		- โดยมันจะขยับยังไงก็ดูจาก slope ของกราฟ เช่นอันนี้กรณี weight เดียว
			- ![Pasted image 20221018230431.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221018230431.png)  ![Pasted image 20221018230515.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221018230515.png)
			- ตามภาพนี้จะเป็นว่า slope มันคือของ weight
		- update **each weight** by subtracting (โดยเอามาลบ) learning rate * slope
		- learning rate เอาไว้ปรับว่ามันจะปรับเปลี่ยนแค่ไหนในแต่ละก้าว เพราะถ้าก้าวไกลไปมันจะพลาดได้ (ส่วนใหญ่จะตั้ง 0.01)
		- การหา slope ของ**แต่ละ w เทียบ loss** จะต้องใช้ **chain rule (calculus)** -> ให้ tensorflow / keras ทำแทน #tounderstand 
			- แต่หลัก ๆ คือการเอา 3 ค่ามาคูณกัน ก็คือ
			- ![Pasted image 20221018232345.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221018232345.png)
			- Slope of the [[2 Areas/Programming/Deep Learning/Mean-Squared Error\|Mean-Squared Error]] (loss) function w.r.t value **at the node we feed into** 
				- หลังใช้แคลจะได้ว่า ค่ามันคือ 2(predicted value - actual value) = **2 * error**
				- ตามภาพอันนี้คือ 2 * -4
			- the value of the node **that feeds into our weight**
				- 3
			- slope of the activation function w.r.t value **at the node we feed into** 
				- หากไม่ได้ใช้ หรือค่าติดลบก็จะเป็น 0
				- แต่หากใช้ และค่ามันเป็นบวก slope ก็จะเป็น 1 เพราะแกน x / y ค่าเท่ากัน
			- หลังจากได้ค่า 3 อันเราจะนำมาคำนวณต่อดังนี้
				- จาก 3 อันจะได้ว่า 2 * -4 * 3 = -24 สิ่งนี้เรียกว่า **Slope ของ Weight เทียบ loss**
				- เอา **ค่า weight มาลบด้วย -24(slope) * learning rate** 
				- ถ้ากำหนด learning rate = 0.01 มันจะเป็น 2 * -24 * 0.01 = 2.24 แปลว่าน้ำหนักใหม่คือ 2.24
			- ปกติเราจะทำแบบนี้กับทุก weights พร้อมกันในทุก iteration
			- Gradients ก็คือชื่อเรียกของ 2 * error * the value of node that feed into weight (ซึ่งตรงนี้อาจเป็น input ที่เป็น array) ดังนั้นเราจะได้ array ที่เอา 2 เท่า error คุณกระจายเข้าไปแล้ว เราเรียก array ของ slope ตรงนี้ว่า **Gradients** จึงเป็นที่มาของชื่อ Gradients Descents
- [[What is backpropagation really doing - Chapter 3 Deep learning \| Back propagation]]
	- ก็แค่เอา output (prediction error?) ไปรันย้อยกลับ แล้วคำนวณ slope เพื่อแก้ weight ของแต่ละอันเหมือนกัน แต่อันนี้มันก็จะใช้คณิตศาสตร์ (rule of chain) เช่นเดียวกัน และปกติเราจะใช้แค่ library ไม่ต้องมารู้คณิตศาสตร์ขนาดนั้น
	- เวลารันจะไปทีละขั้นตอน ทีละ layer โดยสลับ output เป็น input เพื่อไปปรับ node ของ layer ก่อนหน้า และเราจะต้องทำ forward ก่อนจึงจะ back ได้ ถ้า forward 4 รอบ back ก็ต้อง 4 รอบ 
	- ถ้าพูดถึง "slope of the node value" จะเป็นการเอา slope ของทุก weight ที่มายัง node นั้น
	- ![Pasted image 20221021173705.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021173705.png)![Pasted image 20221021173619.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021173619.png)
	- คืออีนี่ไม่ใช่ค่าจาก forward prop แต่เป็น slope ที่มันได้ตอนทำ forward prop เราเอามันมาย้อนแทนโดยคำนวณแบบเดิม ก็คือ เอา slope forward prop (ซึ่งคือ slope of w to loss function) มาคูณกับค่าที่ใส่เข้าไป และคูณกับ slope of activation function ซึ่งคือ 1 ก็จะได้ gradient ที่เอาไว้ไปคูณ learning rate แล้วเอาปรับ weight
	- ![Pasted image 20221021172726.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021172726.png)
- Stochastic Gradient Descent
{ #fc761b}

	- มีสิ่งนี้เพื่อทำให้การคำนวณเร็วขึ้น
	- หมายถึงการใช้ "batch" แทน full data ในการคำนวณ slope เพื่อมาอัพเดท weight
		- ต่างจากแบบ gradient descent ธรรมดาที่ใช้ full data
	- เมื่ออัพเดทเสร็จก็จะเอา batch ใหม่ที่ต่างกันมาใช้คำนวณต่อแล้วอัพเดท
	- เมื่อใช้ครบเราจะเรียกมันว่า epoch (ถ้าใช้ครบ 3 รอบ เรียก 3rd epoch)
	- เมื่อใช้ครบทั้ง full data เราก็จะรันใหม่
