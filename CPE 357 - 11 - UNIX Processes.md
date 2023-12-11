# CPE 357 - 11 - UNIX Processes

Class: [[]]
Date: 12-04-2023
Teacher:
___
## Notes

### Process Control
The UNIX system handles **process control**, including:
- Creation of new processes
- Program execution
- Process Termination
### Process Identifiers
- Every process has a unique **process ID** (PID)
    - Unique, non-negative integer
    - May be reused; terminated process IDs are candidates for reuse
- Special processes (implementation specific)
    - Process ID 0 is usually the scheduler process
    - Process ID is usually the `init` process, responsible for initializing a system after boot
    - Process ID 2 is the pagedaemon; responsible for supporting the paging of the virtual memory system
- ps command
### Library Functions
```c
#include <unistd.h>
pid_t getpid(void);     // Returns: process ID of calling process

pid_t getppid(void);    // Returns: parent process ID of calling process

```
### Process Group ID
- Every process is a member of a unique process group, identified by its **process group ID.**
- When the process is created, it becomes a member of the process group of its parent.
```c
int setpgid(pid_t pid, pid_t pgid); 
// Sets the process group id of the process specified by pid to pgid

pid_t getpgid(pid_t pid);

```
### fork Function
An existing process can create a new process by calling the for function.
```c
#include <unistd.h>
pid_t fork(void);

// Returns: 0 in child, process ID of child in parent, -1 error
```
- New process created by fork() is referred to as the *child* prcoess.
- Child and the parent processes continue executing with the instruction
- that follows the call to fork
    - Return value from fork() is 0 in child process
    - In the parent, fork() returns the child's process ID
- Child process gets a *copy* of the parent's data space, heap, and stack
### Example: fork.c
week6/fork.c in git
```c
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>

int globvar = 6; /* external variable in initialized data */
char buf[] = "unbuffered write() to stdout\n";

int main(void) {
    int var; /* automatic variable on the stack */
    pid_t pid;
    var = 88;

    if (write(STDOUT_FILENO, buf, sizeof(buf)-1) != sizeof(buf)-1) {
        printf("write error\n");
    }
    
    printf("before fork");
    fflush(stdout);
    
    pid = fork();
    if (pid < 0) {
        printf("fork error\n");
    } else if (pid == 0) { /* child */
        printf("(child) pid = %d\n", pid);
        globvar++; /* modify variables */
        var++;
    } else { /* parent */
        printf("(parent) pid = %d\n", pid);
        sleep(2);
    }
    printf("pid = %ld, glob = %d (%p), var = %d (%p)\n",
            (long) getpid(), globvar, &globvar, var, &var);
    
    exit(0);
}
```

- Note difference when running to terminal vs. redirect:
```console
❯ ./a.out                                 
unbuffered write() to stdout
before fork(parent) pid = 9729
(child) pid = 0
pid = 9729, glob = 7 (0x100b74000), var = 89 (0x16f2929f8)
pid = 9728, glob = 6 (0x100b74000), var = 88 (0x16f2929f8)
```

```console
❯ ./a.out > output.txt
❯ cat output.txt      
unbuffered write() to stdout
before fork(child) pid = 0
pid = 9720, glob = 7 (0x100980000), var = 89 (0x16f4869f8)
(parent) pid = 9720
pid = 9719, glob = 6 (0x100980000), var = 88 (0x16f4869f8)
```
- 
### File Sharing
- 
### Uses for fork()
1) 
### Normal Process Termination

### Abnormal Process Termination

### wait / waitpid system calls
```c
#include <sys/wait.h>

pid_t wait(int *status);
pid_t waitpid(pid_t pid, int *status, int options);
```
- Wait for state changes in a child of the calling process, and obtain information about the child whose state has changed
#### week6/wait_status.c in git
```c
// Need to add
```

### exec Functions
- The fork function can be used to create a new process (the child) that then causes another program to be executed by calling one of the exec functions.
- When a process calls one of the exec functions, the program is completely *replaced* by the new program
    - Process ID does not change
![](https://lh7-us.googleusercontent.com/GcILTJjbBnc9VDrPCGXG82oxMjFBTt1X8PHaTdqzQ4_abNPuBDsrFVUozfWBnaEVvSjq9mEl9OYblx2A94nIs3QSkZ9mscfKYLutbB3_9bv0rVJsseVYp3L7W_uu12eGIX8zBewo5KM-ib5fbF-dbKia5A=s2048)
Decoding function names:
- p - the function takes a file name argument and uses the PATH environment variable to find the executable file
- l - the function takes a list of arguments
- v - takes an argv[] vector (mutually exclusive with l)
- e - the function takes an envp[] array instead of using the current environment
