---
{"dg-publish":true,"permalink":"/2-areas/programming/python/python-toolbox-python-data-science-toolbox-2/","created":"2023-03-18T22:17:46.531+07:00","updated":"2025-10-01T23:45:47.699+07:00"}
---

## Iterators

- อะไรที่ interate ได้ = interable
- ซึ่ง interable หมายถึงมี .inter() method
- ใน loop ตามจริงคือ loop จะสร้าง iterable โดยการสร้าง iterator object แล้ว
- interator คือ object ที่มี next() function ที่ให้ค่าถัดไปของมัน เช่น `iter(word)` แต่ถ้า `iter(*word)` มันจะ return all element ของ interator นั้น ๆ โดย star operator มีชื่อเรียกว่า spalt ถ้าเรา next จนมันสุด มันจะ return error

Recall from the video that an _iterable_ is an object that can return an _iterator_, while an _iterator_ is an object that keeps state and produces the next value when you call `next()` on it

**Googol** = 1 ตามด้วย 0 หลายร้อย (เป็นตัวเลขที่ใหญ่)
`range()` มันไม่ได้สร้าง list ให้มา มันแค่กำหนด range ให้ interator รุ้ว่ามันจะ limit ที่ไหน แต่เราสามารถใช้ `list()` เพื่อให้มันสร้าง list ได้ และยัง `sum()` ค่าใน list ได้อีกด้วยถ้าหากเป็น `int`

`enumerate()` เป็น class ที่จะทำให้ iterable กลายเป็น tuple ที่คู่ระหว่าง element ใน iterable กับ index ที่ตัว function มันสร้างขึ้นมาเอง 

เวลาจะ loop ใน enumerate เช่น `for index, value in enumerate(avengers)` เรายังสามารถกำหนด start ได้ด้วยเช่น `(avengers, start=10)`

enumerate object cannot be printed, but can be transform to list before printing (use list()

`zip()` จะสร้าง zip object ที่จะเป็น iterator ของ tuples อีกที โดยหลังแปลง zip เป็น list แล้วจะพบว่ามันจะมีหลาย tuple ด้วยกัน โดยใน tuple แรก ก็จะประกอบไปด้วย first elememt ของแต่ละ list ก่อนที่เราจะ zip มัน

เวลา `pd.read_csv` เราสามารถกำหนด chunksize ได้หากเรากลัวว่าโหลดทีเดียวมันจะไม่ไหว ซึ่ง object ที่สร้างจากการ call `pd.read_csv` ก็จะกลายเป็น interable ของ chunksize นั้น ๆ
## List Comprehension

![Pasted image 20230216113147.png|500](/img/user/3%20Resources/Attachment/Pasted%20image%2020230216113147.png)
- ต้องประกอบไปด้วย
	- Iterable
	- Iterator Variable (ก็คือตัวแทนของแต่ละสมาชิกใน iterable)
	- Output expression

Generator ก็คือ List Comprehension แต่เปลี่ยนจาก [] เป็น () ซึ่งตัวมันเองจะไม่ใช่ list และจะไม่ได้สร้าง list ขึ้นมาเวลา assign แค่มันจะเป็น object ที่สามารถ iterable ได้ โดยอาจใช้ for-loop หรือจะ ใช้ list() ก็ได้เพื่อสร้าง list จาก generator หรือจะใช้ next() function ก็ได้

Generator function คือ function ที่ทำให้เกิด generator object ขึ้นมา และจะใช้ yield แทน return



the command `with open('datacamp.csv') as file` as datacamp binds the csv file 'datacamp.csv' as datacamp in the context manager. Here, the with statement is the context manager, and its purpose is to ensure that resources are efficiently allocated when opening a connection to a file.