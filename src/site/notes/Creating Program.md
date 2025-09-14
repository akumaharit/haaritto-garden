---
{"dg-publish":true,"permalink":"/creating-program/","created":"2025-09-14T21:39:04.058+07:00","updated":"2025-09-14T21:41:04.779+07:00"}
---

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