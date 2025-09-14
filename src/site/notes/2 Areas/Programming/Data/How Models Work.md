---
{"dg-publish":true,"permalink":"/2-areas/programming/data/how-models-work/","created":"2023-02-12T22:00:51.224+07:00","updated":"2025-09-02T23:21:30.861+07:00"}
---

### Decision Tree
- Easiest to understand
- Basic building block for some of the best model in data science

### Terminology
- การ capture pattern จากข้อมูลเรียกว่า **fitting** or **training** the model
- ข้อมูลที่ใช้ **fit model** จะเรียกว่า **training data**
- พอ fit เพียงพอก็จะสามารถนำไปใช้ predict ได้
- หากเราอยากให้มันพิจารณา factor บางอย่างเข้ามาด้วย เราสามารถเพิ่ม **splits** มันได้ ทำให้มันเป็น **deeper** trees โดยตำแหน่งต่ำสุดที่เราไว้ทำ prediction เรียกว่า **leaf**
- **splits** และ **values** ในแต่ละ **leaves** จะถูกกำหนดโดย **data**

