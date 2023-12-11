# CPE 357 10-04 Lecture

Class: [[]]
Date: 10-04-2023
Teacher:
___
## Notes

### Arrays in C
- type name[size] allocates size * sizeof(type) bytes of con
### Array Initialization
- type name\[size] = { val0, val1, ..., valN}
	- initialization via {} can be used only at time of definition
	- if no size supplied, array size is inferred from length of array initializer
### Memory Organization
- Simplified model: array of consecutively numbered or addressed memory cells that may be manipulated individually or in contiguous groups
	- single byte: char
	- two contiguous bytes: short
	- four contiguous bytes: int
- A pointer is a group of cells that can hold a memory address
### Pointers in C
Syntax:
```c
int *p; // variabe p can contain the address of an int
```
Caution:
```c
int *p1, p2; // a pointer to an integer, an integer;
// is not the same as 
int *p1, *p2; // pointer to an int, pointer to an int;
```

### Pointer Operators
- The unary operator & gives the address of an object
	- &var represents the address of a variable named var
	- Example:
```c
char *fgets(char *s, int size, FILE *stream)
int i = 357;
int *p = &i; 
```
P points to the address of 357
[(the address)] --> [357]
- If ip points to the integer x, then \*ip can occur in any context where x could:
```c
*ip = *ip + 10; // increments *ip (x) by 10
```
	