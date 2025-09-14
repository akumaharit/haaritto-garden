---
{"dg-publish":true,"permalink":"/basic-syntax/","created":"2025-09-14T21:39:04.065+07:00","updated":"2025-09-14T21:41:09.563+07:00"}
---

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