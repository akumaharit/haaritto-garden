---
{"dg-publish":true,"permalink":"/data-type/","created":"2025-09-14T21:39:04.066+07:00","updated":"2025-09-14T21:41:11.430+07:00"}
---

### Data Type
- STRING = String for any character length
- C = Predefined character length for string (ex. `DATA text_string TYPE C LENGTH 20` OR `DATA text_string(20) type C` , the latter one are old SAP syntax.), default value is space
	- THIS IS default Data type for the SAP, such as `DATA thevariable(20)`, this will automatically translate into the same as `DATA thevariable TYPE c LENGTH 20`
- N = predefined number length (NO INTENTION TO CALCULATE IT!)
	- It is actually NUMC, and the default value is 0
- D = Date
- I = Integer
- F = Floating Point
- p = packed decimal
	- `DATA packed_demical01 TYPE p DECIMALS 2.` you can specify decimal to store via `DECIMALS`
In ABAP, there are also "arrays" but it is called 'internal tables' in ABAP. (it is a table stored in memory)