# Contents

### Chp 1 Introduction to OS

* [1.1 Introduction to OS](#11-introduction-to-os)
  + [Computer](#computer)
  + [System Hierarchy](#system-hierarchy)
    - [Shell](#shell)
    - [kernel](#kernel)
  + [role of OS](#role-of-os)
* [1.2 History of OS](#12-history-of-os)
  + [1940s: no OS - vacuum tubes](#1940s-no-os---vacuum-tubes)
  + [early 1950s: no os - operator](#early-1950s-no-os---operator)
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
  + [how digital H/W system works: by **clocking**](#how-digital-hw-system-works-by-clocking)
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
  + [2 spaces of memory](#2-spaces-of-memory)
* [3.2 Operation of Process](#32-operation-of-process)
* [3.3 Five States of a Process](#33-five-states-of-a-process)
    - [ready, running, blocked, suspended ready, suspended blocked](#ready-running-blocked-suspended-ready-suspended-blocked)
* [3.4 Context switching](#34-context-switching)
  + [Process Context](#process-context)
  + [Context switching](#context-switching)
* [3.5 Thread](#35-thread)
  + [What is Thread](#what-is-thread)
  + [What a Thread has](#what-a-thread-has)
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
  + [examples](#examples)
  + [Scheduling Algorithm Evaluation](#scheduling-algorithm-evaluation)
    - [Average Waiting Time](#average-waiting-time)
    - [Average Turn-around Time](#average-turn-around-time)

### Chp 5 Process Synchronization

* [5.2 Shared Resource and Critical Section](#52-shared-resource-and-critical-section)
  + [concurrency problem](#concurrency-problem)
* [5.3 Critical Section Synchronization](#53-critical-section-synchronization)
  + [conditions](#conditions)
  + [solution](#solution)
    - [1. **test-and-set code** at the same time supported by HW](#1-test-and-set-code-at-the-same-time-supported-by-hw)
    - [2. **Peterson** Algorithm](#2-peterson-algorithm)
    - [3. **Dekker** Algorithm](#3-dekker-algorithm)
    - [4. **Semaphore** Tool](#4-semaphore-tool)
    - [5. **Monitor**](#5-monitor)
    - [ex. producer-consumer problem](#ex-producer-consumer-problem)
* [6.1 Introduction to Deadlock](#61-introduction-to-deadlock)
  + [what is?](#what-is?)
  + [how to express?](#how-to-express?)
  + [when?](#when?)
    - [conditions](#conditions)
  + [how to resolve?](#how-to-resolve?)
    - [1. deadlock prevention](#1-deadlock-prevention)
    - [2. deadlock avoidance](#2-deadlock-avoidance)
    - [3. deadlock detection & recovery](#3-deadlock-detection-&-recovery)
    - [4. deadlock ignorance](#4-deadlock-ignorance)

<hr/>

##### Chp 1 Introduction to OS

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

## 1940s: no OS - vacuum tubes

* ENIAC: vacuum tubes on 1, off 0
* no OS, instead *hard-wiring* => external program (<=> stored-program)

## early 1950s: no os - operator

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

## how digital H/W system works: by **clocking**

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

## 2 spaces of memory 

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

## What is Thread

* Thread = a basic unit of CPU
* subsets of a process: a process > [multiple threads](#Multi-Thread)
* Hyper Thread = a set of 2 registers 
    - why? when context switching, overhead ↓

## What a Thread has

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

## examples

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

* Waiting time is the sum of the periods spent waiting in the ready queue. / num of processes
* start time - arrival time (- burst time)

### Average Turn-around Time

* Turnaround time is the sum of the periods spent waiting to get into memory, waiting in the ready queue, executing on the CPU, and doing I/O. / num of processes
* turn-around time - arrival time

##### Chp 5 Process Synchronization

# 5.2 Shared Resource and Critical Section

## concurrency problem

* A *race condition* is a situation when *cooperating threads*(<->independent threads) code that would access a *shared resource* could do so in such a way as to cause unexpected results.
*  ex. producer-consumer problem: inconsistent num of resources, sharing hardware resources: printer

=> they need **synchronization**

* how? *atmoic operation*: cannot stop operation 
* then? **mutual exclusion**(mutex): only one process in **critical section**

# 5.3 Critical Section Synchronization

how to resolve synchronization

## conditions

1. using 1 boolean variable: cause **mutex**(multi processes in critical section)
2. using 2 boolean variables: cause **bounded waiting**(stuck forever)
3. using 1 integer variable: cause **progress flexibility**(if p2 stopped, p1 cannot go ahead)

## solution

### 1. **test-and-set code** at the same time supported by HW

``` cpp
lock = true; while(lock == true)
```

### 2. **Peterson** Algorithm

* *using 2 variables - lock, *turn* 
* BUT can cause busy-waiting

``` cpp
while(lock1==true && turn==2)
```

### 3. **Dekker** Algorithm

* *using 2 variables - lock, *turn* 
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

: an integer variable S which indicate the number of resources(ticket) available in the system

#### process access the shared resources

* atmoic operations on S
    - P(): disable interrupts -> acquire -> enable interrupts
    - S(): disable interrupts -> release -> enable interrupts
* BUT can cause deadlock 

``` cpp
Semaphore() //initiate

P(){ // wait()
    block() // to the semaphore queue 
}
// critical section 

V(){ // signal()
    wake_up() // to the ready queue of OS
}
```

### 5. **Monitor**

: abstract data types

1. shared data variables: only by the procedures
2. procedures(only one procedure can be executed at a time))

#### process access the shared variables in the monitor

access it through the procedures.

### ex. producer-consumer problem

* pro(): after empty.signal 
* con(): after full.signal

``` cpp
pro(){
    if(full){
        full.signal();
        full.wait() // suspended in block queue of that condition variable 
        // empty.signal();
        sum+=1; // executed and processing about the shared variable
    }
}
```

# 6.1 Introduction to Deadlock

## what is?

* Deadlock(=Circular wait): by the relationship between more than 2 processes
    - requested resources are blocked by the other processes
* Starvation: by OS
    - the requested resources are continuously used by high priority processes.

## how to express?

Resource-Allocation Graph

* **process**: circle
* **resource**: square, *instances*: dots
* process **<-** resource : allocation edges
* process **->** resource : request edges

=> resources: request -> use -> release

## when?

a situation where the several processes in CPU compete for the finite number of resources available within the CPU

* shared variable: flag
* Dining philosophers problem: at a round table

### conditions

There are four conditions which must occur *simultaneously* to *raise* the condition of *deadlock.*

1. Mutual exclusion: sharing forks X
    - *Only one process at a time* can use a resource if other process requests the same resource, it has to *wait* till the process using resource releases it.
2. No Preemption: taking away forks X
    - The process holding the resources can not be preempted. The process holding the resource *must release the resource* voluntarily when it has completed its task.
3. Hold and Wait: monopolization of two forks X
    - A process must be *holding* a resource and *waiting* to acquire another resource that is held by some other process.
4. Circular wait: a linear table, in order O
    - The process must wait for resources *in a circular* fashion.

## how to resolve?

### 1. deadlock prevention

(BEFORE) Deadlocks can be prevented by preventing at least one of the four required conditions:

1. Mutex: unrealistic
2. No Preemption: unrealistic
3. Hold and Wait: processes holding resources must release them before requesting new resources, and then re-acquire them
    - -) it is hard to *know* all the resources it has
    - -) the *time* that it need that resource is changeable
    - -) A process that requires *lots of resources <* A process that requires a few resources 
    - -) *batch* system
4. Circular wait: number all resources

=> Even thought deadlock is not often, these ways restrict process

### 2. deadlock avoidance

(BEFORE) 
manage resources allocation allowing only safe state 

* State: safe -> unsafe -> deadlocked ∝ the num of allocated resources

1. Single Instance<sub>/ resource types
    - **Resource Allocation Graph Algorithm**) deadlock states: can be detected by cycles in the RSA graphs
    - request edges, allocation edges, *claim edges*
2. Multiple Instance<sub>/ resource types
    - Banker's Algorithm) Safe states = ***Expect****=Max-Allocation* ***=<*** ***Available****=Total-ΣAllocation*
        - ex. allocate -> return its Max -> allocate to other one -> .. => Total == Available

=> 

* -) need to declare all the resources in advance
* -) fixed Total resources
* -) even available -> not allocate => inefficient 

### 3. deadlock detection & recovery

(AFTER) monitoring the resource-allocation graph and recovering it

* NO MAX, allocate the available resources right away

#### deadlock detection

1. Single Instance<sub>/ resource types
    - **Resource Allocation Graph Algorithm**) deadlock states: can be detected by cycles in the RSA graphs
    - request edges, allocation edges
2. Multiple Instance<sub>/ resource types
    - Banker's Algorithm)***Request=<Available****=Total-ΣAllocation*
        - ex. first allocate to the process whose request == 000 ∵ it will return soon => Total == Available

#### deadlock recovery

1. process termination: all the processes || one by one in order 
2. resource preemption: preempt a resource from the least-cost process => starvation => considering counts to call to preempt

### 4. deadlock ignorance

the way to resolve deadlock makes overload on system

* => ignore deadlock on os
* => users cover it
