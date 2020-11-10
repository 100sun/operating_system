# 3.1 Introduction to Process

## program vs process

| program         | process            |
|-----------------|--------------------|
| static state    | dynamic state      |
| on HDD | on [memory](###memory) for execution |
| before creating | before terminating |
| process - PCB | program + PCB |

1. A **program** on HDD got a **PCB** from OS space of memory  => A **process** on user space of memory
2. The **process** returned the **PCB** => program

## Architecture 

### elements of memory 

1. user space
    - process A, process B 
        - code: program code (RDONLY)
        - data: global variables (RDWR)
        - stack: local variables, pointer of program address  
2. operating system space
    - [PCB](##PCB) A, PCB B....

# 3.2 Operation of Process

## process hierarchy

0. 'init process' when booting by OS
1. **fork() system call**: starts child process which is a copy of the parent process
    - copy all but not PID, Parent PID, Children PID
    - pid = fork() -> pid = 0: child(o), -1: error
2. program loads to the child process
3. **exec() system call**: replaces the current process image with new one
4. if child exit(PID) -> parent collects its data
    - data collection fail => **Zombie Process**
    - no parent process => **Orphan Process**

# 3.3 [States of a Process](https://github.com/100sun/operating_system/blob/master/os_w4_cpu_scheduling.md#queuing-diagram)

1. new + PCB => **ready**: waiting in the ready queue <-> running: one process executed by CPU => -PCB => terminated
2. **running**: during time slice
* active (CPU)
    - after time slice -> timeout(PID) => ready
    - IO -> **blocked**(PID): connecting PCB by pointers -> wakeup(PID)  => ready
* inactive (swap area)
    - expelled, delayed -> swap io ->**suspended ready** -> wakeup -> **suspended blocked** -> swap io => ready
3. terminated: code & data eliminated from memory and -PCB  
    - normal - exit() / abnormal - core dump

# 3.4 Process Control Block & Context switching

## PCB

* OS relevant: PID, pointer, process state
* CPU relevant: Program Counter, registers
* resource relevant:  memory limits, list of open files

## Context switching

### why

time-sharing system

### when

io/timer interrupt -> ISR or context switching

### process context

: HW / memory / kernel context 

### how to switch

p2 ready, p1 running -> timeout -> store p1 state in PCB 1 -> get p2 state from PCB2 -> dispatch p2 -> p2 running, p1 ready 

## disadvs 

overhead => [multi-thread](##Multi-Thread) to overhead ↓

# 3.5 Thread

## What is Thread

* Lightweight Process: unit of CPU
    - a process > [multiple threads](##Multi-Thread)
* Hyper Thread: a set of 2 registers
    - when context switching, overhead ↓

## Concurrency 

* *one by one process(share)*: address space(*Data, Code* area), resource(*OS*) in one process
    - the address space of a process = **stack**(one each) + *data(share) + code(share)*
* **one by one thread**: Stack, Program Counter, Registers
    - OS > PCB = **Program Counter + Registers** > Thread Control Block = thread ID + Program Counter + Stack Pointer

## Multi-Thread

* multi-task: multiple processes(single-thread) by fork() -> copied => waste
    - ex. chrome
    - +) security, independency of each webpages
* multi-thread: multiple threads in a process -> shared => no waste
    - ex. explorer
    - +) time, resource, efficiency

<img src="https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter4/4_01_ThreadDiagram.jpg" height = "300" style="float:left"/>
