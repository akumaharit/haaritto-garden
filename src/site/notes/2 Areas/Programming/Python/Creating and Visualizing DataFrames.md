---
{"dg-publish":true,"permalink":"/2-areas/programming/python/creating-and-visualizing-data-frames/","created":"2023-02-12T22:00:45.545+07:00","updated":"2025-09-22T22:54:19.440+07:00"}
---

What is Matplotlib.pyplot
Pyplot is a Matplotlib module that provides a MATLAB-like interface.[[9\|9]](https://en.wikipedia.org/wiki/Matplotlib#cite_note-9) Matplotlib is designed to be as usable as MATLAB, with the ability to use Python, and the advantage of being free and [open-source](https://en.wikipedia.org/wiki/Open_source "Open source")


- select the columns and call `.hist()` then `plt.show()` to create a histogram adjust the bins using `bins` argument
- we use `.plot(kind="bar")` to plot bar graph and add title using `title="...."` argument 
- we can use `.plot(x="column name", y="column name",kind="line")` to plot line plots use `rot=45` to rotate the axis label
	- change `kind="scatter"` to plot scatter graph
- we can plot 2 graph เช่น `.hist()` ไปสองอัน แล้วก็ค่อย `plot.show()` มันก็จะแสดงกราฟออกมาสองอันแต่ทับกัน ทีนี้เราอาจแยกไม่ออกว่าอะไรคืออะไรก็ใช้ `plt.legend(["a","b'])` จะเป้นการใส่ legend ว่าอันนี้คือ a นะ อันนี้คือ b นะ
- ใน `.hist()` เราใส่ `alpha=0.7` ได้อันนี้คือการปรับให้โปร่งแสง 0.7
- NaN stand for "not a number"
- `.isna()` return boolean dataframe ว่า nan ไหมf
- ถ้าใช้ `.isnan().any()` ก็จะ return มาแค่ค่าเดียวของแต่ละ column ว่ามี nan ไหม `.isnan().sum()` ก็จะตอบได้ว่ามีกี่ตัว
- `.dropna()` จะเอา rows ที่มี nan ออกไป
- `.fillna(...)` จะเป็นการเติมพวกที่ nan ด้วยค่าที่ pass ไปให้
- เราสามารถ select หลาย columns แล้วเรียก .hist() ได้ด้วยนะ มันจะสร้าง histograph ของแต่ละ columns ให้
- การสร้าง dataframe ถ้าสร้างจาก list of dictionaries มันจะสร้าง row by row แต่ถ้าสร้างจาก dictionary of list มันจะสร้าง columns by columns
	- ![Pasted image 20230205215946.png|400](/img/user/3%20Resources/Attachment/Pasted%20image%2020230205215946.png)
	- ![Pasted image 20230205215955.png|400](/img/user/3%20Resources/Attachment/Pasted%20image%2020230205215955.png)
	- ![Pasted image 20230205220023.png|500](/img/user/3%20Resources/Attachment/Pasted%20image%2020230205220023.png)
	- ![Pasted image 20230205220028.png|500](/img/user/3%20Resources/Attachment/Pasted%20image%2020230205220028.png)
- `pd.read_csv`
- `pd.to_csv`
	- index = .. ไว้บอกว่าจะ export index ไปด้วยมั้ย
	- encoding ไว้ระบุ encoding แก้ปัญหาภาษาไทยเป็นเอเลี่ยนให้ใช้ 'utf-8-sig'