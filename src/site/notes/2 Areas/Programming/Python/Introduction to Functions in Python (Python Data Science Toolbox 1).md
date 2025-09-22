---
{"dg-publish":true,"permalink":"/2-areas/programming/python/introduction-to-functions-in-python-python-data-science-toolbox-1/","created":"2023-03-18T22:17:46.507+07:00","updated":"2025-09-22T22:49:38.477+07:00"}
---

## User defined function

- Function Headers
- Function Bodys
- Docstrings: documentation for function
	- Placed under function header in triple double quotes "" "" ""     "" "" "" 
- Beware, some variable can be `NoneType` datatype (เวลา assign เช่น x = print("brabra")) x จะเป็น `NoneType`
- เวลา call function สิ่งที่อยู่ใน () อย่าลืมว่าเราเรียกมันว่า arguments แต่ถ้าตอน define function เราเรียกมันว่า parameter
- tuple define ด้วย () ข้อเสียคือ immutable มักมาใช้เวลาจะ return value จาก function

โ้คดอันนี้ก็คือเหมือนการเช็คว่ามีใน dict ยัง ถ้าไม่มีให้ add มันเป็น key แล้วบวกค่าเข้าไปทีละ 1 ถ้าเกิดมันมีอยุ่แล้วใน dict
```python
# Import pandas
import pandas as pd
# Import Twitter data as DataFrame: df
df = pd.read_csv('tweets.csv')
# Initialize an empty dictionary: langs_count
langs_count = {}
# Extract column from DataFrame: col
col = df['lang']
# Iterate over lang column in DataFrame
for entry in col:
    # If the language is in langs_count, add 1
    if entry in langs_count.keys():
        langs_count[entry] += 1
    # Else add the language to langs_count, set the value to 1
    else:
        langs_count[entry] = 1
# Print the populated dictionary
print(langs_count)
```

Scopes หมายถึง part of program where name or object is accessible
Functions scope:
- Global scopes defined in main body of the scripts
- Local Scopes: ใช้ใน functions หลังจากนั้นก็จะ access ไม่ได้แล้ว
- Built-in เป็น predefined buitls in module

เวลาเรียกใช้ functions มันจะดู variable ใน local scope ก่อน ถ้าหากไม่มีมันก็จะไปดูที่ global หากไม่มีทั้งคู่ก็จะไปดูของ built-in scope
ถ้าอยู่ใน local scopes และอยากให้มัน access global ให้ใช้ `global` เช่น
``` python
test = 2
def square():
	global test
	test = 10
	return test
square()
#กรณีนี้มันจะ return 10 มาให้จ้าเพราะเราสั่งไปแล้วว่าอยากได้ test จาก global นะ
```
to query builtins module, you have to import builtins first

ถ้าในกรณีที่มันเป็น nested functions, มันจะ search local function ของมันก่อน แล้วค่อย search enclosed function (ถ้ามี)
ถ้าต้องการให้มัน access ของ enclosed function ให้ขึ้นต้นด้วย `nonlocal`


![Pasted image 20240920163135.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020240920163135.png)
สรุป มันจะค้นหาไล่จาก LEGB
- Local
- Enclosing function
- Global
- Builtins

assigning default parameters that are used when not specified: ให้ assign ค่า parameter นั้น ๆ ตอน def function ได้เลย
หากเราใช้ `*args` เป็น parameter ตอน define function มันจะรับ **positional arguments** มาเก็บใน args ซึ่งเป็น tuple
หากเราใช้ `**kwargs`  มันก็จะเป้นแนวเดียวกัน แต่จะรับ **keyword arguments** และรอบนี้จะเป็น key-value pair ใน dictionary เช่น `def printall(**kwargs) แล้วเรา printall(name="Tets",job="lol")`
**สำคัญ** จริง ๆ จะใช้อะไรก็ได้ แต่ปกติ args และ kwargs เป็น default ที่ใช้ ๆ กัน
Note: arguments =/= parameters! ดังนั้น argument หมายถึงตอนที่เรากำลังจะใส่มันเข้าไป ซึ่งใส่ได้สองแบบ ใส่แบบ positional or keyword


เราสามารถเขียน function แบบเร็ว ๆ ได้โดยการ assign variable ให้มันเป็น lambda เช่น
`raise_to_power = (lambda x,y : x**y)`
นอกจากนั้นแล้ว function `map(func, seq)` จะ apply func ไปในทุกค่าใน seq แล้ว return map ออกมา ดังนั้นถ้าจะดูค่าใน sequence ให้แปลงเป็น `list` ด้วยโดยใช้ `list()`

The function `filter()` offers a way to filter out elements from a list that don't satisfy certain criteria. โดยรับเหมือน map คือ func,seq.

The `reduce()` function is useful for performing some computation on a list and, unlike `map()` and `filter()`, returns a single value as a result. To use `reduce()`, you must import it from the `functools` module.

## Error Handling

Error caught during execution = exceptions
ก็คือ `try กับ except นั่นแหละ` เราสามารถเลือกได้ว่าจะ catch except อะไรเช่น `except TypeError:`
เราสามารถ explicitly raise error ได้ด้วยโดยการใช้ `raise` แล้วเลือกว่าจะให้ error อะไรเช่น `raise ValueError('x ต้องไม่ติดลบ')`
