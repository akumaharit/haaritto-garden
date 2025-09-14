---
{"dg-publish":true,"permalink":"/debugging/","created":"2025-09-14T21:39:04.152+07:00","updated":"2025-09-14T21:41:21.907+07:00"}
---

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