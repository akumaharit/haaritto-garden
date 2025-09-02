---
{"dg-publish":true,"permalink":"/2-areas/programming/data-analysis/random-number-and-probability/","created":"2024-09-12T15:47:08.048+07:00","updated":"2025-09-02T22:59:45.095+07:00"}
---

**Sampling without replacement** -> เหตุการณ์เกิดพร้อมกัน
`df.sample(number_to_sample)` to pick random row from the dataframe
use `np.random.seed(number)` to assign seed

เหตุการณ์ Sampling without replacement จะบอกได้เลยว่าเป็น dependent event เพราะ each pack is dependent มันอาจเปลี่ยนไป จากผลของเหตุการณ์ก่อนหน้า เช่น สุ่มรอบแรกได้คนนี้ สุ่มรอบสอง โอกาสคนที่ยังไม่โดนก็จะเพิ่มขึ้น เพราะเอาชื่อของคนที่โดนสุ่มในรอบแรกออกไปแล้ว


**Sampling with replacement** -> เหตุการณ์เกิดไม่พร้อมกัน เช่น จะสุ่มผู้นำเสนอมาในงานประชุม วันนี้มีประชุม พรุ่งนี้ก็จะมีประชุมอีก ผู้ที่ต้องนำเสนอสามารถนำเสนอซ้ำได้
ใช้ `df.sample(number_to_sample, replacement = True)` so the same sample can appear more than once

เหตุการณ์ sampling with replacement ก็คือพบได้ใน independent event **(เหตุการณืไม่ได้มีความสัมพันธ์ต่อกันและกัน)** เช่น การสุ่มผู้นำเสนอมาในงานประชุม แม้วันนี้จะมีประชุม พรุ่งนี้จะมีประชุม จะกี่วันก็มีประชุม เขามีโอกาสที่จะโดนสุ่มออกมานำเสนอเท่า ๆ กันหมด เพราะไม่ได้มีการนำชื่อของเขา ออกจากกล่องสุ่มหลังจากสุ่มโดน


**A probability distribution** describes the probability of each possible outcome in a scenario.
When all outcomes have same probability: this distribution is called a **discrete uniform distribution**
![Random number and Probability.png|450](/img/user/3%20Resources/Attachment/Random%20number%20and%20Probability.png)
The expected value of a distribution, which is **the mean of a distribution**, เอาค่าที่เป็นไปได้มาคูณกับความน่าจะเป็นของมัน แล้วรวมกัน
- let's say we have a die where the two got turned into a three. This means that we now have a 0% chance of getting a 2, and a 33% chance of getting a 3. To calculate the expected value of this die, we now multiply 2 by 0, since it's impossible to get a 2, and 3 by its new probability, one third. This gives us an expected value that's slightly higher than the fair die. ค่าใหม่จะเป็น 3.67
![Pasted image 20240912171326.png|525](/img/user/3%20Resources/Attachment/Pasted%20image%2020240912171326.png)
**Law of large numbers,** which is the idea that as the size of your sample increases, the sample mean will approach **the theoretical mean (calculated mean of distribution)** 

