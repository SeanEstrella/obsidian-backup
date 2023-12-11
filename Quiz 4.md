### Process-Control Functions (fork, exec, wait)

#### 1. What happens in a UNIX system when the `fork()` function is called, and how does the system differentiate between the parent and child process?
- When `fork()` is called in UNIX, it creates a new process (the child process) by duplicating the calling process (the parent process). The child process gets a copy of the parent's memory space, including variables and program counters.
- Differentiation: The parent process receives the child's PID (Process ID) as the return value from `fork()`, while the child process receives 0. This difference in return values is how each process knows its role.1. Can you explain the difference between `fork()` and `exec()` in process creation and management? How do they work together in a typical application?

a new process is created which copies the parents memory space. The parent process contains the pid of the child and child contains 0.

#### 2. Can you explain the difference between `fork()` and `exec()` in process creation and management? How do they work together in a typical application?

fork creates a new process in the format:
```c
pid = fork();
```
the two processes are copies of eachother with the only difference that one is tracked as the child and one is tracked as a parent , based on PIDs.

**NOTE**: If a PID is returned as -1 (or less than 0), then an error has occurred. 

exec has multiple formats
p -> filename argument using PATH
l -> list of args
v -> takes an argv[] vector and is mutually exclusive with l
- **Description**: `argv[]` is an array of character pointers (strings) that represent the command-line arguments passed to the program being executed. The name `argv` stands for "argument vector."
e -> envp[] array instead of using the current environment
- **Description**: `envp[]` is an array of character pointers that hold the environment variables for the program. Each string in this array has the format `KEY=VALUE`. The name `envp` stands for "environment pointer."

exec takes that newly created process and will change its memory space to a new program. PID is conserved

1. **`execl()`**:
    - Function Prototype: `int execl(const char *path, const char *arg, ... /*, (char *) NULL */);`
    - Used to execute a program specified by `path`.
    - Allows specifying arguments as a list of strings, ending with a NULL pointer.
    - Each argument is passed individually.
2. **`execv()`**:
    
    - Function Prototype: `int execv(const char *path, char *const argv[]);`
    - Similar to `execl()`, but takes an array of pointers to null-terminated strings that represent the argument list.
    - The array of pointers must be terminated by a NULL pointer.
3. **`execle()`**:
    
    - Function Prototype: `int execle(const char *path, const char *arg, ... /*, (char *) NULL, char *const envp[] */);`
    - Similar to `execl()`, but allows specifying the environment of the executed program explicitly via `envp[]`.
    - Arguments are specified as a list, and the environment is a null-terminated array of strings.
4. **`execve()`**:
    
    - Function Prototype: `int execve(const char *path, char *const argv[], char *const envp[]);`
    - Similar to `execv()`, but also allows specifying the environment.
    - Takes an array of arguments and an array of environment settings.
5. **`execlp()`**:
    
    - Function Prototype: `int execlp(const char *file, const char *arg, ... /*, (char *) NULL */);`
    - Similar to `execl()`, but instead of a full path, it uses the system's PATH environment variable to find the executable file.
    - Arguments are specified as a list.
6. **`execvp()`**:
    
    - Function Prototype: `int execvp(const char *file, char *const argv[]);`
    - Similar to `execv()`, but uses the PATH environment variable to find the executable.
    - Takes an array of arguments.

#### 3. Describe a scenario where the `wait()` function is crucial in process synchronization. What might happen if `wait()` is not used properly?


#### 4. How does a child process typically terminate, and what are the implications of its termination for the parent process?

### Interprocess Communication

5. Define interprocess communication and explain why it is necessary in operating systems.
6. What are the different methods of interprocess communication available in UNIX, and how do they differ in terms of functionality and use cases?
7. How does interprocess communication in a single computer system differ from communication between processes across a network?

### Pipes

8. What is a pipe in UNIX, and how does it facilitate communication between processes?
9. Describe the differences between named and unnamed pipes. In what scenarios would you prefer one over the other?
10. How would you use pipes in a program to redirect the output of one process to the input of another?

### UNIX Domain Sockets

11. Explain what UNIX domain sockets are and how they differ from network sockets.
12. In what scenarios are UNIX domain sockets more advantageous than other forms of interprocess communication?
13. How do UNIX domain sockets handle data transmission, and what are the different types of sockets available?