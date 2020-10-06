# 3.5 Thread

## What is Thread

* Lightweight Process: unit of CPU
    - a process > [multiple threads](##Multi-Thread)
* Hyper Thread: a set of 2 registers
    - when context switching, overhead ↓

## Concurrency 

* *one by one process(share)*: address space(*Data, Code* area), resource(*OS*) in one process
    - the address space of a Process = **stack**(one each) + *data(share) + code(share)*
* **one by one thread**: Stack, Program Counter, Registers
    - Process Control Block = **Program Counter + Registers** > Thread Control Block = thread ID + Program Counter + Stack Pointer

## Multi-Thread

* multi-task: multiple processes(single-thread) by fork() -> copied => waste
    - ex. chrome
    - +) security, independency of each webpages
* multi-thread: multiple threads in a process -> shared => no waste
    - ex. explorer
    - +) time, resource, efficiency

<img src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.cs.uic.edu%2F~jbell%2FCourseNotes%2FOperatingSystems%2F4_Threads.html&psig=AOvVaw0xfFa56efL1QKEnV2xiZa-&ust=1602077223943000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCLDM__GIoOwCFQAAAAAdAAAAABAD" height = 300px/>

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

1. Programs on HDD/SDD -> (long-term scheduler: order process) -> A process on Ready Queue
2. Ready queue -> (short-term scheduler: select process) -> (dispatcher: assign) -> Processor
3. Processor -> 
    1. (short-term scheduler) IO request -> IO Device Queue: blocked and waiting -> IO Device
    2. (short-term scheduler) time-out for assignment
    3. (short-term scheduler) interrupt
    4. (mid-term scheduler) swap out -> paused process -> swap in
4. -> Ready Queue

<hr/>

5. done

# 4.2 scheduling

# 4.3 Multilevel Queue

# 4.4 Scheduling Algorithm
