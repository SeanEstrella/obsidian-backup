Date Created: 09-27-2023
___
# CPE 357 09-25 Lecture
## Notes
### UNIX Processes
- **A process is an instance of a running program**
	- Contrast with: program, an executable file residing on disk in a directory
- **Whenever a command is issued in UNIX, it creates/starts a new process.**
	- System tracks: user ID, group ID, process ID, working directory
- Record of services/resources used:
	- Memory
	- CPU Time
	- I/O Streams
### **Signals**
- Signals are a technique to notify a process that some condition has occurred.
	- Example: divide by zero / SIGFPE (floating point exception)
- Three choices for dealing with signals:
	- Ignore the signal
	- Let the default action occur (for SIGFPE, terminate the process)
	- Provide a function that is called when the signal occurs ("catch" the signal)
### UNIX Paths
**A path is a reference to a file or directory:**
	**/usr/local/bin/**
	**/home/amigler/csc357/recipes.txt**

Absolute (starting with /) or relative to the current working directory.
~  (short for "home directory")**

###  PATH Environment Variable
- PATH is an environment variable specifying a set of directories where executable programs are located
- When you execute a command, the shell searches through each directory defined in PATH, one by one, until it finds a directory where the executable exists.
### Some Useful UNIX Commands
- man: view reference manuals for commands, library functions, or system calls
- wc: word, line, character, and byte count
- ps: Used to see what processes are running
- who: Used to see if other people are on this same machine
- top: Used to see active processes
- which: locate a program file in the user's path
- grep: text match based on regular expression
- head / tail: list start or end of a file
- tr and sed: two “editors” controlled by command-line options
### Unix Streams
- Input Stream (STDIN / file descriptor 0)
	- keyboard by default
	- in terminal control d indicates end of stream 
- Output Stream (STDOUT / file descriptor 1)
	- Terminal by default
- Error Stream (STDERR / file descriptor 2)
	- terminal by default
format: command < input.txt > output.txt 2>error.txt
### **Redirection of Standard Input/Output**
- Append output of the command into output.txt:
	- command >>output.txt
- Redirect stdout (to out.txt) and stderr (to error.txt):
	- command >output.txt 2>error.txt
- Redirect stderr and stdout to file output.txt:
	- command >output.txt 2>&1
### Composing Unix Tools
Pipe and chain commands by sending an output of one as the input to another
