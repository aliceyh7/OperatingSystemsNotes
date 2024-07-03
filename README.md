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

# Types of Scheduler, Context Switching
Long-term Scheduler: determines what processes & how many to move from HD to RAM
Short-term Scheduler: determines what processes to move from RAM to CPU

High priority processes should be executed first

Whenever a process needs to be moved from HD to RAM and RAM is full, which process should be moved to HD to allocate more space is decided by Medium Scheduler

# Various Times of a Process
Terms: Arrival Time, Burst Time, Completion Time， waiting time, response time, i/o time
Turn Around Time: completion time - arrival time
Turn Around Time: burst time + i/o time + waiting time
I/O time: the amount of time on I/O after it has arrived into the RAM


# Types of Scheduling Algorithms
CPU Scheduling Algorithms: preemptive, non-preemptive
Non-preemptive: never preempt a process if it has already started
Preemptive: if a higher priority process appears, leave the current process and schedule higher priority

CPU Scheduling Algorithms can be applied only to processes which are in the "ready state" (not running or I/O)
- processes in I/O are blocked so that they will not be considered by scheduling algorithms while scheduling

SJF Scheduling Algorithm: among the arrived processes, process with the least burst time (execution time) will be given preference
-Non-preemptive scheduling algorithm
-Priority-based algorithm
-Throughput: number of processes/schedule length

SRTF: Shortest remaining time first scheduling algorithm (preemptive version of SJF)

Response time: the initial waiting time before getting the CPU for the first time
-non-preemptive: response time = waiting time
-preemptive: 

FCFS: the process which has the least arrival time will be scheduled first
- non-preemptive scheduling algorithm
- not a priority-based scheduling algorithm

FCFS with context-switching overhead
-context-switching: x time unit

# Starvation
Starvation problem: iff there is a chance for a process in the ready state to wait indefinitely to get the CPU

Any priority based scheduling algorithm will definitely suffer from the problem of starvation

Any FIFO structure for RAM is starvation free

# Convoy Effect
A smaller process (process with very small execution time) waiting for one big process to get off (release) the CPU

An algorithm with convoy effect problem can lead to higher waiting time and higher TAT in comparison to an algorithm without convoy effect problem

FCFS has high convoy effect: short processes have to wait for long processes at the front of the queue 


# Practical Implementation
SJF, SRTF: better throughput (produce processing much faster than FCFS)
FCFS: easier to implement (just add clock)

# Throughput:
number of processes executed per unit time
Equation: = (# of processes executed) / schedule length

SRTF has highest throughput -- CPU never idle

