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

<img src="https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter4/4_01_ThreadDiagram.jpg" height = "300" style="float:left"/>

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
3. Processor -> waiting, being interrupted, being paused
    1. (short-term scheduler) IO request -> IO Device Queue: blocked and waiting -> IO Device
    2. (short-term scheduler) time-out for assignment
    3. (short-term scheduler) interrupt
    4. (mid-term scheduler) swap out -> paused process -> swap in
4. -> Ready Queue

<hr/>

5. done

# 4.2 Considerations for Scheduling

## Scheduling Algorithm

| basis | Preemptive Scheduling | Non-Preemptive Scheduling |
| ---- | ---- | ---- |
| when can start a new process | suspended by OS or interrupted | unless termination of the process or I/O |
| --- | response time ↑ | throughput ↓ (even IO bound job has to wait for a long time) |
| example | time-sharing | batch system |

## The Criteria 

CPU Utilization ↑ Throughput ↑ Waiting Time ↓ Response Time ↓ Turn-around time ↓ => A Better Algorithm

* waiting time: ~ start execution of process
* response time: ~ start first output of process
* turn-around time: ~ terminate and turn out all the resources

## Process Priority  

* kernal > general process
* foreground > background process
* interactive > batch process
* IO bound job > CPI bound job

# 4.3 Multilevel Queue

# 4.4 Scheduling Algorithm
