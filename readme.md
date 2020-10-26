# contents

### Chp 1 Introduction to OS

* [1.1 Introduction to OS](#11-introduction-to-os)
  + [Computer](#computer)
  + [System Hierarchy](#system-hierarchy)
  + [role of OS](#role-of-os)
* [1.2 History of OS](#12-history-of-os)
  + [1940s: ENIAC](#1940s-eniac)
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
  + [how digital system works: **clocking**](#how-digital-system-works-clocking)
* [2.2.1 CPU](#221-cpu)
  + [how to execute a source file](#how-to-execute-a-source-file)
  + [Instruction Cycle](#instruction-cycle)
* [2.2.1 Memory](#221-memory)
  + [Memory Types](#memory-types)
  + [Memory Hierarchy](#memory-hierarchy)
  + [Why Protection is needed](#why-protection-is-needed)
  + [Booting Process](#booting-process)
* [2.3 computer performance improvement technology](#23-computer-performance-improvement-technology)
  + [Dual mode when CPU works](#dual-mode-when-cpu-works)
  + [Hardware Mechanism](#hardware-mechanism)

### Chp 3 Process and Thread

* [3.1 Introduction to Process](#31-introduction-to-process)
  + [program vs process](#program-vs-process)
  + [Architecture](#architecture)
* [3.2 Operation of Process](#32-operation-of-process)
  + [process hierarchy](#process-hierarchy)
* [3.3 States of a Process](#33-states-of-a-process)
* [3.4 Process Control Block & Context switching](#34-process-control-block-&-context-switching)
  + [PCB](#pcb)
  + [Context switching](#context-switching)
* [3.5 Thread](#35-thread)
  + [What is Thread](#what-is-thread)
  + [Concurrency](#concurrency)
  + [Multi-Thread](#multi-thread)

### Chp 4 CPU Scheduling 

* [4.1 Introduction to Scheduling](#41-introduction-to-scheduling)
  + [What is scheduling](#what-is-scheduling)
  + [CPU-I/O Burst Cycle](#cpu-io-burst-cycle)
  + [CPU Schedulers](#cpu-schedulers)
* [4.2 Considerations for Scheduling](#42-considerations-for-scheduling)
  + [Scheduling Algorithms](#scheduling-algorithms)
  + [Process Priority](#process-priority)
* [4.3 Multilevel Queue](#43-multilevel-queue)
  + [Multilevel Queue](#multilevel-queue)
* [4.4 Scheduling Algorithm](#44-scheduling-algorithm)
  + [Priority Scheduling](#priority-scheduling)
  + [Round Robin Scheduling](#round-robin-scheduling)
  + [Multilevel Queue Scheduling](#multilevel-queue-scheduling)
  + [Multilevel Feedback Queue Scheduling](#multilevel-feedback-queue-scheduling)
  + [Scheduling Criteria](#scheduling-criteria)
  + [Algorithm Evaluation](#algorithm-evaluation)

### Chp 5 Process Synchronization

* [5.2 Shared Resource and Critical Section](#52-shared-resource-and-critical-section)
  + [concurrency problem](#concurrency-problem)
* [5.3 Critical Section Synchronization](#53-critical-section-synchronization)
  + [conditions](#conditions)
  + [solution](#solution)

### Chp 6 Deadlock

* [6.1 Introduction to Deadlock](#61-introduction-to-deadlock)
  + [what is?](#what-is?)
  + [how to express?](#how-to-express?)
  + [when?](#when?)
  + [how to resolve?](#how-to-resolve?)

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

## How to handle the sudden events by the devices when CPU busy

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

#### Types

* **S/W Interrupt** via Kernal of OS
    - *system call* is the job when *program1* requests OS to interrupt -> PC moves *from program1 to ISR* of OS
    - *exception*: => check [what *mode*](#Dual-mode-when-CPU-works) of CPU now via mode_bit and *terminate* the program
* [**H/W Interrupt**](#io-interrupt) via 𝜇C
    - is the job when *IO device* requests OS to interrupt for program1 -> PC moves *from the program1 to ISR*
* **Timer Interrupt**: Time-Sharing System by setting timer via * *

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

| process state | [scheduler](#queuing-diagram) | 
|----|---|
| 1. new: program + PCB => Process and PCB created | 1. Programs on HDD/SDD -> (long-term scheduler: order process) -> A process in the Ready Queue |
| 2. **ready**: waiting in the ready queue | 2. Ready queue -> (short-term scheduler: select one PCB and let dispatcher to assign CPU(processor) to it) -> Processor |
| 3. **running**: during time-slice | 3. Processor -> blocked, interrupted, paused | 
|active (CPU)<br/>- after time-slice -> *timeout(PID)* => "ready"<br/>- IO request -> **blocked**(PID): waiting in the IO device queue -> IO complete -> interrupt -> wakeup(PID) -> "ready"<br/>|-(short-term scheduler) time-out for assignment<br/>-(short-term scheduler) IO request -> IO Device Queue: blocked and waiting -> IO Device<br/>-(short-term scheduler) interrupt|
|inactive (swap area)<br/>- "ready", "blocked" -> (expelled, delayed, long cycle) -> swap out -> **suspended blocked** -> (wakeup) -> **suspended blocked** -> swap in => "ready", "blocked" |-(mid-term scheduler) swap out -> paused process -> swap in|
|4. terminated: code & data eliminated from *memory and -PCB*<br/>- normal - *exit()* during "running", after completing jobs<br/>- abnormal - core dump||

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

## What Thread has

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

<img src="https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter4/4_01_ThreadDiagram.jpg" height = "300"/>

<Br/>

# 4.1 Introduction to Scheduling

## What is scheduling

the method that allows **when and what process cpu resource can be assigned** by order of ready queue of *PCB* for more efficiency between the processes whose most jobs are using *CPU VS IO*

## CPU-I/O Burst Cycle

how to execute a process

1. **CPU Burst**: when the process is being *executed in the CPU*
    1. Long CPU burst : **CPU bound job** ex. simulation program (complicated)
        * duration ↑ => frequency ↓
    2. Short CPU burst : **I/O bound job** ex. docx program (keyboard)
        * duration ↓ => frequency ↑
        * => *priority* of process ↑ 
2. **I/O Burst**: when the *CPU is waiting* for I/O for further execution
3. ready queue: the process goes into the ready queue for the next CPU burst

## CPU Schedulers

### Queuing diagram

how to express process-scheduling

1. Programs on HDD/SDD -> (long-term scheduler: order process) -> A process in the Ready Queue
2. Ready queue -> (short-term scheduler: select one PCB) -> (dispatcher: assign) -> Processor
3. Processor -> blocked, interrupted, paused

    1. (short-term scheduler) IO request -> IO Device Queue: blocked and waiting -> IO Device
    2. (short-term scheduler) time-out for assignment
    3. (short-term scheduler) interrupt
    4. (mid-term scheduler) swap out -> paused process -> swap in

4. -> Ready Queue

<hr/>

5. done

# 4.2 Considerations for Scheduling

## Scheduling Algorithms

### Preemptive/Non-Preemptive Scheduling

| basis | Preemptive Scheduling | Non-Preemptive Scheduling |
| ---- | ---- | ---- |
| when can start a new process | suspended by *OS or interrupted* | unless *termination* of the process or I/O |
| --- | response time ↑ | throughput ↓ <Br/>(even IO bound job has to wait for a long time) |
| [e.g.](#Priority-Scheduling) | SRT, RR | FCFS, SJF, HRN |

## Process Priority  

* kernal > general process
* foreground > background process
* interactive > batch process
* IO bound job > CPI bound job

# 4.3 Multilevel Queue

### IO Interrupt

more than 2 io interrupts can happen simultaneously 

1. mouse moved, interrupt happened -> current process: paused, out of CPU
2. temporarily store the info of the process
3. **Interrupt Vector Table**: address of ISR -> Interrupt Service Routine: code -> 
4. CPU: handle that interrupt -> restart the process

## Multilevel Queue

by priority of the multiple ready-queues

* ex. queue 0: HDD -> queue 1: CD-ROM -> ...

### Priority

||Static Priority|Dynamic Priority|
|----|----|----|
|priority|[cannot be changed](#Multilevel-Queue-Scheduling)|[can be changed](#Multilevel-Feedback-Scheduling)|
|work|↓|↑|
|efficiency|↓|↑|

### State

1. **ready**: dispatch *one* process
    - priority in PCB: insert process in that specific priority queue 
    - CPU scheduler: dispatch the prior process to the CPU
2. **waiting**: make *multiple* processes be ready
    - check IV table: make the prior process in that specific priority queue be ready 

# 4.4 Scheduling Algorithm

## Priority Scheduling

* ex: FCFS, SJF, HRN, [static, dynamic](#priority)
* -: starvation(∵convoy effect), overhead(∵context-switching)-> low efficiency
* => solution: [aging](#Multilevel-Feedback-Queue-Scheduling), considering waiting time as well(SRT)

||FCFS|SJF|HRN|SRT|
|---|---|---|---|---|
|alleviation|First Come First Served|Shortest Job First|Highest Response ratio Next|Shortest Remaining Time|
|type|non-preemptive|||preemptive(time slice O [re-scheduling](#context-switching) O)|
|priority↑|waiting_time↓|burst_time↓|(waiting_time/CPU_burst_length)+1↓|remained_burst_time↓|
|disadvs|low efficiency<Br/>∵convoy effect(AWT⇑)|starvation<br/>∵when the first process takes too long|starvation still|

## Round Robin Scheduling

RR: just in order of the ready queue

### advs of RR

response time ⇓

### disadvs of RR

* time slice⇑ ≈ FCFS: AWT⇑ -> starvation
* time slice⇓ ≈ SRT: context switching -> low efficiency

## Multilevel Queue Scheduling

[multilevel-queue](#Multilevel-Queue)
by static priority

## Multilevel Feedback Queue Scheduling

by dynamic priority

* each ready-queue: **priority↓ time slices⇑** the rate to burst CPU↓ CPU burst length⇑ 
* ex: *IO burst job*: TS⇓* -> CPU burst job*: TS⇑.. *->* ***FCFS***: TS=∞(∵ it has been moved lots.. 😞)
* *aging*: a process that waits too long in a lower-priority queue may be moved to a higher-priority queue.
* hard to build and implement

## Scheduling Criteria

### what is better

CPU Utilization ↑ Throughput ↑ Waiting Time ↓ Response Time ↓ Turn-around time ↓

#### waiting time < response time < turn-around time

* waiting time: ~ start execution of process
* response time: ~ start first output of process
* turn-around time: ~ terminate and turn out all the resources

## Algorithm Evaluation

w/ Gantt Chart

### Average Waiting Time

* Waiting time is the sum of the periods spent waiting in the ready queue. / num of processes
* time until started - arrival time (- burst time)

### Average Turn-around Time

* Turnaround time is the sum of the periods spent waiting to get into memory, waiting in the ready queue, executing on the CPU, and doing I/O. / num of processes
* time until turned around - arrival time

#### problem

<details>
<summary>open</summary>

|process|arrival time|execution time|
|---|---|---|
|P1|0|20|
|P2|1|14|
|P3|2|8|
|P4|3|16|

<img src="https://github.com/100sun/operating_system/blob/master/cpu_scheduling_evaluation_ex.png" height=400/>

</details>
=> AWT/ART: SRT < SJF < HRN < FCFS < RR

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
