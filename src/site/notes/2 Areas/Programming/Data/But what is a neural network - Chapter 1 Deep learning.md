---
{"dg-publish":true,"permalink":"/2-areas/programming/data/but-what-is-a-neural-network-chapter-1-deep-learning/","created":"2023-02-12T22:00:51.151+07:00","updated":"2025-09-02T23:21:31.013+07:00"}
---


- มันเหมือนการพยายาม recognize ในส่วนเล็ก ๆ แล้วส่งไปยัง node ถัดไป ที่เอามารวม ๆ กันอีกทีนึง เช่น ตัวเลข ตอนแรกอาจเเป็นส่วนต่าง ๆ ของวงกลม จนได้วงกลม แล้วดูว่ามีขีดแบบไหน ลงล่างก็คือ 9 รึเปล่า ขึ้นก็อาจจะเป็น 6 รึเปล่า
- ตัวเลขใน neuron เราเรียกมันว่า "Activation"
- อย่างในคลิป เขาใช้ 784 neuron ใน first layer แต่ตรรกะการเลือกเขายังไม่ได้พูดถึง
- activation ใน layer นึงส่งต่อไปอีก layer นึงได้อย่างไร?
	- ใส่ weight เข้าไป
	- โดย node ถัดไปที่ถูกเชื่อมโดย node in first layer จะเป้นค่าอะไร ก็คือการเอาค่า activations * weight ของมันในแต่ละตัว แล้วรวมกัน
	- เราอาจดูค่าของ weight ก็ได้ เพื่อดูในภาพรวมว่าปัจจัยใด ส่งผลต่อปัจจัยใด
	- weighted sum อาจถูกบีบให้เล็กลงด้วย activation function (ทำไมถึงต้องใส่นะ มันช่วยเรื่อง non-linear ยังไง?) #tounderstand 
	- หากเราใส่ bias ไป เช่น ต้องการให้มัน activate ก็ต่อเมื่อ weighted sum > 10 เราเรียกว่า **bias for inactivity** สิ่งที่ทำก็คือการใส่ตัวเลขไป เช่น -10 ไปข้างท้ายของการคำนวณ weighted sum ก่อนเข้า activation function เช่น sigmoid(w1a1+w2a2+w3a3+....+wnan-10) เราเรียก 10 ว่า **bias** ซึ่งจะบ่งบอกว่ามันต้องสูงแค่ไหนมันถึงจะ activate โดย bias มันจะเป็นของแต่ละ activation function ของแต่ละ node มันอาจไม่ได้เป็นค่าเดียวกันในทั้ง network
	- learning ก็คือการเลือก weights and bias ให้ตอบโจทย์ที่สุด
- เวลาไปอ่าน paper เขาอาจเขียนเป็น matrix งี้
	- ![Pasted image 20221021150323.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021150323.png)
	- ![Pasted image 20221021150502.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021150502.png)	
	- การเขียนแบบย่อ
		- ![Pasted image 20221021150546.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021150546.png)
		- คลิปแนะนำให้ไปดู chapter 3 linear algebra เพราะจำให้เข้าใจ matrix มากขึ้น #tounderstand 
	- จริง ๆ 1 node ก็เหมือน 1 function
		- ![Pasted image 20221021150646.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021150646.png)
	- why relu มันดีกว่า sigmoid ? #toaskajball
		- sigmoid = old school 