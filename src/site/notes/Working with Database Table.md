---
{"dg-publish":true,"permalink":"/working-with-database-table/","created":"2025-09-14T21:39:04.156+07:00","updated":"2025-09-14T21:41:26.323+07:00"}
---

### Working with Database Table
- Always make a copy of existing database table before you make any change to migrate risk of loss. Don't forget to activate the table after copying. (ps. No need to reactivate the data element and domain.) When ever you copy the table, it only copy the structure not the actual data.
- Pre-existing domain:
	- char01, char03 (the number is length)
	- curr9 (currency)
- Pre-existing data-element
	- When working with the currency (data type CURR), you have to specify the currency key field
	  ![Pasted image 20250420145301.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020250420145301.png)
	- To enable error-checking (valid data-entry) for the currency key, you can add "foreign key" to enable to drop-down (BECAUSE the CURCY data element, contain the domain that use "VALUE TABLE" for value range checking.
	- CURCY (currency key field)
- Creating foreign create
	- When creating foreign key for the field that has the domain that contain 'value table' for value range checking, you will have option if it should check for all of the 'value table' table's key (in this case, I only wanted it to check for the WAERS field) so I just remove the foreign key table and foreign key field then of the MANDT and tick GENERIC
	  ![Pasted image 20250420150552.png|575](/img/user/3%20Resources/Attachment/Pasted%20image%2020250420150552.png)
- Naming convention for append structure and include structure (for anything not SAP standard)
	- USE ZZ in front of the component, because it is not a part of the MAIN structure.
	- Use Z in front of component type
- Why use append structure? -> **Preferred method of maintain SAP delivered tables.**
	- To make change to the existing (mostly the SAP standard table, also often used for customer specific table), we often use "append structure". Because if the SAP updated and added the field, our customized fields could get overwritten by those new fields that SAP have added. That's why we should use append structure rather than making change to the existing structure.
	- Most commonly used name is: (table = `ZEMPLOYEES`, append structure = `ZAZEMPLOYEES2`)
	- Specify enhancement category for the table to allow it to be appended via
	  ![Pasted image 20250420162617.png](/img/user/3%20Resources/Attachment/Pasted%20image%2020250420162617.png)
	- When adding append structure, you have to specify "Component Type", double click and it will pop-up, select "data element", and the rest goes the same as creating the normal table.
- Include structures,
	- Edit -> Include -> Insert
	- it is like **append structure but it is reusable in the other ABAP program, dynos, structure**. 
	  However, it must be flat structures (cannot contain additional structure in them), and the field in flat structure can only be 16 length.
	- When adding include, it will appear ABOVE the cursor rows.
- Changing Key Fields.
	- Adding key field is not dangerous, but changing and deleting IS, because when changing the key fields, it will also apply change to the database.
	- Removing key fields will always result in an ERROR when activating in SE11, you have to go for SE14 to activate and adjust change to the table.