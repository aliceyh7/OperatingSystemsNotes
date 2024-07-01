# OperatingSystemsNotes

CPU can only understand 1s and 0s

# Intro to OS 

High Level Program --> Compilers --> Machine Code --> placed in Hard Disk --> RAM --> CPU takes program and runs it line by line
-once the program is finished, it will be completely removed from RAM (freed space)

RAM costs less & is faster than HD

OS is about Resource Allocation (of CPU) -- it is a piece of code with lots of functions
- of processes in Hard Disk, long-term scheduler decides next 
- of processes in RAM, short-term scheduler decides what gets CPU first

OS is always present inside the RAM
- RAM holds {OS Code | User space (application programs) } 

I/O Devices working with CPU:
- Can read/write to hard disk (e.g. editing word document)
- Other examples: Monitor, Keyboard, Hard Disk

After program has been moved from hard disk to ram: the things that can happen are:
1. Execution - executed by CPU line by line
2. I/O Event - executed by I/O
3. Waiting

Turn Around Time: waiting time + execution time + I/O Time

# Program vs Process
A program in execution is called a process
States of a process: 
1. new state -- process is newly created by program (e.g. GoogleChrome.exe)
2. ready state -- process is moved to RAM from HD and is waiting for CPU or I/O
3. running state == 
4. I/O state -- performing reading/writing from I/O event
5. terminated state -- remove process from RAM
6. Suspend ready state
7. Suspend wait state

# Degree of Multiprogramming: 
- the max number of processes that can be placed in RAM in our computer
 = Size of RAM / Size of Single Process

# Types of Operating Systems:
1. Batch OS: jobs are processed in batches without interaction with the user.
(i) degree of multiprogramming is always 1 (i.e., only one job is processed at a time)
(ii) execution and I/O operations cannot be performed simultaneously on the same process
Advantages: Simple to implement and manage, Suitable for large, repetitive jobs.
Disadvantages: Less efficient due to the idle CPU time during I/O operations, long turnaround time since jobs are processed sequentially.

2. Multiprogramming OS: multiple jobs to reside in memory simultaneously, sharing the CPU
- Only 1 CPU, CPU switches between jobs (more efficient)
Disadvantage: overhead, complex to manage (memory and scheduling)

3. Multiprocessing OS: (used today, quad core for example)
- multiple CPUs are present
- parallel processing 
may have too high system cost

Parallel Processing vs Concurrent Processing
Parallel Processing: Executing multiple tasks simultaneously using multiple processors or cores.
- Example: Running different parts of a large scientific computation at the same time on different cores of a multi-core processor.

Concurrent Processing: Managing multiple tasks at the same time by switching between them rapidly on a single processor.
- Example: computer running web browser, music player, and a document editor by quickly switching between each task, giving the appearance that all are running at the same time.


# CPU Efficiency: 
Useful time of CPU / Total time of CPU

# Process Control Block, Attribute of a Process:
When user opens a program, a process is created
PCB has: process ID, program counter, process state, general purpose registers, priroity, list of open files, list of open devices and protection (8 things)

Process contains: Stack, heap, static/global variables, program

Stack -> | <- Heap | Static/Global Vars | Program

Stack: temporary data managed by CPU, grows and shrinks as functions are called and return, LIFO
Heap: Dynamic Memory Allocation (malloc, calloc), managed by programmer (C, C++) or language runtime (Java, Python) grows upward, requires explicit freeing or garbage collection

Data Segment: Stores global and static variables

CPU Scheduling: done by scheduler, which is part of our OS code

Program Counter: the instruction number/line of the program to continue from where we left off

Preemption: forcefully stopping the execution of a process by CPU

TImestamp: the max amount of time a process can be executed without preemption