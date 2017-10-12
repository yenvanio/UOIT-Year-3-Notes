# Systems Programming


## Week 1


#### Linux
- 3 Main Components
  - Kernel
    - Core part of Linux
    - Responsible for all major activities of the OS
    - Has various modules and interacts directly with hardware
    - Kernel provides required abstraction to hide low level hardware details to system or application programs
  - System Library
    - Special functions/programs that can access Kernel's features
    - These libraries implement most of the functionality for the OS and do not need kernel module code access
  - System Utility
    - Programs responsible to do specialized individual level tasks

#### Basic Features of Linux
- Portable
  - Can work on different types of hardware in the same way. Linux Kernel and application programs support installation on any hardware or platform
- Open Source
  - Linux source code is freely available and it is a community based development project
- Multi-User
  - Multiple users can access system resources like mem/ram/programs at the same time
- Multiprogramming
  - Multiple applications can run at the same time
- Hierarchical File System
  - Standard file structure
- Shell
  - Special interpreter program which can be used to execute commands of the OS.
- Security
  - User security using password protection / controlled access to files and data encryption

#### Linux System Architecture (innermost -> outermost)
- Hardware Layer
  - All peripheral devices (RAM/HDD/CPU..etc)
- Kernel
  - Core component of OS, interacts with hardware and provides low-level services to upper layer components
- Shell
  - Interface to kernel, hiding the complexity from users
- Utilities
  - Gives user most of the functionalities of an OS


## Week 2


####


#### Quiz 1

```
1.) Which of the following statements is false?
a.) Linux and Unix are available for many different platforms
b.) Components of a computer system usually can't function together without an OS
c.) MULTICS is an OS
d.) Dennis Ritchie wanted to build a system for a game called "Space Wars"  

2.) Which of the following is not a part of free software foundation standard?
a) Run the program for any purpose you want to, rather than be restricted in what you can use it for.
b) Improve the program and release those improvements so that others can use them.
c) Share the program with restricted access.
d) Study the program's source code and modify it if you need to

3.) Operating system kernel
a) provides the required abstraction to hide low level hardware details to system or application programs.  
b) consists of libraries that implement most of the functionalities of the operating system
c) consists of programs that are responsible to perform specialized, individual level tasks.
d) is an application program

4. Which of the following is not related to multitasking?
a) Jobs can be run in background, and owned by different users – on the same processor
b) Capable of supporting and utilizing more than one computer processor.
c) Allow different parts of a software program to run concurrently.
d) Manages memory

5. What does .. mean?
a) current directory b) parent directory

6. Which field of the following denotes the size of the file created?
a) 1 byte b) 1KB c) 106 bytes d) 106KB

7. To rename a file, which shell commands can be used:
a) rename b) move c) cp d) mv

8. Which of the following represents the words in using the wc utility?
a) 9 b) 43 c) 213

9. Which of the following option for chmod will not remove executable permission from user?
a) a – x b) u – x c) 777

10. Which utility can be used to change the ownership of a file?
a) chmod b) chgrp c) chown 

```
