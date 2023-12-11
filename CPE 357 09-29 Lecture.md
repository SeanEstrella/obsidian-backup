# CPE 357 09-29 Lecture

Class: [[]]
Date: 09-29-2023
Teacher:
___
## Notes

### Data Type Qualifiers (Continued)
These allow fine grain control:
- static: link now
- register: store value in a CPU register, if possible
- **extern** extern declarations (for variables in libraries)
- **volatile** for things that change by themselves
- **restrict** promises no aliasing
### C Data Structures
- **Arrays** are contiguous chunks of memory
	- no default initialization
	- no bounds checking (length not stored)
- C-strings: are null-terminated arrays of characters
	- char x[] = "hi"
	- **[string.h](https://man7.org/linux/man-pages/man0/string.h.0p.html) has helpful library/utility functions**
### C Filenames
- .c C source file      
- .h Header file
	- type definitions, prototypes and declarations
- **.o / a.out**: Compiled object file
### C Program Layout (* .c)

```c
#include <system_header.h>  
#include "local_header.h"

#define macro_name macro_expr  
  
/* declare functions */  
/* declare external variables & structs */

int main(int argc, char* argv[]) {  
/* the code */  
}
```

### The main() function
```c
int main(int argc, char* argv[])
```
- argc: contains the count of arguments on the command line
	- Executable name counts as one, plus one for each argument  
- argv: is an array of the arguments as strings 
- Example:
```bash
$ ./a.out 14 hi
```
```c
argc = 3
argv[0]="./a.out", argv[1]="14", argv[2]="hi"
```
### Error Handling in C
- No built-in exception handling (no try/catch)
- Errors are returned as integer error codes from functions
	- Error handling is inelegant
	- CONSTANT_NAMES are defined to avoid "magic" integer values – need to look up in documentation**
- Global variable **errno** holds value of last system error
### Error handling
- Processes exit (e.g., return from main) with status code
-  Standard codes found in stdlib.h:
	- EXIT_SUCCESS (usually 0) 
	- EXIT_FAILURE (non-zero)
-  "Crashes " trigger signals from OS (e.g., SIGSEGV for segfault)
### C Functions
- Parameters: all passed by value  
- Function declarations (prototypes)
	- Specifies function arguments and return type 
	- Example: int power(int base, int n);  
- Function definitions
### Function Declaration vs. Definition
- Declaration
	- Function prototype, external variable declaration
	- Often placed in header files (.h) incorporated via \#include
	- Should appear before first use in all files that use the function  
- Definition
	- Code for function, or variable definition that creates storage
	- Must be exactly one definition of each thing (no duplicates)**
### Function Declaration vs. Definition
```c
// function definition
// power: raise base to n-th power; n ≧ 0
int power(int base, int n) {
	int i, p;
	p = 1;
	for (i = 1; i ≤  n; ++i) {
		p = p * base;
	}
	return p;
}
```


**![](https://lh3.googleusercontent.com/DGNMOcIMplk4Y288G1OnIIru7PBkGdmoNerXADfUy1kA7_zX8pvVPKVlXsdptWTgzeBEPgMqQTGej0O7EG66aiYZsqMlDlxmcYAndyXjYtZjycUDy2j5lU86_CUGnsm5DYAbVv8P7rr1cNrQ9GkNaXGa7A=s2048)**

### System Calls and Library Functions
- System call: entry point directly into the kernel
	- Linux provides ~400 system calls
	- Exposed as regular C functions  
- Contrast with: library functions, which do not represent a direct entry point into the kernel
	- printf() library function invokes the write() system call 
	- malloc() library function invokes the sbrk() system call
	- many library functions do not involve system calls, examples:
		- strcpy() copy a string    
		- atoi() convert ASCII to integer     
- Manual pages:
	- "section 1" for general UNIX commands: man 1 cd  (or, equivalently: man cd)    
	- "section 2" for system calls: man 2 sbrk
	- "section 3" for library functions: man 3 printf
### Code Style
Overall goals:
- Correctness    
- Readability / Maintainability  
- Security   
- Performance   
Many different code style conventions (often specified at the team/company level) Good starting points:
- [CS50 Style Guide](https://cs50.readthedocs.io/style/c/)
- [SEI CERT C Coding Standard](https://wiki.sei.cmu.edu/confluence/display/c/Introduction) (Secure Code)
- 
