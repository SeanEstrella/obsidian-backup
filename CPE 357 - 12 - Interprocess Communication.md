Class: [[CPE 357]]
Date: 11-13-2023
Teacher:
___
## Notes
### File Sharing
UNIX supports the sharing of open files among different processes.
Three data structures are used to represent an open file:
1) Every process has an entry in the process table
2) Within each process table entry is a table of open file descriptors for that process
3) Each open file (or device) has a v-node structure:
    1) Tye of file
    2) pointers to functions that operate on files
    3) Typically

