#
- After this unit, you will be able to:
    - Understand the general structure of an operating system
    - Understand the role of processes and how they are managed
    - Understand multithreading and how it can improve performance
    - Understand memory and device management
    - Understand the basics of file structures
    
- As computers evolved from __Vaccum Tubes__ to __Transistors__ to __Integrated Circuits__ to __VLSI__
    - When it comes to circuits and electronic devices, energy is typically stored in one of two places
        - The first, a battery, stores energy in __chemicals__
        - Capacitors are a less common (and probably less familiar) alternative
            - They store energy in an __electric field__
    - the OS has also undergone significant changes to keep up with the computers
## What are the types of OS?
    - Batch OS- This OS does not directly work with the computer
        - An operator (human) takes similar jobs having the same requirement and group them into batches
        - The batches are then given to the CPU for execution
        - The efficiency of the operating system depends on the operator to group the jobs
    - Time-sharing OS - Here the tasks are given a time slice/quantum to execute
        - This allows many users to share the computer resources in a fair manner and CPU utilization is increased
        - Tasks can be from a single user/ multiple users
        - eg. UNIX
    - Distributed OS- Effectively, manages a group of different computers (each with own memory and CPU) and make them appear to be a single computer
        - This allows shared access to files, printers and applications
    - Network OS- The individual computers have a common server and computers running in the different operating systems can participate in a common network
        - Remote access is possible like in case of distributed systems
        - Presence of server enhances the security of the whole network
        - They are tightly coupled
    - Real-time OS — As the name suggests, they are meant for real-time devices
        - where time requirements are very strict like air traffic control, missile control and even in autonomous cars
        - Here delays could lead to failures
## What does OS do?
- [linux series](https://www.youtube.com/watch?v=Z-C11_xK_ZI)
- [OS series](https://www.youtube.com/watch?v=5AjReRMoG3Y)
- [os is an interface between user and hardware](https://www.tutorialspoint.com/operating_system/os_overview.htm)
- [all you need to know about os](https://hackernoon.com/heres-what-you-need-to-know-about-operating-systems-a40603e74b8d) *
    - Memory management is a function of the OS to load the programs into the main memory
        - scans all request for memory space and check if it's valid, allow allocation of memory spaces
        - The __memory usage__ of an application __cannot be altered__, __only allocated__ if there’s enough space 
    - Processor Management — Monitors processor (CPU) and process states and allocates the CPU to process in a scheduled way
        - Keeps track of the status of each process, handle jobs as they enter the system and manage each process
        - __scheduler__ - __time slicing__
        - processes are typically independent, while threads are subsets of a process
        - processes have separate address spaces, whereas threads share their address space
    - Device Management — Communicates with devices via device drivers, Keeps track of them using I/O Controller, allocates them to processes.
    - Network management: provides way for users to share hrdw n sftw resources, also controlling the user access
    - File management: file permissions
    - Security — Provides authentication and prevents unauthorized access
- A program loaded into the memory becomes a process, the memory layout consists of ─ stack, heap, text, and data.
## I/O and file management
- device management : https://computer.howstuffworks.com/operating-system8.htm
- i/o polling, interupting : https://www.tutorialspoint.com/operating_system/os_io_hardware.htm

## subsystems, components
- a system is a set of hardware and software components that have been chosen to work together for a particular purpose
- Without a greater system, the subsystem could not exist
- It is a set of collaborating components that interact with the greater system to perform a task
- Your keyboard as a whole is a subsystem
- A system or subsystem is an independent, performing entity
    - __hardware subsystem__ : cpu, memory, i/o
    - Components, however, cannot perform specific tasks on their own
    - A __module__ is a self-contained __component__ of hardware or software that interacts with the larger system
- When you break the keyboard into parts it is made up of components
- For example, if the Shift key was ripped off of your keyboard, it could not perform its own specific task
    - It is a component that must work collaboratively with other parts
    - If you understand the difference between components and the subsystem definition, you have mastered these important basics!

## File
- A file is a named collection of related information that is recorded on secondary storage such as magnetic disks, magnetic tapes and optical disks
- In general, a file is a sequence of bits, bytes, lines or records whose meaning is defined by the files creator and user
### File Structure
- A File Structure should be according to a required format that the operating system can understand
    - A file has a certain defined structure according to its type
    - A __text file__ is a sequence of characters organized into lines
    - A __source file__ is a sequence of procedures and functions
    - An __object file__ is a sequence of bytes organized into blocks that are understandable by the machine
    - When operating system defines different file structures, it also contains the code to support these file structure
        - Unix, MS-DOS support minimum number of file structure

### File Type
- File type refers to the ability of the operating system to distinguish different types of file such as __text files__ __source files__ and __binary files__ etc
- Many operating systems support many types of files

- Operating system like MS-DOS and UNIX have the following types of files −
    1. __Ordinary files__
        - These are the files that contain user information
        - These may have text, databases or executable program
        - The user can apply various operations on such files like add, modify, delete or even remove the entire file
    2. __Directory files__
        - hese files contain list of file names and other information related to these files

    3. __Special files__
        - These files are also known as device files
        - These files represent physical device like disks, terminals, printers, networks, tape drive etc
        - These files are of __two types__ −
            - Character __special files__ − data is handled character by character as in case of terminals or printers
            - Block __special files__ − data is handled in blocks as in the case of disks and tapes

### File Access Mechanisms
- File access mechanism refers to the manner in which the records of a file may be accessed
- There are several ways to access files −
    - Sequential access
    - Direct/Random access
    - Indexed sequential access

- Sequential access
    - A sequential access is that in which the records are accessed in some sequence
        - i.e., the information in the file is processed in order, one record after the other
    - This access method is the most primitive one
    - Example: Compilers usually access files in this fashion
- Direct/Random access
    - Random access file organization provides, accessing the records directly
    - Each record has its own address on the file with by the help of which it can be directly accessed for reading or writing
    - The records need not be in any sequence within the file and they need not be in adjacent locations on the storage medium

- Indexed sequential access
    - This mechanism is built up on base of sequential access
    - An index is created for each file which contains pointers to various blocks
    - Index is searched sequentially and its pointer is used to access the file directly

### Space Allocation
- Files are allocated disk spaces by operating system
- Operating systems deploy following three main ways to allocate disk space to files
    - Contiguous Allocation
    - Linked Allocation
    - Indexed Allocation

- Contiguous Allocation
    - Each file occupies a contiguous address space on disk
    - Assigned disk address is in linear order
    - Easy to implement
    - External fragmentation is a major issue with this type of allocation technique

- Linked Allocation
    - Each file carries a list of links to disk blocks
    - Directory contains link / pointer to first block of a file
    - No external fragmentation
    - Effectively used in sequential access file
    - Inefficient in case of direct access file

- Indexed Allocation
    - Provides solutions to problems of contiguous and linked allocation.
    - A index block is created having all pointers to files.
    - Each file has its own index block which stores the addresses of disk space occupied by the file.
    - Directory contains the addresses of index blocks of files.
