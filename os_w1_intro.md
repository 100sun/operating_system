# 1.1 Introduction to OS

## relationship

* user > sw > hw
* sw: application software > operating system
* OS ex. ios, android, windows

## role

* performance ↑
    - **resource management, allocation** 
        - SW management: manage process, file,,,
        - processor management: manage CPU
        - memory management: manage memory
        - file management: manage HDD
        - IO management: manage keyboard, monitor, printer
    - resource protection ex. prevent from monopolizing CPU
* convenience ↑
    - hw interface
    - user interface 
        - ex. GUI

# 1.2 Architecture of Computer

CPU scheduling (Processor management)
Memory management
Disk(HDD) scheduling
Interrupt
메모리에 여러 프로그램이 올라가면 cpu에서 읽어가서 실행 -> 1cpu이기에 매우 빠른 switching으로 illusion 제공

## 1.3 internal parts of computer

on motherboard<br/>
: register, 

## 1.4 external parts of computer

not on motherboard<br/>
I/O devices: monitor, keyboard, mouse

* kernel: resource manager in OS 

    전원 off 될때까지 메모리에서 계속 상주하는 부분 

* Shell = command interpreter

    : User 명령 받아서 해석하여 실행 

hdd 비휘발성에 보조기억장치
os에 -> memory dram 주기억장치 휘발성 전원이 꺼질때부터 겨질태
