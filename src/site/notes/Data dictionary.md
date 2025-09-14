---
{"dg-publish":true,"permalink":"/data-dictionary/","created":"2025-09-14T21:39:04.143+07:00","updated":"2025-09-14T21:41:15.623+07:00"}
---

### Data dictionary
- ABAP Dictionary: t-code se11
- Transparent Table, Calista Table, Pool Table
- Inside the table, you can create field for the table.
	- The field, will contain the name (no need to Z or Y) BUT for the **data element** which specify the semantic meaning (including search help, labels) and technical type that field, you have to adhere customer naming space
		- Field Labels is what APPEAR as a label for that field. (you have to specify, short, medium, long and heading.)
	- **Domain** specify technical attribute (data type, length, possible data value)
		- Domain allow you to specify possible data value via -> **Single Value**, **Intervals (if it is in sequence)** or **Value Table** (in case of value table, you have to specify foreign key for that table)
- Before creating table, you have to specify **Technical Settings** for the table.
	- Data class
	- Size Category
	- Buffering: if not allowed -> will not allow the table to be read in advance (only turn on buffer if the table is updated infrequently.)