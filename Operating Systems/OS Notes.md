**How Computers Work**
- Input is data we give to our computers
- Processing is comprised of the translation of input and the instructions given for output
- Memory is used to store either temporary or permanent information
- Output is the information that gets returned by the computer

**Introduction to Operating Systems**

>An **Operating System,** or OS, is system software that’s responsible for handling the basic functionalities. At the core of an operating system is the **_kernel_** which manages all the interactions between the hardware and software components of a computer.

**Functions of an OS**

Some of the vital functions of an OS:

- Process Management 
- Memory Management
- File System Management
- IO Management
- Multitasking
- Networking
- Security
- Providing a user interface

**Process**: When we run a program, the instance of that execution is represented by a process.

**CPU**: The CPU controls all the different components between hardware and software by processing all of the information that flows throughout the computer.

CPUs generally consist of three main components: a control unit (CU), an arithmetic and logic unit (ALU), and a collection of registers.

The control unit (**CU**) is the overseer of the CPU, responsible for controlling and monitoring the input and output of data from the computer’s hardware. Its primary job is making sure that data is sent to the right component at the right time, and arrives with integrity.

The arithmetic and logic unit (**ALU**) is where all of the processing of the computer takes place. It is the fundamental part of the CPU that actually does the arithmetic calculations of the data as well as the handling of logical comparisons and conditionals.

The **register**, or immediate access store, is a limited space, high-speed memory mounted on the CPU for quick processing. It provides the CPU with a place to store values that are crucial for the calculations the ALU is currently processing.

**Kernel**: The kernel manages all of the interactions between the hardware and software components of a computer, such as interfacing with memory and hard drives.

**Process wait time** is ==the amount of time a process spends waiting (*Ready*) to be executed by the CPU. It's calculated by subtracting the burst time from the turnaround time.

First come First serve
https://static-assets.codecademy.com/Courses/Operating-Systems/GIFs/First-Come-First-Served.gif

**convey effect** - long process occupy the CPU (Ex. FCFS)
**starvation** - low priority process never executed (Ex. SJF)


**Priority scheduling** 
**SJF** - Shortest Job First 
- variation of priority scheduling
- incoming shortest processes make longest processes starve for CPU
- solved by aging the jobs
- aging - the priority of a process increases the longer it has been waiting
- queue should be sorted for every interruption

**Round robin**
- Context switching required at every time slice

**Multiple-levels queue scheduling**
https://static-assets.codecademy.com/Courses/Operating-Systems/Multiple-level-queues-scheduling-algorithm-GIF.gif


Synchronization:  program is synchronized when each critical section satisfies the mutual exclusion, progress, and bounded waiting conditions.

locking: there must only be one thread at a time with access to a critical section.

mutual exclusion lock or mutex
lock and unlock

> once a thread call mutex lock() other threads wait infinitely until the locked thread to call mutex unlock()

condition variable: 
- consumer - producer problem
- wait and notify based on condition

atomic variables:  The variable is atomic because the operations required to modify it take place, from our threads’ perspective, in exactly one atomic step.

**synchronization conditions for a critical section:**
- mutual exclusion: no more than one thread may access critical section at a given time.
- progress: if no thread is currently inside the critical section, a thread attempting to access it must be allowed to do so.
- bounded waiting: each thread that wishes to gain access to a critical section must, at some point, gain access.

lifecycle of a process -> new, ready, active, blocked, terminated

memory: size and speed

paging: spreading processes' memory across non-contiguous locations.

file control block: metadata, file permissions, times, access
file permissions: read, write, execute

layers of file system: application programs, logical file system, file organization module, basic file system, IO control, devices