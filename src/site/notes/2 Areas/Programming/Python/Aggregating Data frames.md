---
{"dg-publish":true,"permalink":"/2-areas/programming/python/aggregating-data-frames/","created":"2023-02-12T22:00:51.180+07:00","updated":"2025-09-22T22:54:22.769+07:00"}
---

- Summary statistics
	- `df.mean, median, mode, min, max, var, std, sum, quantile, agg, cumsum, cummax, cummin, cumpod()` มันมี method หลายแบบและ return การคำนวณทั้ง column
	- `df.info()`
- `.agg()` เหมือนเป็น method ให้เรา pass statistics ที่เราอยากให้มันคำนวณเข้าไป สามารถใส่ได้หลายอัน เช่น `.agg([pct30, pct40])` อย่างอันนี้คือ function ที่จะคำนวณ quantile30 และ quantile40 ออกมา
- The `.agg()` method allows you to apply your own custom functions to a DataFrame, as well as apply functions to more than one column of a DataFrame at once, making your aggregations super-efficient.
	- An _aggregation_ summarizes your data as metrics, statistics, or other analytics.
``` python
# Import NumPy and create custom IQR function
import numpy as np
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)
# Update to print IQR and median of temperature_c, fuel_price_usd_per_l, & unemployment
print(sales[["temperature_c", "fuel_price_usd_per_l", "unemployment"]].agg([iqr, np.median]))
```
- Counting `.drop_duplicates(subset="column that you want a unique value")` สามารถใส่เป็น list ได้ด้วยนะ เพื่อให้มันดูทั้งสองอันเลย
- `.value_counts(sort=True)` อันนี้นับจำนวน sort ทำให้ค่าเยอะไปข้างบน ถ้าใส่ `normalize=True` argument เข้าไปด้วยมันจะ turn the counts to the proportion of total
- `.groupby('colname')` ใช้กับพวก categorical values ทำให้มัน group by value ของ column นั้น ๆ
- Pandas ก็มี Pivot Table นาจาา `.pivot_table(values="...", index="...", columns="...")` ปกติจะ return มาเป็น mean  ถ้าหากจะเปลี่ยนให้ใส่ argument เพิ่ม ได้แก่ `aggfunc=....` หากมีค่าที่เป็น NaN สามารถใส่ `fill_value` เข้าไปได้เพื่อให้มันเติมค่า NaN เป็นอย่างอื่น ถ้าใช้ `margins = True` มันจะใส่ column,row ขวาสุดหรือล่างสุดให้ เป็น mean of all values โดยจะไม่คำนวณค่าที่ missing
	- excel ทำยังไง ไอนี่ก็ทำแบบนั้นแหละ