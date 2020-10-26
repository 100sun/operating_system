##### Chp 1 Introduction to OS

# Contents

### Chp 1 Introduction to OS

* [Contents](#contents)
    - [Chp 1 Introduction to OS](#chp-1-introduction-to-os)
    - [Chp 1 Introduction to OS](#chp-1-introduction-to-os)
    - [Chp 2 Computer Architecture](#chp-2-computer-architecture)
    - [Chp 3 Process and Thread](#chp-3-process-and-thread)
    - [Chp 4 CPU Scheduling](#chp-4-cpu-scheduling)
    - [Chp 5 Process Synchronization](#chp-5-process-synchronization)
* [1.1 Introduction to OS](#11-introduction-to-os)
  + [Computer](#computer)
  + [System Hierarchy](#system-hierarchy)
    - [Shell](#shell)
    - [kernel](#kernel)
  + [role of OS](#role-of-os)
* [1.2 History of OS](#12-history-of-os)
  + [1940s: no OS](#1940s-no-os)
  + [early 1950s: no OS](#early-1950s-no-os)
  + [1950s: batch processing system](#1950s-batch-processing-system)
  + [early 1960s: interactive system](#early-1960s-interactive-system)
  + [mid 1960s: multiprogramming system](#mid-1960s-multiprogramming-system)
  + [late 1960s: time sharing system](#late-1960s-time-sharing-system)
  + [late 1970s: distributed system](#late-1970s-distributed-system)
  + [1990s-now: client/server system](#1990s-now-clientserver-system)
  + [early 2000s-now: P2P system](#early-2000s-now-p2p-system)

### Chp 2 Computer Architecture

* [2.1 basic configuration](#21-basic-configuration)
  + [international units](#international-units)
  + [how digital H/W system works: by clocking](#how-digital-hw-system-works-by-clocking)
* [2.2.1 CPU](#221-cpu)
  + [how to execute a source file](#how-to-execute-a-source-file)
  + [Instruction Cycle](#instruction-cycle)
* [2.2.1 Memory](#221-memory)
  + [Memory Types](#memory-types)
  + [Memory Hierarchy](#memory-hierarchy)
  + [Why Protection is needed](#why-protection-is-needed)
  + [Booting Process](#booting-process)
* [2.3 computer performance improvement technology](#23-computer-performance-improvement-technology)
  + [CPU execution mode: dual mode](#cpu-execution-mode-dual-mode)
    - [CPU-I/O Burst Cycle](#cpu-io-burst-cycle)
  + [How to handle the sudden events by I/O](#how-to-handle-the-sudden-events-by-io)
    - [Polling](#polling)
    - [Interrupt](#interrupt)

### Chp 3 Process and Thread

* [3.1 Introduction to Process](#31-introduction-to-process)
  + [program vs process](#program-vs-process)
  + [two spaces of memory](#two-spaces-of-memory)
* [3.2 Operation of Process](#32-operation-of-process)
* [3.3 Five States of a Process](#33-five-states-of-a-process)
    - [ready, running, blocked, suspended ready, suspended blocked](#ready-running-blocked-suspended-ready-suspended-blocked)
* [3.4 Context switching](#34-context-switching)
  + [Process Context](#process-context)
  + [Context switching](#context-switching)
* [3.5 Thread](#35-thread)
  + [What Thread is](#what-thread-is)
  + [WhatThread has](#whatthread-has)
  + [Thread States](#thread-states)
  + [Single-Thread VS Multi-Thread](#single-thread-vs-multi-thread)

### Chp 4 CPU Scheduling

* [4.1 Introduction to Scheduling](#41-introduction-to-scheduling)
  + [What is scheduling](#what-is-scheduling)
  + [CPU Schedulers](#cpu-schedulers)
* [4.2. Considerations for Scheduling](#42-considerations-for-scheduling)
  + [Criteria](#criteria)
    - [time criteria](#time-criteria)
  + [Process Priority](#process-priority)
* [4.3. Scheduling Algorithm](#43-scheduling-algorithm)
  + [types](#types)
    - [preempt?](#preempt?)
    - [give priority?](#give-priority?)
  + [FCFS, SJF, HRN, RR, MSQ, MSFQ](#fcfs-sjf-hrn-rr-msq-msfq)
  + [Scheduling Algorithm Evaluation](#scheduling-algorithm-evaluation)
    - [Average Waiting Time](#average-waiting-time)
    - [Average Turn-around Time](#average-turn-around-time)

### Chp 5 Process Synchronization

* [5.2 Shared Resource and Critical Section](#52-shared-resource-and-critical-section)
    - [Concurrency Problem](#concurrency-problem)
    - [critical section](#critical-section)
* [5.3 Critical Section Synchronization](#53-critical-section-synchronization)
  + [conditions to resolve critical section problem](#conditions-to-resolve-critical-section-problem)
  + [solutions to resolve critical section problem](#solutions-to-resolve-critical-section-problem)
    - [1. HW support](#1-hw-support)
    - [2. **Peterson** Algorithm](#2-peterson-algorithm)
    - [3. **Dekker** Algorithm](#3-dekker-algorithm)
    - [4. **Semaphore** Tool](#4-semaphore-tool)
    - [5. **Monitor**](#5-monitor)
    - [ex. producer-consumer problem](#ex-producer-consumer-problem)

### Chp 6 Deadlock

* [what is Deadlock?](#what-is-deadlock?)
* [how to express Deadlock?](#how-to-express-deadlock?)
* [when Deadlock happen?](#when-deadlock-happen?)
* [how to resolve Deadlock? - before](#how-to-resolve-deadlock?---before)
  + [1. deadlock prevention](#1-deadlock-prevention)
  + [2. deadlock avoidance](#2-deadlock-avoidance)
* [how to resolve Deadlock? - after](#how-to-resolve-deadlock?---after)
  + [3. deadlock detection & recovery](#3-deadlock-detection-&-recovery)
  + [4. deadlock ignorance](#4-deadlock-ignorance)

<hr/>

# 1.1 Introduction to OS

## Computer

* internal parts) on motherboard: the processor (CPU), memory (RAM), hard drive, and video card
* external parts) not on motherboard = I/O devices: monitor, keyboard, mouse
* von Neumann architecture: CPU + Main Memory + IO devices

## System Hierarchy

**user >> app s/w >> system s/w** > shell > kernel **>> h/w**

### Shell

* interpreting user's command
* the interface between the kernel and user

### kernel

* the core of the operating system that controls all the tasks of the system
* power-on: OS on HDD -> kernel on memory ~ until power-off

## role of OS

* performance ↑
    1. **resource management**(allocation)
        - S/W management: manage process, file,,,
        - processor management: manage CPU
        - memory management: manage memory
        - file management: manage HDD
        - IO management: manage keyboard, monitor, printer
    2. resource protection
        - ex. prevent from monopolizing CPU
* convenience ↑
    3. H/W interface
    4. user interface 
        - ex. GUI

=> efficiency, reliability, scalability, convenience

# 1.2 History of OS

## 1940s: no OS

* ENIAC: vacuum tubes on 1, off 0
* no OS, instead *hard-wiring* => external program (<=> stored-program)

## early 1950s: no OS

* no OS, instead *operator*
    - punched card reader -> **processor + memory** -> line printer

## 1950s: batch processing system

* yes OS, using *resident monitor* 
    - punched card reader -> **processor + memory(OS + user)** -> line printer

## early 1960s: interactive system

* user **<->** monitor, keyboard **<->** memory(OS + user)

## mid 1960s: multiprogramming system

* multiple jobs at the same time on 1 CPU 
* => OS needs to do cpu scheduling, memory management...

## late 1960s: time sharing system

* = multitasking system 
* by time slice = time quantum
* interactive computer: connected monitor and keyboard to computer

## late 1970s: distributed system

* mainframe(huge c.) X  => distributed system by TCP/IP O
* personal computer

## 1990s-now: client/server system

## early 2000s-now: P2P system

##### Chp 2 Computer Architecture 

# 2.1 basic configuration

## international units

* International System of units: 10<sup>3</sup>
* International Electrotechnical Commission: 2<sup>10</sup>
* p < n < μ < m < K < M < G < T
* (SI) 10<sup>-4 < -3 < -2 < -1 < 1 < 2 < 3 < 4</su[]>

## how digital H/W system works: by clocking

one cycle = from 1 ~ to 0

* T(clock period): __seconds / one cycle (ps)
* F(clock frequency): __cycles / a second (Hz)
* T * F = s/c * c/s = 1

# 2.2.1 CPU

## how to execute a source file

1. secondary memory(long-term memory): compiling process
    - .c -> (compiler) -> .obj -> (linker-libs) -> .exe
2. loads on main memory(short-term memory)
    - instruction memory | data memory
3. process the [Instruction cycle](#-Instruction-Cycle) between main memory <->  CPU

## Instruction Cycle

1. **Fetch** the address of the next instruction -> PC, the value of the instruction -> IR
2. **Decode** interpret the instruction in IR
3. **Execute** it on ALU.
4.  **Store** it on GPR or data memory

* ***registers***: faster and more expensive than memory
    - GPR(General Purpose Register) e.g. data processing...
    - SPR(Special Purpose Register) e.g. Program Counter, Instruction Register, Stack Pointer...

# 2.2.1 Memory

## Memory Types 

* short-term memory
    - **D**ynamic **R**andom **A**ccess **M**emory: main memory
    - **S**tatic **R**andom **A**ccess **M**emory: caches of CPU
* long-term memory
    - flash memory: e.g. USB
    - SSD(Solid State Drive): replacing HDD 

## Memory Hierarchy 

| CPU (**register** > processor > SRAM a.k.a **caches**) > DRAM a.k.a **main memory** > **HDD** |
| --------------------------------------------------- |
| -----------------------------> price↓ speed↓ size↑ |

* Processor: gives 8bit(1byte) **address** to memory and the *memory* gives back **data** by the address to the processor

## Why Protection is needed

now time-sharing system => can invade other program's memory: *interrupt* -> terminate it

## Booting Process

= loading OS to memory

1. ROM's POST command to CPU
2. CPU copies **boot-strap-code** from 0 sector in *HDD to RAM* to execute in the kernel of RAM

# 2.3 computer performance improvement technology

## CPU execution mode: dual mode

CPU <-> Program(user+OS)

* mode_bit = 0: Kernel mode to execute a kernel process
* mode_bit = 1: User mode to execute a user process

### CPU-I/O Burst Cycle

how to execute a process

#### burst

1. **CPU Burst**: when the process is being *executed* in the CPU
2. **I/O Burst**: when the CPU is *waiting* for I/O for further execution
3. ready queue: the process goes into the ready queue for the next CPU burst

#### bound job

* **CPU bound job** ex. simulation program (complicated)
    - duration ↑ => frequency ↓
    - *Long CPU burst <-> Short IO burst*
* **IO bound job** ex. docx program (keyboard)
    - duration ↓ => frequency ↑
    - *short CPU burst <-> long IO burst*

=> to save time: priority of IO bound job ↑ 

## How to handle the sudden events by I/O

### Polling

* *CPU* keeps on *checking* I/O devices at regular interval whether it needs CPU service => in-order work

``` c++
void main(void){

    while(1){
        if(button_pressed) // by the SW (CPU)
            do_something();
    }

}

``` 

### Interrupt

* *I/O device interrupts* the CPU and tell CPU that it need CPU service => give priorities
* interrupt => CPU: user mode -> kernel mode

``` c++
Interrupt_Service_Routine(BUTTON_PRESS_vect){
    do_something();
}

void main(void){
    setup_button_press_interrupt(); // by the HW (IO device)
    while(1){
    }
}
```

#### S/W Interrupt

via Kernal of OS

* *system call* is the job when *program1* requests OS to interrupt -> PC moves *from program1 to ISR* of OS
* *exception*: => check [what *mode*](#Dual-mode-when-CPU-works) of CPU now via mode_bit and *terminate* the program

#### H/W Interrupt = I/O Interrupt

via 𝜇C

* is the job when *IO device* requests OS to interrupt for program1 -> PC moves *from the program1 to ISR*
* more than 2 I/O interrupts can happen simultaneously 

1. A mouse moved = An interrupt happened
2. Current process: blocked -> out of CPU, in the I/O device queue
2. Store the info of the paused process
3. Execute ISR(Interrupt Service Routine) whose address is stored in **IVC**(Interrupt Vector Table).
4. CPU: handle that interrupt
5. Restart the process

#### Timer Interrupt

Time-Sharing System by setting timer via * *

##### Chp 3 Process and Thread

# 3.1 Introduction to Process

## program vs process

| program         | process            |
|-----------------|--------------------|
| static state    | dynamic state      |
| on HDD | on [memory](#memory) |
| before creating | before terminating |
| process - PCB | program + PCB |

1. A **program** on *HDD* got a **PCB** from OS space of memory  => A **process** on user space of *memory*
2. The **process** returned the **PCB** => ** **
* Process Control Block contains process-related info e.g. *pointer*(for queue)*, process state, PID*(unique), registers' value, memory limits, list of open files

## two spaces of memory 

1. **user space**
    - process A, process B ....
        - **code**: program code *(RDONLY)*
        - **data**: global variables *(RDWR)*
        - **stack**: local variables, pointer of program address  
2. **o**perating **s**ystem **space**
    - [PCB](#PCB) A, PCB B....

# 3.2 Operation of Process

0. '*init* process' when *boot*ing by OS
1. **fork() system call**: starts *child process* which is a copy of the parent process
    - pid = fork(): copy all but not PID, Parent PID, Children PID
    - => pid == 0: child(o) / pid == -1: error
2. program *loads to the child process*
3. **exec() system call**: replaces the current process image with new one
4. if *child exit*(PID) -> parent collects its data
    - data collection *fail* => **Zombie Process**
    - *no parent* process => **Orphan Process**

# 3.3 Five States of a Process

### ready, running, blocked, suspended ready, suspended blocked

<img src="https://github.com/100sun/operating_system/blob/master/process-state-diagram.JPG" height="400"/>

# 3.4 Context switching

## Process Context

= info about current process state

* HW context: PC, registers
* memory context: process code, process data, process stack
* kernel context:  kernel stack, kernel data(∋PCB)

## Context switching

* = re-scheduling
* why? time-sharing system
* when? io/timer interrupt -> ISR or context switching
* how? store the current process context in its PCB and get the next process context from its PCB
* ex? p2 ready, p1 running -> timeout -> store p1 state in PCB 1 -> get p2 state from PCB2 -> dispatch p2 -> p2 running, p1 ready 
* disadvs? overhead => [multi-thread](#Multi-Thread) to overhead ↓

# 3.5 Thread

## What Thread is

* Thread = a basic unit of CPU
* subsets of a process: a process > [multiple threads](#Multi-Thread)
* Hyper Thread = a set of 2 registers 
    - why? when context switching, overhead ↓

## WhatThread has

(A process has 1 address space - code+data+stack)

* Multiple processes *share Code address space, Data address space, OS resources* for one process
* Each process has its own **Stack* address space, PC, Register set**.
    - TCB = thread ID + thread PC(->move in the Code address space) + thread SP(pointing the Stack address space)

## Thread States

* new -> **ready** -> dispatch -> **running** -> terminated
    1. running -> timeout -> ready
    2. running -> **blocked** -> ready

## Single-Thread VS Multi-Thread

* single-thread = **multi-task**: multiple processes by fork() -> copied => waste
    - ex. chrome
    - +) security, independency of each webpages
* **multi-thread**: multiple threads in a process -> shared => no waste
    - ex. explorer
    - +) time, resource, efficiency

<img src="https://github.com/100sun/operating_system/blob/master/multi-thread.JPG" height = "300"/>

##### Chp 4 CPU Scheduling 

# 4.1 Introduction to Scheduling

## What is scheduling

the method that allows **when and what process cpu resource can be assigned** by order of ready queue of *PCB* for more efficiency between the processes whose most jobs are using *CPU VS I/O*

## CPU Schedulers

* long-term scheduler = job scheduler: takes process from new
* mid-term scheduler=the degree of multiprogramming↓ : takes process from running
* short-term scheduler = CPU scheduler: takes the process from ready

<img src="https://github.com/100sun/operating_system/blob/master/process-state-diagram.JPG" height="400"/>

# 4.2. Considerations for Scheduling

## Criteria

CPU Utilization ↑ Throughput ↑ Waiting Time ↓ Response Time ↓ Turn-around time ↓

### time criteria

arrival < execution < first output < termination 

* waiting time: ~ until execution of process
* response time: ~ until first output of process
* turn-around time: ~ until termination and turn-out all the resources

waiting time ⊂ response time ⊂ turn-around time

## Process Priority  

* kernal > general process
* foreground > background process
* interactive > batch process
* IO bound job > CPI bound job

# 4.3. Scheduling Algorithm

## types

### preempt?

| | Non-Preemptive Scheduling | Preemptive Scheduling |
| ---- | --------- | -------- |
| when can start a new process | can't until *termination* of the process or I/O | when suspended by *OS or interrupted* |
| disadvs | throughput ↓ <Br/>(even IO bound job has to wait for a long time) | response time ↑ |
| e.g. algorithm | FCFS, SJF, HRN | SRT, RR, MLQ, MLFQ |

### give priority?

||Static Priority|Dynamic Priority|
|----|----|----|
|priority|processes are permanently assigned to a queue|allows a process to move between queues|
|level of implementation|↓|↑|
|efficiency|↓|↑|
| e.g. algorithm |MLQ, FCFS|MLQF, SJF, HRN, SRT |

#### MLQ

Multilevel Queue: How To Assign Priority of Process

1. **ready** queue
    1. enqueue process to the back in its priority queue 
    2. CPU scheduler: dispatch the front process in priority 0 queue to the CPU
2. **waiting** queue (blocked by IO request)
    - make *multiple* processes be ready *by checking IV*

+) automatically separate IO bound job and CPU bound job

## FCFS, SJF, HRN, RR, MSQ, MSFQ

||FCFS|SJF|HRN|SRT|RR|MSQ|MSFQ|
|---|---|---|---|---|---|---|---|
|alleviation|First Come First Served|Shortest Job First|Highest Response ratio Next|Shortest Remaining Time|Round Robin|Multilevel Queue Scheduling|Multilevel Feedback Queue Scheduling|
|preempt?|non-preemptive|||preemptive<br/>(SJF+preemptive)||||
|prior?|static priority|dynamic priority|||**X**|**static priority**|**dynamic priority**|
|which process first?|**waiting_time↓**|**burst_time↓**|**waiting_time/CPU_burst_length↑**|**remained_burst_time↓**<br/>(SJF+preemptive)|just in order of the ready queue|priority assigned by OS↑|CPU burst length↓|
|advs||convoy effect⇓|starvation⇓||response time⇓|overhead⇓|high flexibility|
|disadvs|efficiency⇓<Br/>∵convoy effect(AWT⇑)|starvation|flexibility⇓|≈ SJF|- time slice⇑ ≈ FCFS<br/>- time slice⇓: context switching⇑<br/>=>time slice↓|flexibility⇓|hard to build and implement|

* starvation: when we have a process having high-priority and long burst time, this leads indefinitely waiting for the process having low-priority
    - solution to Starvation: aging = time ∝ priority
* aging: a technique of gradually increasing the priority of processes that wait in the system for a long time.
    - HRN: considering waiting time as well
    - MLFQ: so that we can separate processes with different CPU-burst characteristics.
        1. If a process uses too much CPU time, it will be moved to a lower-priority queue. 
        2. If a process waits too long in a lower-priority queue, it may be moved to a higher-priority queue.
        * **priority↓ time slices⇑** possibility to burst CPU⇓ CPU burst length⇑ 
        * ex. *IO burst job*: TS⇓* -> CPU burst job*: TS⇑.. *->* ***FCFS***: TS=∞

## Scheduling Algorithm Evaluation

w/ Gantt Chart

### Average Waiting Time

* Waiting time = ∑ the periods spent waiting in the ready queue
* AWT = {start time - arrival time (- burst time)} / #. processes 

### Average Turn-around Time

* Turnaround time = ∑ the periods spent waiting to get into memory + waiting in the ready queue + executing on the CPU + doing I/O jobs
* ATT = {turn-around time - arrival time} / #. processes 

##### Chp 5 Process Synchronization

# 5.2 Shared Resource and Critical Section

### Concurrency Problem

* shared resource: variables, memory, files that N threads(processes) are sharing
* cooperating threads(sharing) <-> independent threads(not sharing)
* race condition: when cooperating threads access a shared resource
* e.g. **producer-consumer problem**: inconsistent result num of resources by order of execution of code when race codintion
* e.g. sharing hardware resources like printer
* => cooperating threads need **synchronization**
* how? using atomic operation: cannot stop operation ex. load/store/add...
* then? **mutual exclusion** = only one process in **critical section** at a time

### critical section

* code section that only one thread can be executed (no multitasking)
* code section which update the shared resources

# 5.3 Critical Section Synchronization

## conditions to resolve critical section problem

1. using *1 boolean* variable: denies **mutex**
    - ∵ lock=true; lock=true;
2. using *2 boolean* variables: leads **bounded waiting**(stuck forever)
    - ∵ while(lock2=true); while(lock1=true);
3. using *1 integer* variable: leads **progress flexibility**(if p2 stopped using critical section, p1 cannot access to the critical section)
    - ∵ int lock1=1;

## solutions to resolve critical section problem

### 1. HW support

execution of test-and-set code at the same time 

``` cpp
lock = true; while(lock == true)
```

### 2. **Peterson** Algorithm

* using 2 variables - lock, *turn* 
* BUT limitation of 2 processes 

``` cpp
while(lock1==true && turn==2)
```

### 3. **Dekker** Algorithm

* using 2 variables - lock, *turn* 
* BUT can cause busy-waiting

``` cpp
while(lock2==true) {

    if(turn==1){
        lock1=false; 
        while(turn==2); 
        lock1=true;
    }
}
```

### 4. **Semaphore** Tool

* using an *int S* which indicate how many resources(ticket) are available in the system
* P, V atomic operations and only S can access to those func.
* BUT can cause deadlock if 2 shared resources

``` cpp
Semaphore(n){
    S=n; // initiate S
} 

// lock acquire (implemented by atomic operation)
P(){ 
    // disable interrupts
    if(S>0) S--; // => "it is being used now" and can access to the section
    block() // wait for the sync signal to access critical section in the Semaphore queue 
    // enable interrupts
}

// critical section 

// lock release(implemented by atomic operation)
V(){ 
    // disable interrupts
    S++; // increase the num of ticket
    wake_up() // send sync signal to the process waiting in the Semaphore queue
    // enable interrupts
}
```

<img src="https://github.com/100sun/operating_system/blob/master/semaphore-o.JPG" width="400"><img src="https://github.com/100sun/operating_system/blob/master/semaphore-x.JPG" width="400">

### 5. **Monitor**

* = MUTEX abstract data types providing by program language ∋ procedures
* only procedures in monitor can access each process.
* only codes inside monitor can access shared resources.
* only one procedure can be executed at a time in monitor.

### ex. producer-consumer problem

* pro(): after empty.signal 
* con(): after full.signal

``` cpp
// other processes are waiting in the Monitor queue.
monitor m{
    // 1. declare shared variables
    int sum;
    condition full, empty;

    // 2. declare procedures that can access to the critical section
    pro(){ // producer process
        if(full){
            full.signal();
            full.wait(); // => empty.signal();
        } 
        sum++;
    }
    con(){ // consumer process
        if(empty){
            empty.signal();
            empty.wait(); // => full.signal();
        } 
        sum--;
    }

    // 3. initiate code
    initial(){}
}
```

##### Chp 6 Deadlock

### what is Deadlock?

|| Deadlock | Starvation |
|--|--|--|
|process|*All* processes keep *waiting* for each other. ∵ *Circular* wait|High priority processes keep executing and *low* priority processes are *blocked*|
|resource|Resources are *blocked* by the *processes*|Resources are continuously *utilized* by high *priority* processes|

### how to express Deadlock?

* Resource-Allocation Graph
    - **process** : ㅇ
    - **resource** : ㅁ ∋ **instances** : •
    - ㅇ **<---** ㅁ : allocation edges
    - ㅇ **--->** ㅁ : request edges
* resources: request -> use -> release 

## when Deadlock happen?

* e.g Dining philosophers problem: at a round table
* when all the four conditions occur.

1. **Mutex**: no sharing forks
2. **No Preemption**: no taking away forks
3. **Hold and Wait**: no monopolization of all forks
4. **Circular wait**: no in-order linear table

## how to resolve Deadlock? - before

### 1. deadlock prevention

* = Deadlocks can be prevented by preventing *at least one* of the four required conditions:
1. **Mutex**: unrealistic
2. **No Preemption**: unrealistic
3. **Hold and Wait**: processes holding resources must *release* them, and then *re-acquire* them+new.
    - -) *batch system*
    - e.g. it is *hard to know* all the resources it has
    - e.g. the *time* that it needs that resource is *changeable*
    - e.g. *A process that requires lots of resources <* A process that requires a few resources 
4. **Circular wait**: *number* all resources
    - -) how to number? -> low flexibility
* => Even though deadlock is not often, these ways *restrict* process too much.

### 2. deadlock avoidance

* = manage resources allocation only allowing safe state 
* state: safe -> unsafe -> deadlocked (∝ #. allocated resources)
1. when Single Instance<sub>/ resource types
    - **Resource Allocation Graph Algorithm**) deadlock states: can be detected by cycles in the graph.
        - request edges, allocation edges, *claim edges*(ㅇ---->ㅁ)
    - Banker's Algorithm
2. when Multiple Instances<sub>/ resource types
    - **Banker's Algorithm**) safe states = **Expect**=Max-Allocation **<=** ***Available**=Total-ΣAllocation
        - ex. *Available=*(allocate)*-Expect*->(return)*+Max*->(allocate)->(return)-> .. => *== Total*
* -) need to declare all the resources in advance
* -) fixed Total resources
* -) even available -> not allocate => inefficient 

## how to resolve Deadlock? - after

### 3. deadlock detection & recovery

* = monitoring the graph and recovering it
* NO MAX, allocate the Available resources right away

#### deadlock detection

1. when Single Instance<sub>/ resource types
    - **Resource Allocation Graph Algorithm**) deadlock states: can be detected by cycles in the RSA graphs
        - request edges, allocation edges
2. when Multiple Instance<sub>/ resource types
    - Banker's Algorithm) even Available==0, can allocate a process whose request == 0
        - Available = -Request +(Request+Allocation)  -Request +(Request+Allocation) .. => == Total
        - ex. 

#### deadlock recovery

1. process termination: all the processes at the same time || one by one in order 
2. resource preemption: preempt a resource from the *least-cost* process => BUT starvation => SO must consider count to be preempted

### 4. deadlock ignorance

* = the way to resolve deadlock makes overload on system
* ignore deadlock on os => users cover it
