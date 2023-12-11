# CPE 357 10-16 Lecture

Class: [[CPE 357]]
Date: 10-16-2023
Teacher:
___
## Notes
Programming assignment 2 notes:
- don't corrupt file
- don't segfault
### UNIX File System
- The UNIX file system is a hierarchical arrangement of directories and files.
- Everything starts in the root directory.
	- root directory name is the character /
**![](https://lh3.googleusercontent.com/YzF5ScES5tcFmxji0kDQ8OOSqfmx3-fhBnkSYlEJM09azzeXhH0O0QnevcEVit63CrvWRcKmdjlD56w_aTQiwW436pfNJh4rqaekn1df2294CHs2jZMOfaZR6zBbcZZvQ7rO23ZYhVkSlb29MgC7OpZ_oA=s2048)**
### Stat Function
```c
#include <sys/stat.h>

// struct stat contains information about a named file
int stat(const char *restrict pathname, struct stat *restrict buf);

// information about an already opened file (fd)
int fstat(int fd, struct stat *buf);

// information about a symbolic link
int lstat(const char *restrict pathname, struct stat *restrict buf);
```
### struct stat
**![](https://lh4.googleusercontent.com/AjRJAItSZ7AkLArW9lSHfiv53aFkrFY_ClYWuFmpI8vfu2jjnCx6F5uAjUS4GU3INA53nK-UMLPNBKzD8gB-Jsu0uNWpFvV0tRYhpXgFGlPF2k_mIRPUaYLDXsLXAQu775MYgnkYe0Hx1A59_jMn6B-Mig=s2048)**
in unix everything is considered a file, abstracted to a file

### File Types (st_mode in struct stat)
- Regular File - contains some form of dats, interpretation of the contents of a regular file is left to the user/application
	- file type macros defines in <sys/stat.h>
	- S_ISREG(fstat.st_mode) // assuming: struct stat fstat;
- Directory File - file that contains the names of other files and pointers to information on these files
	- S_ISDIR(fstat.st_mode)
- Block Special File - Provides buffered I/O access in fixed-size units to devices such as disk drives.
	- S_ISBLK(fstat.st_mode)
- Character Special File - Provides unbuffered I/O access in variable-sized units to devices
	- S_ISCHR(fstat.st_mode)
- FIFO - Used for communication between processes (also known as: named pipe)
	- S_ISFIFO(fstat.st_mode)
- Socket - Used for network communication
- Symbolic Link - A type of file that points to another file
### File Access Permissions
- st_mode value encodes access permission bits for the file
- All the file types - directories, character special files, etc - have permissions
- Nine Permission Bits:
	- User (Read, Write, Execute)
	- Group (Read, Write, Execute)
	- Other (Read, Write, Execute)
### Permissions Bitmask
![[Pasted image 20231016163012.png]]
