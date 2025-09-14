---
{"dg-publish":true,"permalink":"/2-areas/programming/sap/sap-abap/","created":"2025-09-14T21:38:11.772+07:00","updated":"2025-09-14T21:49:50.834+07:00"}
---

### Intro
https://www.tutorialspoint.com/sap_abap/index.htm
SAP run with its SAP kernel, SAP code is stored in the SAP database (not an external file like other programming language)

![Object Directory Entry Prompt.png](/img/user/3%20Resources/Attachment/Object%20Directory%20Entry%20Prompt.png)

 Any change you do through SAP will prompt you to create object directory, choose the "development class" to choose the transport route that we want to use for the development. IF you don't want to transport it anywhere, just click 'local object'
 - Anytime you use local object, it will be automatically assigned development class to `$tmp`
 - When activating the objects, ALWAYS active one object at a time #tounderstand 
 - Everytime you **ACTIVE** the object, it will automatically **SAVE** the object before activating.


### Creating Program
ABAP editor: se38
- Best practice is to start with Z or Y for custom program (not SAP standard)
- When creating program,
	- Type: executable program mean that the program can be execute without t-code and can be run as background job
	- Status and Application are used as an information field.
	- Turning on editor lock will prevent the program from being edited.
	- Fixed point arithmetic will allow decimal (if not ticked, it will be rounded to whole number)
	- Unicode code check, always turn this open so it check for... 
- t-code: `ABAPDOCU` to open ABAP DOCUMENT
### Basic Syntax
- `REPORT` always the first of the program.
	- The report automatically `...LINE-SIZE 132` and will automatically break line for write statement
	- IF you want to break new line in the write statement, use `/` in the `WRITE` statement to break new line.
- Use `WRITE` to print to the report (USE `WRITE / VALUE` to also add new line before printing that value.)
- Statement always begins with `keyword` and end with `period`
- You can use `: and ,` to change statement together if it use the same keyword.
- Partial Line comment start with `"`  and Full line comment are indicated via `*` (if `*` is not in the first column it will not work.)
	- Use CTRL + < to comment the highlighted line
- Insert blank line via `SKIP 1`, you can change the number of line to add
- `ULINE` to insert horizontal line

- Declaring Variable and using Suppressing Blank

``` 
DATA: W_NUR(10) TYPE N. 
	  MOVE 50 TO W_NUR. 
	  WRITE W_NUR NO-ZERO.
```

- This declare a variable "W_NUR" with length of 10 type = number, and assign value '50' to a variable 'W_NUR' then WRITE with NO-ZERO to suppress all leading zeros of a number field.

- `MESSAGE` command to display message defined by message ID.

``` 
MESSAGE 'คุณกำลังเข้าสู่บริการรับฝากหัวใจจจ' TYPE 'I' DISPLAY LIKE 'E'.
```

This will display the message with the type of "Information", but the appearance will be like 'Error'

![ABAP Message Type.png](/img/user/3%20Resources/Attachment/ABAP%20Message%20Type.png)

- To read the table data into temporary structure use `TABLES <table name>` and then use `SELECT <selection> FROM <table name>.` to select the data, the SELECT is a loop so dont' forget to end with `ENDSELECT.` too
	- `SELECT` will loop each row of the table, to access the field of the table just simply use `<table name>-<field name>`
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

### Variable Declaration
- Use `DATA <name> TYPE <type> VALUE <val>` to define the variable
	- add VALUE if you wanted to assign the value to that variable when declaring it.
	- In case if the number is decimal, you have to put quotes (' ') so it don't interpret the period ( . ) as a termination.
- `DATA d2 LIKE d1`, will make D2 with the same data type as d1 **WARNING, this does not assign the variable's value, use "MOVE" for the assign.**
	- you can also declare variable with the same data type of the field in the table `DATA d2 LIKE <tablename>-<fieldname>`
- `MOVE d2 TO d1`, this will assign d2 value to the d1. (d1 = d2)
- **in SAP the variable is also called "FIELD' if it is from table**

- There are three types of the variable, **static variable**, **references variable** and **system variables** #tolearn

**Literals** are unnamed data objects that you create within the source code of a program.

**Constants** are named data objects created statically by using declarative statements. The value assigned to constants cant be changed during the execution of the program.
- DATA is almost the same as CONSTANTS (same syntax too!) except that, you cannot change the value of the CONSTANTS //it is a **must** to use also include `VALUE` during the constant declaration.
- You cannot define constant for, XSTRING, References, Internal table, structure containing internal tables
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
### Arithmetic Calculation and Conversion
- Very simple, however there is also keyword for calculation.
- `ADD 8 to result.` There is also `SUBSTRACT, DIVIDE, MULTIPLY`
- There is in-built conversion in SAP (almost same as Python)
- There are 3 way to division
	- use / (standard division)
	- use DIV (integer division)
	- use MOD (remainder division
### [[2 Areas/Programming/SAP/Character Strings\|Character Strings]] this note seems to be the broken one :(
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