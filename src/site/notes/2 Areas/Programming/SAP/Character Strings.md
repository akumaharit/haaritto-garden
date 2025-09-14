---
{"dg-publish":true,"permalink":"/2-areas/programming/sap/character-strings/","created":"2025-09-14T21:48:53.732+07:00","updated":"2025-09-14T21:49:54.780+07:00"}
---

### Character Strings
- Concatenating string fields: `CONCATENATE <variable1> <variable2> ... <variablen> INTO <destination> [separator by sep].` For example, `CONCATENATE title surname forename INTO destination.`
	- By just using `DATA sep.` will declare STRING with 1 character and default value of space.
- Condensing character strings: `CONDENSE <variable> [NO-GAPS]` This will condense the spacebar into just 1 spacebar and save into the same variable. If `NO-GAPS` is specified, there will be NO spacebar.
- Finding the length of the string: `STRLEN(<variable name to check for length>)`
- Replacing character strings. `REPLACE <string to be replaced> WITH <string to replace> INTO <variable to process the replacing>.` For example `REPLACE ',' WITH '.' INTO surname2.`
	- **THIS only replace the first occurrence of the string,** if you wanted to replace all you have to use loop
- Searching for specific characters `SEARCH <string to be searched> FOR <string to search>.`
	- System variables are used to return
	- `<string to search>`
		- You can use wildcard `*` If you input like `'.Joe        .'` (add the period) it will take blank space into account.
	- `SY-SUBRC` to specify if the search success or not
		- 0 = successful
		- 4 = not successful
	- `SY-FDPOS` to specify the position of the found string.
		- To specify the FIRST character of the term found, add +1
		- เช่น Mr Joe Smith ค้นหาคำว่า "Smi*" จะ Return 7 แต่มันเริ่มต้นจริง ๆ 8 (ตัว S)
- Shift Statement `SHIFT <string> LEFT DELETING LEADING '0'.` This will shift to the left (align left) and remove the leading '0'.
	- If you use just `SHIFT`, it will by default shift from right to left 1 character.
	- If `SHIFT <string> CIRCULAR.` it will shift and place the removed string to another side.
- SPLIT Statement `SPLIT <string> AT <seperator> INTO <variable1> <variable2> ... <variablen>.'
	- Please note that for the variable that will store the string after spliting, it will fill BLANK space in front and in the back to the total length of variable's length
	- If there are more to be split but **the variables to spilt into is full**, the rest of the string will be assigned to the last variable.
- Subfield (referring to a specific character in the field or variable)

```
DATA phone_number(17) VALUE '+44-(0)207-123456'.
DATA country_code(3).
DATA telephone_num(14).

telephone_num = phone_number+4(13). This mean starting from the 4 index length of 13 of phone_number will be assigned to telephone_num
country_code = phone_number+1(2). This mean starting from the 1 index length of 2 of phone_number will be assigned to country code
```


### Debugging
- Single Step (F5): go line by line single step
- Execute (F6): execute function module or form or independent section of code
	- mostly used for standard module, so it just execute the entire module (which we know that it won't be error)
- Return (F7): it is life saving if we forgot to use execute and we just accidently step in the function or the module, just use Return (F7) so it run the remaining code within that specific function or module.
- Continue (F8): continue your program without line by line
- You can investigate the internal table by double clicking on the table -> it will then open the table in "Structures" tab.
- You can also investigate breakpoint and watchpoint you set in "Break./Watchpoints" tab.
- You can add `BREAK-POINT.` to the code if you want the program to break into debugger when executed.
- Watchpoint is used to monitor for the variable's value and
- If there is a error, debugging will end. To stop debugging, you can also use the menu bar Debugger -> Restart, it will return to the main screen, you can simply press Debugging and it will restart the debugging session.
### System Field
- belong to table `SYST`
- system field will contain the value dependent to the statement executed
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