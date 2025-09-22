---
{"dg-publish":true,"permalink":"/2-areas/programming/python/slicing-and-indexing-dataframe/","created":"2023-02-12T22:00:46.148+07:00","updated":"2025-09-22T22:54:21.914+07:00"}
---

![Pasted image 20240920154833.png|625](/img/user/3%20Resources/Attachment/Pasted%20image%2020240920154833.png)

- `.set_index` และ `.reset_index` โดยที่ `.reset_index(drop=True)` จะทำให้มันทิ้ง index ของมันออกไปเลย
- `.set_index` สามารถใส่เป็น list ได้ โดยจะจัดเป็น multi-level indexes or hierarchical index (synonymous terms)
	- กรณีนี้การ subset จะใช้ list of tuple โดย tuple ใช้เลือกเอา อันแรกเป้น outer-level comma แล้วอันสองเปเ็น inner-level
- การตั้ง index ให้เป็นชื่อบางอย่าง มันทำให้เราสามารถใช้ .loc (เลือกตาม index value) แล้วใส่ชื่อมันเข้าไปเลยได้ ในการเรียก rows ต่าง ๆ ออกมา
- index ไม่จำเป็นต้อง unique
- `.sort_index`. ปกติจะ sort from outer to inner index in ascending order
	- ![Pasted image 20230205171733.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020230205171733.png)
- You can also slice using custom index you set, however it only work in outer level of the index! If you want to also select the index, you must pass two tuple as said above. ระวัง! สมมุติ A:C อันีนี้คือมันจะมาทั้ง A B C เลยต่างจาก 0:2 ที่เอาแค่ 0 1
- เราสามารถ subset columns ได้ด้วย หมายเหตุ: เวลา slice พวก list อะไรพวกนี้ colon มันจะหมายถึง **keep everything** ซึ่งต่างจากตัวเลข
- ถ้าตั้ง date เป็น index เราสามารถ slice date ได้ด้วยนะ! ยังสามารถ slice partial date ได้ด้วย เช่น 2012:2013
- อย่าลืมนะว่าบนโลกนี้เรายังมี `.loc` อยู่แต่สำหรับ dataframe  มันจะมี 2 อันก็คือ `[2:3, 2:4]` หมายถึง row 2 และ column 2, 3
``` python
# Sort the index of temperatures_ind
temperatures_srt = temperatures_ind.sort_index()

# Subset rows from Pakistan to Russia
print(temperatures_srt.loc["Pakistan":"Russia"])

# Try to subset rows from Lahore to Moscow
print(temperatures_srt.loc["Lahore":"Moscow"]) #อันนี้จะ return nonsense! เมื่อไหร่ก็ตามที่ต้องการจะ subset inner index จะต้องใส่เป็น tuple โดยอันแรกหมายถึง outer level

# Subset rows from Pakistan, Lahore to Russia, Moscow
print(temperatures_srt.loc[("Pakistan","Lahore"):("Russia","Moscow")])
```
- Be careful when using Boolean conditions to subset dates. Using a check like `df['date'] == '2011'` or `df['date'] <= '2011'` will **not** check for all dates in 2011, and will **only** check for the date `2011-01-01`. Write out the full date when using Boolean conditions (e.g. `2011-12-31`).
- `axis = "index"` หมายถึงคำนวณ statistical summary ของแต่ละ columns
- `axis = "columns"` หมายถึงคำนวณ statistical summary ของแต่ละ  row