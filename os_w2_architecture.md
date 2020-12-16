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
    - **S**tatic **R**andom **A**ccess **M**emory: in Cache of CPU
* long-term memory
    - flash memory: in USB
    - Solid State Drive: replacing HDD 

## Hierarchy

| CPU: register > processor > cache > main memory > HDD |
| --------------------------------------------------- |
| -------------------------------------------------------------------------> price↓ speed↓ size↑ |

* Processor: gives 8bit(1byte) **address** to memory and the memory gives back **data** by the address to the processor

## Why Protection is needed

now time-sharing system => can invade other program's memory: interrupt -> terminate it

## Booting Process

: load operating system to memory

* ROM's command to CPU
    1. POST: test
    2. CPU copies boot-strap-code from 0 sector in HDD to RAM
    3. CPU executes boot-strap-code by kernal of RAM which was copied from kernal in HDD by the process of OS 

# 2.3 computer performance improvement technology

## Dual mode when CPU works

CPU <-> Program(user+OS)

* Kernel mode by kernal process relevant to the OS (more authority)
    - mode_bit = 0
* User mode by user process
    - mode_bit = 1

## Hardware Mechanisum

### Polling

: in order(X) 

* CPU steadily checks whether the device needs attention

``` c
void main(void){
    while(1){
        if(button_pressed)
            do_something();
    }
}
```

### Interrupt

: in order(O)  

* the device notices the CPU that it requires its attention. Interrupt can take place at any time.

``` c
Interrupt_Service_Routine(BUTTON_PRESS_vect){
    do_something();
}

void main(void){
    setup_button_press_interrupt();
    while(1){
    }
}
```

* request 𝜇P to work instantly for the event 
* user mode -> kernal mode

#### Types

* **S/W Interrupt** via Kernal of OS
    - system call: the job when program1 requests OS to interrupt -> Program Count moves from program1 to ISR of OS
    - exception: by checking [what mode](##Dual-mode-when-CPU-works) of CPU now via mode_bit
* **H/W Interrupt** via 𝜇C
    - : the job when IO device requests OS to interrupt for program1 -> Program Count moves from the program1 to ISR
* **Timer Interrupt**: Time Sharing System by setting timer via time slice
