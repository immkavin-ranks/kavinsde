## Process

- A **process** is a dynamic entity representing **Program in execution.**
### Differences Between Program and Process

|**Aspect**|**Program**|**Process**|
|---|---|---|
|**Definition**|Static set of instructions|Dynamic execution of instructions|
|**State**|Passive (on disk)|Active (in memory, undergoing execution)|
|**Existence**|Exists in storage (disk)|Exists in memory (RAM)|
|**Lifetime**|Permanent until deleted|Temporary, lasts until execution completes|
|**Multiplicity**|Single copy can be executed many times|Each execution is a unique process|
|**Resources**|Requires no resources when stored|Requires CPU, memory, I/O when executing|
|**Concurrency**|Cannot be concurrent|Can be concurrent (multitasking)|
|**Example**|Word Processor Application (`word.exe`)|Running instance of `word.exe`|

## Race Condition

>A race condition exists when the result of a computation varies, depending on the timing of other processes.

>A **race condition** occurs when the scheduling of two processes is so critical that the various orders of scheduling them result in different computations. Race conditions result from the explicit or implicit sharing of data or resources among two or more processes.
## Schedulers

>The **job scheduler** chooses a small subset of the jobs submitted and lets them “into” the system. That is, the job scheduler creates processes for these jobs and assigns the processes some resources.

>The **process scheduler** decides which of the processes within this subset will be assigned a processor, at what time, and for how long.
## Deadlock

>A situation where there are two processes, each of which is waiting for resources that the other has and will not give up. In this situation, no processor can be assigned to either process. *Deadlocks involve conflicting needs for resources by two or more processes.*

>**Deadlock** can be defined as the **permanent blocking of a set of processes that either compete for system resources or communicate with each other**. 
>
>A set of processes is deadlocked when each process in the set is blocked awaiting an event (typically the freeing up of some requested resource) that can only be triggered by another blocked process in the set. 
>
>Deadlock is permanent because none of the events is ever triggered. Unlike other problems in concurrent process management, there is no efficient solution in the general case.
## Kernel

>Kernel (Here I mean **monolithic** kernel, not micro-kernel or exokernel) is a set of core functionality of a modern operating system. (e.g. Memory Management, Inter-process Communication, Task Management, I/O stack, Network, device driver...). 

>Kernel runs in a **privileged** level and interact with hardware directly while user cannot access; The only way a user-level program could interact with a kernel is via **system call.** Operating system is a larger concept, it includes kernel, run-time libraries, system managers and shell...

>Kernel is a process which is always running on your machine. Kernel includes various background threads which takes care of scheduling threads, handling IO etc. OS is just a program in which various kernel modules along with other modules which are part of OS are included.

## System call & Interrupt

>User programs can’t be trusted if they wish to invoke some functionality in kernel. So whenever they wish to access the OS functionality in kernel they make the use of System Calls. System Calls let the User access the kernel in controlled manner.

>However an interrupt is a request from some external device for a response from the processor. There can be **software interrupts** (generated via a program) or **hardware interrupts** but the way interrupts are handled remains same.
>System call is a call to a subroutine built in to the system, while Interrupt is an event, which causes the processor to temporarily hold the current execution. However one major difference is that system calls are synchronous, whereas interrupts are not. 
>
>That means system calls occur at a fixed time (usually determined by the programmer), but interrupts can occur at any time due an unexpected event such as a key press on the keyboard by the user. 
>
>Therefore, when ever a system call occurs the processor only has to remember where to return to, but in the event of an interrupt, the processor has to remember both the place to return to and the state of the system. Unlike a system call, an interrupt usually does not have anything to do with the current program.

![](attachments/Pasted%20image%2020241015085846.png)


## Convoy Effect

- The convoy effect pertains to the sequential arrangement of processes in a system's scheduling queue, where slower processes hinder the progress of faster ones. It's like slower vehicles blocking faster ones on a road.
- For instance, in a computing system using first-come-first-served (FCFS) scheduling, longer processes occupying resources may delay the execution of shorter, quicker processes, causing a traffic jam-like effect.

## Starvation

- Starvation, on the other hand, results from the CPU's bias towards certain processes, where high-priority tasks continuously receive attention, leaving lower-priority tasks waiting indefinitely. It's akin to people cutting in line for food, leaving others hungry.
- In a priority-based scheduling system, low-priority tasks might be starved of resources as the CPU consistently prioritizes high-priority tasks, leading to unfair resource allocation.

>In simpler language **Convoy Effect** is slower processes hold up faster ones due to their order in the queue, whereas **Starvation** is CPU's favoritism towards high-priority tasks leaves low-priority ones waiting indefinitely

## Spooling

>Spooling is a process in which data is temporarily gathered to be used and executed by a device, program or the system. 
>
>It is associated with printing. When different applications send output to the printer at the same time, spooling keeps these all jobs into a disk file and queues them accordingly to the printer.

![](attachments/Pasted%20image%2020241015084530.png)

## File Directory Database

![](attachments/Pasted%20image%2020241015085244.png)

## State Transistions

![](attachments/Pasted%20image%2020241015090639.png)
