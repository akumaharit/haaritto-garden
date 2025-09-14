---
{"dg-publish":true,"permalink":"/2-areas/programming/data/summary-statistics/","created":"2024-08-17T11:53:00.181+07:00","updated":"2025-09-14T20:28:16.746+07:00"}
---

**Statistics:** practice and study of collecting and analyzing data
**Summary statistics:** a fact or summary of some data

**Type of Statistics**
- Descriptive: Describe and Summarize, ex: 25% go to work by bus
- Inferential: use sample data to make **inferences** about larger population

**Data Type**
- Numeric (Quantitative)
	- Continuous (Measured)
	- Discrete (Counted)
- Categorical (Qualitative)
	- Nominal (Unordered): Married/unmarried, Country of Residence
	- Ordinal (Ordered): เช่น คะแนนความพึงพอใจเวลาทำ survey 1-5
	- Categorical can be represented as numbers, but this doesn't make it numeric variables.

**Measure of Center**
- mean is more sensitive to outliers than median
- mode is more often used for categorical data

**Variance and standard deviation**
- average distance between all datapoints and mean
- variance is squared
- `np.var(...[...], ddof = 1)` -> ddof = 1 for sample variance, ถ้าไม่ใส่จะเป็น population variance
- `np.std(...[...], ddof = 1)`
- SD penalize longer distance than the shorter one, however, mean absolute deviation penalize each distance equally

**Quantiles**
- `np.quantile(...[...], 0.5)` -> is equally to median
- โดย 0.5 อาจใส่เป็น list หรือใช้เป็น  `np.linspace(start,stop,num)` ก็ได้เพื่อให้มันคำนวณ quantile เป็นช่วง ๆ

**Interquartile range (IQR)**
- height of the box of boxplot (75% - 25%)

**Outliers**
![Pasted image 20231030225936.png|650](/img/user/3%20Resources/Attachment/Pasted%20image%2020231030225936.png)
- `data < Q1 - 1.5 x IQR` OR `data > Q3 + 1.5 x IQR` ถือเป็น outliers.

**Variances**
average of distance of the datapoint to the mean
- subtract mean from each datapoint, square each data and then add them all together
- divide sum with number of data point - 1
**standard deviation (SD)** = square root of the variance // เข้าใจง่ายกว่าเพราะหน่วยไม่ติด square
**mean absolute deviation (MAD)**  = penalizes each distance equally, แต่ SD จะมี square ทำให้อะไรที่มันยิ่งยาวจะยิ่งถูก penalize เยอะ
- subtract mean from each datapoint, add absolute and then find mean of it.
ไม่ได้มีอะไรดีไปกว่ากันระหว่าง SD vs MAD แต่ SD พบได้บ่อยกว่า
0.5 quantile = mean
IQR = 0.25 - 0.75 quantile
นอกจากจะคำนวณแยกด้วยการใช้ np.quantile ยังสามารถใช้
```python
from scipy.stats import iqr
iqr = iqr(sleep['bodywt'])
lower_threshold = np.quantile(sleep['bodywt'],0.25) - 1.5 * iqr
upper_threshold = np.quantile(sleep['bodywt'],0.75) + 1.5 * iqr
sleep[(sleep['bodywt'] < lower_threshold) | (sleep['bodywt'] > upper_threshold)]

```
**outliers**
datapoint is an outlier if: `data < Q1 - 1.5 x IQR` or `data > Q3 + 1.5 x IQR`
**general**
`sleep['bodywt'].describe()`