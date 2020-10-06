# 2.1 basic configuration

## international units

* (SI) 1km = 10<sup>3</sup>m / (IEC) 2<sup>10</sup>
    - K < M < G < T
    - 1 < 2 < 3 < 4
* (SI) 1mm = 10<sup>-3</sup>m
    - m > μ > n > p
    - -1 > -2 > -3 > -4

## how digital system works: **clocking**

one cycle = 1-0

* T(clock period): __seconds / one cycle
* F(clock frequency): __cycles / a second

=> T * F = 1

# 2.2.1 CPU

## how to execute a source file

1. second memory: compile process
    - .c -> (compiler) -> .obj -> (linker-libs) -> .exe
2. load on main memory
    - instruction memory | data memory
3. process the Instruction cycle between main memory <->  CPU

## Instruction Cycle

1. **Fetch** the addresses of instructions stored in instruction memory to ***Program Counter*** of CPU
2. **Decode** the instructions(machine code) by each processors and set the configuration of registers and ALU on ***Control Unit*** of CPU, 
3. **Execute** it on ***ALU***
4. **Store** it on GPR or data memory
    - ***registers***: faster than memory
        - General Purpose Register: data processing...
        - Special Purpose Register: for PC, IR, SP...

# 2.2.1 Memory

## Types

* short-term memory
    - **D**ynamic **R**andom **A**ccess **M**emory: in main memory
    - **S**tatic **R**andom **A**ccess **M**emory: in cache of CPU
* long-term memory
    - flash memory: in USB
    - Solid State Drive: replacing HDD 

## Hierarchy Architecture

### CPU (register > processor > cache) > main memory > HDD

-------------------------------------------------------------------------> price↓ speed↓ size↑<Br/>

* processor gives 8bit(1byte) address to memory and the memory gives back data by the address to the processor

# 2.3 computer performance improvement technology

Dual mode

* Kernel mode
* User mode

## Interrupt

### types

* S/W Interrupt (=Trap)
    - system call
    - exception
* H/W Interrupt
* Timer Interrupt

### the way

* Polling: in order(X)
* Interrupt: in order(O)
