---
{"dg-publish":true,"permalink":"/2-areas/programming/python/transforming-dataframes/","created":"2023-02-12T22:00:51.235+07:00","updated":"2025-09-22T22:54:23.380+07:00"}
---

- pandas is built on numpy and matplotlib
	- numpy เรื่องการเก็บข้อมูล
	- matplotlib เรื่องการ visualize data
- rectangular data = tubular data
	- ใน pandas มันคือ "dataframe object"
	- R ก็เรียกมันว่า dataframe ส่วน SQL เรียก dataframe table
- `.head()` return first few row of dataframe
- `info()`
- `.shape` จะ return tuple of row and column
- `.describe()` summary statistics
	- count = non-missing value
- `.values` เอา data value มา return เป็น 2d numpy array
- `.columns` return column label
- `.index` มัน return เป็น index object (เพราะว่าในแต่ละ row เราจะ assign name ไปก็ได้ หรือจะใช้เป็นตัวเลขก็ได้
	- เรียนในคลิปถัดๆไป 
- `.sort.values()` ปกติ ascending = True by default
	- ใส่ list ที่ต้องการเข้าไป ("column") ถ้าอยากได้การ sort 2 อันเลย `(["columnA","columnB"], ascending=[True,False])` ทำนองนี้
- `df["column name"]` 
- `df[["columnA","columnB"]]` 
	- ในกรณีนี้ outer bracket ใช้ **subsetting**
	- inner bracket ใช้ list of column name ที่ต้องการ
- conditional subsetting
	- `df[   df["columnA"] > 20   ]`
	- ตัวข้างในสุดไว้สร้าง  true/value
- ถ้าอยาก filter ข้อมูลใน column หลายค่าให้ใช้ `.isin("value")` or `.isin(["valueA","valueB"])`
``` python
colors = ["brown", "black", "tan"]
condition = dogs["color"].isin(colors)
dogs[condition]
```
