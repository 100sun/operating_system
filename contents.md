# 1.1 Introduction to OS
## Computer
## System Hierarchy
### Shell

### kernel

## role of OS
# 1.2 History of OS
## 1940s: ENIAC
## 1950s: batch processing system
## early 1960s: interactive system
## mid 1960s: multiprogramming system
## late 1960s: time sharing system
## late 1970s: distributed system
## 1990s-now: client/server system
## early 2000s-now: P2P system
# 2.1 basic configuration
## international units
## how digital system works: **clocking**
# 2.2.1 CPU
## how to execute a source file
## Instruction Cycle
# 2.2.1 Memory
## Memory Types 
## Memory Hierarchy 
## Why Protection is needed
## Booting Process
# 2.3 computer performance improvement technology
## Dual mode when CPU works
## Hardware Mechanism
### Polling

### Interrupt

#### Types

# 3.1 Introduction to Process
## program vs process
## Architecture 
### elements of memory 

# 3.2 Operation of Process
## process hierarchy
# 3.3 [States of a Process](#queuing-diagram)
# 3.4 Process Control Block & Context switching
## PCB
## Context switching
### why

### when

### process context

### how to switch

## disadvs 
# 3.5 Thread
## What is Thread
## Concurrency 
## Multi-Thread
# 4.1 Introduction to Scheduling
## What is scheduling
## CPU-I/O Burst Cycle
## CPU Schedulers
### Queuing diagram

# 4.2 Considerations for Scheduling
## Scheduling Algorithms
### Preemptive/Non-Preemptive Scheduling

## Process Priority  
# 4.3 Multilevel Queue
### IO Interrupt

## Multilevel Queue
### Priority

### State

# 4.4 Scheduling Algorithm
## Priority Scheduling
|---|---|---|---|---|
## Round Robin Scheduling
### advs

### disadvs

## [Multilevel Queue](#Multilevel-Queue) Scheduling
## Multilevel Feedback Queue Scheduling
## Scheduling Criteria
### what is better

#### waiting time < response time < turn-around time

## Algorithm Evaluation
### Average Waiting Time

### Average Turn-around Time

#### problem

# 5.2 Shared Resource and Critical Section
## concurrency problem
# 5.3 Critical Section Synchronization
## conditions
## solution
### 1. **test-and-set code** at the same time supported by HW

### 2. **Peterson** Algorithm

### 3. **Dekker** Algorithm

### 4. **Semaphore** Tool

#### process access the shared resources

### 5. **Monitor**

#### process access the shared variables in the monitor

### ex. producer-consumer problem

# 6.1 Introduction to Deadlock
## what is?
## how to express?
## when?
### conditions

## how to resolve?
### 1. deadlock prevention

### 2. deadlock avoidance

### 3. deadlock detection & recovery

#### deadlock detection

#### deadlock recovery

### 4. deadlock ignorance

