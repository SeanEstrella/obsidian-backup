# CPE 357 - 09 - Memory Allocation

Class: [[CPE 357]]
Date: 11-06-2023
Teacher:
___
## Notes
### Virtual Memory Layout
- Virtual memory is often discussed in terms of [[Low Memory]] versus [[High Memory]]
- High memory is typically reserved for the kernal
- By default, the Linux kernel uses a 3:1 proportion. For example, 32-bit address space (4GB):
	- User space: 0x00000000 - 0xbfffffff  (3GB)
	- Kernel space: 0xc0000000 - 0xffffffff  (1GB)
### Memory Layout of a C Program
- Text segment
	- Machine instructions
- Initialized data segment
	- Variables that are initialized in the program (e.g. int months = 12;)
- Uninitialized data segment (bss) 
	- For example: long sum[1000]; outside of any function
- Stack
	- Automatic variables, return address
- Heap
	- Dynamically allocated memory ie. malloc()
- The size(1) command reports the sizes (in bytes) of the text, data, and bss segments of an executable.
![[Pasted image 20231106152539.png]]
### Function Call Stack
- The [[Function Call Stack]] is responsible for maintaining the local variables and parameters during function execution
- Plays a central role in the execution of C programs
- The stack is a dynamic entity
- 