## Arrays in C
## Array Initialization

## Memory Organization
- pointer is a group of cells that holds a memory address
- unary operator & gives address of an object
- unary operator * is the indirection or dereferencing operator
	- this is the operator for making a pointer
```c
var = 10
int *varAddress = &var
```
## Pointer Arithmetic
- Pointers are declared with a type
- Pointer arithmetic is scaled by sizeof(* p)
- closely aligned with arrays
## Pointers and Arrays
```c
int a[10];
int *pa;
pa = &a[0];   // equivalent to: pa = a;
``` 
## Character Pointers (Strings)
- a string is an array of characters terminated by '\\0'
## char * versus char[]
```c
char *s = "abc";
char t[] = "abc";
```
- char * results in an unmodifiable string constant in a memory area that should be considered read only
	- trying it change s with indexing is invalid
- char\[t] allocates a modifiable array of characters
- t is an array name -- not a pointer variable in the sense that s is
## Copying a string
- to copy a string you must loop through string and replace character one by one
- or use strcpy(the one being replaced, the one to copy)
## Pointers to Pointers
## Two-dimensional arrays
Basically a one dimensional array that holds the addresses of other arrays as its elements

