---
{"dg-publish":true,"permalink":"/2-areas/programming/deep-learning/what-is-backpropagation-really-doing-chapter-3-deep-learning/","created":"2023-02-12T22:00:51.421+07:00","updated":"2025-09-02T23:21:30.877+07:00"}
---

**Topic:** What is backpropagation really doing - Chapter 3 Deep learning
**Alias:**
**Tags:**
**Links:** https://www.youtube.com/watch?v=Ilg3gGewQ5U&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&index=4
**Creation Date**: 2022-10-21 16:37
**Modification Date:**  2022-10-21 16:37

- ค่าของแต่ละตัวใน cost function หากมีค่าสูง มันก็คือมีผลต่อ average ค่อนข้างเยอะ ดังนั้นหากเราจัดการกับตัวนั้น (ก็คือ weight นั้น / edge นั้น มันก็จะส่งผลต่อภาพรวมได้เยอะ มากกว่าตัวที่มี weight น้อยกว่า)
	- ![Pasted image 20221021163824.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021163824.png)
- อย่าลืมว่าค่า MSE (ก็คือ cost function) ที่คำนวณออกมา มันคือค่าของแต่ละ datapoint เท่านั้น! เวลาเราปรับ weight มันก็จะขึ้นกับแต่ละ datapoint เลยว่ามันจะทำให้เกิดผลอย่างไร
- ลำดับการใส่ข้อมูล (datapoint) เข้าไปเพื่อ forward propogation ถ้าหากเราใช้ลำดับ datapoint ที่มันต่างกัน ตัว final parameter ต่าง ๆ ที่เราได้มา จะเปลี่ยนไปด้วยมั้ยถ้าเราเปลี่ยนลำดับ #toaskajball 
- เวลาเรา nudge ค่า activation ใด ๆ ถ้าหากมันห่างจากความเป็นจริง เราก็คงอยากให้ proportion การ nudge มันเยอะ มากกว่าตัวที่มันน้อย
	- ![Pasted image 20221021164312.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021164312.png)

- ในการ nudge ค่า activation เรา่สามารถทำได้สามทาง คือการปรับ activation ก่อนหน้า คือ weight หรือ bias และอย่าลืมว่า activation ที่มีค่ามาก ถ้าเราไปปรับ weight มัน มันก็จะยิ่งส่งผลมากขึ้นด้วย (และอย่าลืมว่า เราไม่ได้สนใจว่าตัวไหนจะเพิ่มหรือลด เราสนใจแค่ว่า ทำยังไงก็ได้แหละให้มัน predict สิ่งที่เราต้องการได้)
	- ![Pasted image 20221021164653.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021164653.png)
	- ภาพประกอบบ่งบอกว่า node ที่เข้ม ถ้าไปปรับ weight มันมันก็จะยิ่งส่งผลมากขึ้น ซึ่งตรงนี้สอดคล้องกับ Hebbian Theory ว่า Neurons that fire together wire toghet ก็คือเซลล์ประสาทไหนที่มัน fire พร้อมกัน มันจะทำให้ connection ตรงนั้นยิ่งแข็งแกร่งมากขึ้น
	- ทุก output มีผลต่อ second-last layer ว่าจะเปลี่ยนเป็นอะไร
		- ![Pasted image 20221021165812.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020221021165812.png)
		- หลังจากที่ค่ามันเปลี่ยนแล้ว เราสามารถ recursively (ทำซ้ำ) ให้กับ node อื่น ๆ ที่อยู่ก่อนหน้า second-last layer ได้ เพื่อปรับ bias / weight ของมัน และสิ่งนี้แหละเรียกว่า[[2 Areas/Programming/Deep Learning/Optimizing a neural network with backward propagation\| Back Propagation]]
		- การคำนวณทั้งหมด มันใช้เวลาค่อนข้างเยอะ จึงมีการใช้ [[2 Areas/Programming/Deep Learning/Optimizing a neural network with backward propagation#^fc761b\|Stochastic Gradient Descent]] เพื่อลด computation time 