# CPE 357 - 06 - Tools => gdb, C Preprocessor, make

Class: [[]]
Date: 10-16-2023
Teacher:
___
## Notes

### Breakpoints
- Breakpoints can be used to pause your running program at a designated point
- The command "break" sets a breakpoint at a specified file-line pair
- (gdb) break program.c:23
	- Sets a breakpoint at line 23, of program.c. When the running program reaches that location, gdb will pause and prompt you for another command.
- (gdb) break my_function
	- Break any time the function my_function is called
	- 