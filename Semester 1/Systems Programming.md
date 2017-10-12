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


#### Quiz 1 (Week 1 + Week 2)

1.) Which of the following statements is false?
  - Linux and Unix are available for many different platforms
  - Components of a computer system usually can't function together without an OS
  - MULTICS is an OS
  - **Dennis Ritchie wanted to build a system for a game called "Space Wars"**  

<br>
2.) Which of the following is not a part of free software foundation standard?
  - Run the program for any purpose you want to, rather than be restricted in what you can use it for.
  - Improve the program and release those improvements so that others can use them.
  - **Share the program with restricted access.**
  - Study the program's source code and modify it if you need to

3.) Operating system kernel
  - **provides the required abstraction to hide low level hardware details to system or application programs.**  
  - consists of libraries that implement most of the functionalities of the operating system
  - consists of programs that are responsible to perform specialized, individual level tasks.
  - is an application program

4.) Which of the following is not related to multitasking?
  - Jobs can be run in background, and owned by different users – on the same processor
  - Capable of supporting and utilizing more than one computer processor.
  - Allow different parts of a software program to run concurrently.
  - **Manages memory**

5.) What does .. mean?
  - current directory
  - **parent directory**

6.) Which field of the following denotes the size of the file created?
<br>
`-rw-r--r--   1   glass   106   Jan 30 19:46    heart`
- 1 byte
- 1KB
- **106 bytes**
- 106KB

7.) To rename a file, which shell commands can be used:
  - rename
  - move
  - cp
  - **mv**

8.) Which of the following represents the words in using the wc utility?
<br>
`wc heart.final   ...obtain a word count.`
<br>
`9    43    213 heart.final`
- 9
- **43**
- 213

9.) Which of the following option for chmod will not remove executable permission from user?
  - a – x
  - u – x
  - **777**

10.) Which utility can be used to change the ownership of a file?
  - chmod
  - chgrp
  - **chown**
