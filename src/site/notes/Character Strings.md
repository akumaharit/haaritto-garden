---
{"dg-publish":true,"permalink":"/character-strings/","created":"2025-09-14T21:39:04.150+07:00","updated":"2025-09-14T21:41:19.950+07:00"}
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

telephone_num = phone_number+4(13). *** This mean starting from the 4 index length of 13 of phone_number will be assigned to telephone_num
country_code = phone_number+1(2). *** This mean starting from the 1 index length of 2 of phone_number will be assigned to country code
````