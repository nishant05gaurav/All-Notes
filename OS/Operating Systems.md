#  Operating System
- An operating system (OS) is a program that manages the computer hardware 
  - eg: Windows, Linux, Ubuntu, MacOSX, iOS, Android
- It also provides a basis for Application Programs and acts as an intermediate blw users and computer hardware
  ![alt text](https://imgur.com/4M3eI6y.png)

## Types of Operating System
### Batch OS
- Users used to prepare `jobs` (**program + input data + control instruction**) and provide it to an operator which is used to collect similar jobs and give to input devices and similarly collect output in form of cards
- OS was very simple and always present in memory.
- Its major task was to transfer control from one job to another
- **Disadvantage**
  - small memory, wastage of time , CPU remains ideal most of the time, lack of interaction with user
  
### Multi-Programming
- OS related concept
- One CPU and processor, only one process at a time but keep on switching (instead of sitting ideal)
- OS loads multiple programs to RAM then RAM to CPU
- CPU executes 1 work at a time, and switche so fastly when the previous program wants some kind of I/O operation
- Parallel execution not take place, since only switches of programs take place
- **Goals**
  - Maximise CPU utilisation

### Multi-Tasking
- OS related concept
- **Objective**: Improve responsiveness and performance of system by allowing the user to interact with multiple applications at the same time
- It is basically **multi-programming + time-sharing**
- CPU switches b/w multiple task/process, giving impression that all tasks are happening concurrently on single machine. It feels like everything is acting simultaneously
> Preemptive Programing: In modern OS, OS interrupt any task before it actually finished its time since if a high-priority tasks needs CPU time

### Multi-Processing
- **Objective**: Increase processing power and speed of system by dividing workload
- Support multi-process and thread
- It contains more than one CPU
- Multiple processes is executing in multi-processors 
- Hardware related concept

### Real-Time OS
- Response time is very very small, as well as time interval required for process is very less
- Used where rigid time is required, can also be used as control device in dedicated application. It has fixed (defined) time constraint else it will fail
- It is of two types:
  - Hard Real Time OS:
    - It guarantee that the critical task complete on time
    - Secondary storage is limited/ missing; data stored in ROM 
  - Soft Real Time OS:
    - lesser restrictive
    - Critical task is given priority and executed first
    - Limited utility
    - eg: multimedia, virtual reality, etc

![alt text](https://imgur.com/6whgQUT.png)
### Distributed OS v/s Network OS
  - Both facilitates resource sharing and communication in network environments but the difference lie in their scope, transparency, and focus
  - Distributed OS extend their functionality across multiple machines to provide a unified computing environment
  - Network OS primarily focus on providing network services within a local network environment

## Functions of OS
- It is an interface b/w user and hardware
- Allocation of Resources
- Managment of Memory, Security, File, Device, etc
- Controls System performance
- Error detection aids
- Coordination b/w other software and users

## Goals of OS 
- Convenience 
- Efficiency
---

## Basics of OS
- A moder general-purpose computer system consists of one or more CPUs and a number of devices controller connected through a common bus that provide access to shared memory
  ![alt text](https://imgur.com/eH2A8l8.png)
- Each device controller is in charge of a specific type of device
- CPU and device controllers execute concurrently, completing for memory cycle
- To ensure orderly access to the shared memory, a memory controller is provide whose function is to synchronize access to the memory

## Boot-Strap Program 
![alt text](https://imgur.com/iLGT1TT.png)
- As the computer system powered up, a test called `POST` (Power On Self Test) 
- POST basically test's is everything is working and connecting to the computer, in a specific amount of time
- In that time, consequently a piece of code initially runs that is store in ROM/ EEPROM, called `BIOS` (Basic Input Output System)
- And that initial program is called Boot-Strap Program
- This piece of code basically loads the Kernel into the memory of the computer system 
- Bootstrap program is also called `FirmWare` 

## Interrupt
- The occurence of an event is usually signalled by an *Interrupt* from hardware to software
- Hardware may trigger an interrupt at any time by sending a signal to the CPU, usually by the way of system bus

## System Call
- Software may trigger an interrupt by executing a special operation called system call
- When the CPU is interrupted, it stops what it is doing and immediately transfers execution to a fixed location
- `Fixed Location`: Usually contains the starting address where the Service Routine of Interrupt is located 
- The interrupt service routine executes
- On completion, CPU remains the interrupted computation

## I/O Structure
![alt text](https://imgur.com/UEQw6rR.png)
- Storage is only of many types of I/O devices within a computer
- A large portion of OS Code is dedicated to managing I/O, both b/c of its importance to the relliability and performance of a system and b/c of the varying nature of the device
- Computer System = CPU + Device Driver
  - Device Drivers maintains: 
    - Local Buffer Storage
    - Set of special purpose resistance

## Working of an I/O Structure
![alt text](https://imgur.com/TSgkMh0.png)
- To start an I/O operation, the device driver loads the appropriate registers within the device controller
- Device controller examines the content of registers and starts the transfer of data from the device to its local buffer
- Once the data gets transfered fully, controller informs the device driver via an interrupt. After that device driver returns control to OS
- This form of interrupt-driven I/O is fine for moving small amounts of data but can produce high overhead when used for bulk data movement
- `DMA`(Direct Memory Allocation): use to solve this
- After setting up buffers, pointers and counter for the I/O device. The device controller transfers an entire block of data directlt to or from its own buffer storage to memory with no intervention by the CPU
  - Here, only one interrupt is generated
  - availability of CPU is there, while the device controller is performing operations

## Computer System Architectur
### Types of computer system based on number of prossesor:
- **Single Processor System**
  - One main CPU is capable of executing a general purpose instruction set including instrutions from user processes
  - Other special purpose processors are also present which perform device specific tasks
- **Multi Processor System**
  - It has two or more processors in close communication sharing the computer bus and sometimes clock, memory and peripheral devices
  - **Advantages**
    - Increased throughput// Rate at which a system can process or deliver a specific amount of work within a given time frame
    - Economy of scale
    - Increased reliability
  - **Types**
    - Symmetric Multi-processing
    - Asymmetric Multi-processing
        ![alt text](https://imgur.com/znpdT4Q.png)
- **Clustered System**
  - Gather multiple CPUs to accomplish computational work (as multi-processor system)
  - They are composed of two or more individual systems coupled together 
  - Provide high availability
  - Structured as:
    - *Asymmetrically*:
      -  One machine in hot-standy mode
      -  Others run application
    - *Symmetrically*: 
      - Two or more hosts run application
      - Monitors eachother

## Operating System Services
- Operating systems provide a set of services to both the users and the applications running on a computer system. These services are essential for managing hardware resources, facilitating communication between software and hardware components, and ensuring a secure and efficient computing environment.
-  Here are some common operating system services:
  ![alt text](https://imgur.com/Mgy0TuP.png)

## GUI v/s CLI
![alt text](https://imgur.com/wd0h5e3.png)

## **System Call** 
- System calls provide an interface to the services made available by an OS
- System call is the programatic way in which a computer program requests a service from the kernel of the operating system
- These calls are generally available as routine written in C and C++
- If you're programming is executing in Kernel Mode, somehow if the program gets crashed then the whole program gets crashed
  - User Mode: Safer
  - Kernel Mode: Privilaged
![alt text](https://imgur.com/mghbN4N.png)
- Acquire input Name:
  - ask to enter the name
  - select the input file/ pointing device
- Write prompt to Screen: Use of hardware for this we use system call
- If the file doesn't exist, you need to abort/ terminate your execution
- If the file exist, you also need to abort b/c you're trying to create a new file in which you are going to copy the context of source file to the destination file
- If the name of the output/destination file that you provided, if it a new file and you are not allowed to create a file that already exist. So, if you find that the file already exist, then you have to abort 
  - Use of **System Call**
- **Types of System Call**:
![alt text](https://imgur.com/sJQyYVy.png)

## System Programs
- System Programs provide a convenient environment for program development and execution
- Some of them are simply user interfaces to system call
- Others are considerably more complex:
  - **File Management**:
    - create, delete, copy, rename, print, dump
    - list and generally manipulate files and directories
  - **Status Information**:
    - Date, Time, Amount of available memory/ disk space, No. of users
    - Detailed performance, logging, debbuging, information, etc
  - **File Modification**:
    - several text editors may be available to create and modify the content of files stored on disk or other storage devices
    - There may also be special commands to search contents of files or perform transformation of the texts 
  - **Programming Language**:
    - Compliers, Assemblers, Debuggers, Interpreters
  - Program-loading and Execution:
    - Once a program is assembled or compiled, it must be loaded into memory to be executed
    - The system may provide:
      - Absolute Loaders
      - Relocatable Loaders
      - Linkage Editors 
      - Overlay Loaders
    - Debugging systems for either higher-level languages/ machine language are needed as well
  - **Communication**:
    - These programs provide the mechanism for:
      - Creating Virtual connection among processes, users and computer systems
      - Allowing users to send messages to one anothers screens
      - To browse webpages
      - To send electronic-mail messages 
      - To log in remotely or to transfer files from one member to another 

## Operating System Design and Implementation
- **Design Goal**: 
  - Problem:
    -  Defining goals and specifications
    -  Choice of Hardware
    -  Types of systems
 -  Beyond this highest design level, requirements may be much harder to specify:
    - **User Goals**:
       -  Convenient to use
       -  Easy to learn and use
       -  Reliable
       -  Safe & Fast
    - **System Goals**:
       -  Easy to design, implement, maintain and operate
       -  Flexible, reliable, error traces and efficient

## Mechanism & Policies:
- Mechanism determine how to do something
- Policies determine what will be done 
- One important principle is the separation of policy from mechanism
  ![alt text](https://imgur.com/MIJI5hZ.png)

## Advantage of Writing in High-Level Language
- code can be written faster
- more campact
- easier to understand and debug
- easier to port

## Structure of OS
![alt text](https://imgur.com/PKPpjKz.png)
## Virtual Machines
- The fundamental idea behind a virtual machine is to abstract the hardware of a single computer (CPU, Memory, Disk-Drivers, Network Interface Cards, and so forth) into several different execution environments, thereby creating the illusion that each separate execution environment is running its own private computer
  ![alt text](https://imgur.com/sTOQQf8.png)
- **Implementation**:
  - Virtual Machine Software - Runs in Kernel Mode
  - Virtual Machine itself - Runs in User Mode

## OS Generation & System Bot
- Design, code and implement on Os specificially for one machine one site
- Os is designed to run on on any bof a class of machines at a variety of site with a variety of peripheralconfiguration
- The system must then be configured or generated for each specific computer site, a process sometimes known as system generation (SYSGEN) is used for this

<!-- ![image](https://github.com/nishant05gaurav/Notes/assets/140972654/4b1d9243-8ee6-4bd9-a3de-f4fcaa1e11a8) -->
### Kinds of information determined by the **SYSGEN** Program:
- What CPU is used?
- how much memory is available?
- what devices are avialable?
- What os options are desired?

## System Boot
- The procedure of starting a computer by coding the kernel is known as `booting the system`
- On most id computer system, a small piece of code knowmn as bootstrap program or bootstrap loader ocates the kernel
- This program is in the form of ROM, b/c RAM is in an unknown state at system startup. 
- ROM is convenient because it needs no initialization and cannot be infected by a computer virus
- When the full bootstrap program has been cooded, it can traverse the file system to find the OS Kerne;, load it into the memory, and starts its execution. It is only at this point that the system is said to be `RUNNING`.
<!-- ![image](https://github.com/nishant05gaurav/Notes/assets/140972654/90295263-2626-4e52-9dee-2ec6bc8e8d04) -->

## Process Scheduling
- The **objective of multiprogramming** is to have some process running at all times, to maximize CPU utilization.
- The objective of **time sharing** is to switch the CPU among processes so frequently that the users can interact with each program while it is running.
- To meet these objectives, the process scheduler selects an available process (possibly from a set of several available processes) for program execution on the CPU.
  - For a single-processor system, there will never be more than one running process.
  - If there are more processes, the rest will have to wait until the CPU is free and can be rescheduled.

## Scheduling Queues
![alt text](https://imgur.com/SL2GOrf.png)
![alt text](https://imgur.com/Y4BTSC1.png)


## Context Switching
- Interrupts cause the operating system to change a CPU from its current task and to run a kernel routine.
- Such operations happen frequently on general-purpose systems.
- When an interrupt occurs, the system needs to save the current **context** of the process currently running on the CPU so that it can restore that context when its processing is done, essentially suspending the process and then resuming it.
- The context is represented in the ``PCB(Process Control Block)``.
- Switching the CPU to another process requires performing a state save of the current process and a state restore of a different process.
![image](https://github.com/nishant05gaurav/Notes/assets/140972654/b3221ad4-c42a-43c7-86a1-47ed243ec36b)
- Context-switch time is pure overhead because the system does no useful work while switching.
- Its speed varies from machine to machine, depending on the memory speed, the number of registers that must be copied, and the existence of special instructions (such as a single instruction to load or store all registers).
- Typical speeds are a few milliseconds.
  

### `Operations and Processes`      
#### `Process Creation`
- A process may create several new processes, via a create-process system call, during the course of execution.
- The newly created process is called a parent process, and the new process is called the child process.
![image](https://github.com/nishant05gaurav/Notes/assets/140972654/1d630025-93b9-437d-8648-2ec81f1cf285)

When a process creates a new process, two possibilities exist in terms of execution:
- The parent continues to execute concurrently with its children.
- The parent waits until some or all of its children have terminated.

There are also two possibilities in terms of the address space of the new process:
- The child process is a duplicate of the parent process (it has the same program and data as the parent).
- The child process has a new program loaded into it.
    
#### `Process Termination`
- A ``Process terminates`` when it finishes executing its final statement and asks the `OS` to delete it by using the ``exit()`` system call.
- At that point, the process may return a status value (typically an integer)
- To its parent process (via the ``wait()`` system call).
- All the resources of the process-including physical and virtual memory, open files, and I/O buffers- are de-allocated by the `OS`.

Termination can occur in other circumstances as well:
- A process can cause the termination of another process via an appropriate system call.
- Usually, such a system call can be invoked only by the parent of the process that is to be terminated.
- Otherwise, users could arbitrarily kill each other's jobs.

A parent may terminate the execution of one of its children for a variety of reasons, such as threats:
- The child has exceeded its usage of some of the resources that it has allocated **(To determine whether this has occurred, the parent must have a mechanism to inspect the state of its children )**.
- The task assigned to the child is no longer required.
- The parent is exiting, and the operating system does not allow a child to continue if its parent terminates. 

---
### ``Interprocess Communication``
- Processes executing concurrently in the OS may be either `independent processes` or `cooperating processes.`
- **``Independent processes:``** They cannot affect or be affected by the other processes executing in the system.
- **``Cooperating processes:``** They can affect or be affected by the other processes executing in the system.
- Any process that shares data with other processes is a cooperating process.

There are several reasons for providing an environment that allows process cooperation:
- **Information sharing**: Sharing the common information needed by each other.
- **Computation Speedup**: 
- **Modularity**:
- **Convenience**:
  
Cooperating processes require an interprocess communication **(IPC)** mechanism that will allow them to exchange data and information.

There are two fundamental models of interprocess communication: 
- ` Shared Memory:`
  - In the shared-memory model, a region of memory that is shared by cooperating processes is established.
  - Processes can then exchange information by reading and writing data to the shared region.
- `Message Passing:`
  - In the message-passing model, communication takes place by means of messages exchanged between the cooperating processes.
  
![image](https://github.com/nishant05gaurav/Notes/assets/140972654/8d1a0be0-c175-46b4-bcee-2881c0e20805)


### `Shared Memory Systems`:
* Interprocess communication using shared memory requires a communicating process to establish a region of shared memory.
* Typically, a shared-memory region resides in the address space of the process creating the shared-memory segment.
* Other processes that wish to communicate using this shared-memory segment must attach it to their address space.
* Normally, the operating system tries to prevent one process's memory.
* Shared memory requires that two or more processes agree to remove this restriction.

#### `Producer-Consumer Problem`:
- A producer process produces information that is consumed by a consumer process.

For example, a compiler may produce assembly code, which is consumed by an assembler. The assembler, in turn, may produce object modules, which are consumed by the loader.

- One solution to the producer-consumer problem uses shared memory.
- To allow producer and consumer processes to run concurrently, we must have available a `buffer of items` that can be filled by the producer and emptied by the consumer.
- This buffer will reside in a region of memory that is shared by the `producer` and `consumer` processes.
- A producer can produce one item while the consumer is consuming another item.
- The producer and consumer must be synchronized so that the consumer does not try to consume an item that has not yet been produced.

![image](https://github.com/nishant05gaurav/Notes/assets/140972654/013a3f18-821d-4d5d-9eca-909adb15a284)


### `Message-Passing Systems`
- Message passing provides a mechanism to allow processes to communicate and synchronize their actions without sharing the same address space and is particularly useful in a distributed environment, where the communicating processes may reside on different computers connected by a network.
- A message-passing facility provides at least two operations:
  - `send(message)`
  - `recieve(message)`
- Messages sent by a process can be either `fixed` or `variable size`.
  ```
  Fixed Size:
  The system-level implementation is straightforward. But makes the task of programming more difficult.

  Variable Size:
  Requires a more complex system-level implementation. But the programming task becomes simpler.
  ```
- If processes `P` and `Q` want to communicate they must send messages to and receive messages from each other.
  - A communication link must exist between them.
  - This link can be implemented in a variety of ways. There are several methods for logically implementing a link and the `send()`/`receive()` operations, like:
    - `Direct or Indirect communication.`
    - `Synchronous or asynchronous communication.`
    - `Automatic or explicit buffering.`
  - There are several issues related to features like:
    - `Naming.`
    - `Synchronization.`
    - `Buffering.`

#### ``Naming:``
- Processes that want to communicate must have a way to refer to each other.
- They can use either `direct` or `indirect` communication.
  
##### Under direct communication-
- Each process that wants to communicate must explicitly name the recipient or sender of the communication.
  - `send(P, message)` - Send a message to process P.
  - `receive(Q, message)` - Recieve a message from process Q.

#### A communication link in this scheme has the following properties:
- A link is established automatically between every pair of processes that want to communicate. The processes need to know only each other's identity to communicate.
- A link is associated with exactly two processes.
- Between each pair of processes, there exists exactly one link.

>  This scheme exhibits Symmetry in addressing that is, both the sender process and the receiver process must name the other to communicate.
  

#### Another variant of Direct Communication:-
- Here, only the sender names the recipient; the recipient is not required to name the sender.
  - `send (P, message)`  - Send a message to process P.
  - `receive (id, message)` - Recieve a message from any process; the variable id is set to the name of the process with which communication has taken place.

  >  This scheme employs asymmetry in addressing.

- The `disadvantage` in both of these schemes ``(symmetric and asymmetric)`` is  the `limited modularity` of the resulting process definitions.
- Changing the identifier of a process may necessitate examining all other process definitions.

#### `With indirect communication:`
The messages are sent to and received from mailboxes, or ports.
  - A mailbox can be viewed  abstractly as an object into which messages can be placed by processes and from which messages can be removed.
  - Each mailbox has a unique identification.
  - Two processes can communicate only if the processes have a shared mailbox.
    - `send(A, message)` - Send a message to mailbox `A`.
    - `receive(A, message)` - Recieve a message from mailbox `A`.
  - A communication link in this scheme has the following properties:
    - A link is established between a pair of processes only if both members of the pair have a shared mailbox.
    - A link may be associated with more than two processes.
    - Between each pair of communicating processes, there may be a number of  different links, with each link corresponding to one mailbox.
  
![image](https://github.com/nishant05gaurav/Notes/assets/140972654/2a86f56f-3ee6-430c-aee8-99c625311acc)

Process `P1` sends a message to `A`, while both `P2` and `P3` execute a `receive()` from `A`.

### Which process will receive the message sent by `P1`?
The answer depends on which of the following methods we choose:
- Allow a link to be associated with two processes at most.
- Allow at most one process at a time to execute a `receive()` operation.
- Allow the system to select arbitrarily which process will receive the message (that is, either P2 or P3, but not both, will receive the message). The system also may define an algorithm for selecting which process will receive the message (that is, round robin where processes take turns receiving messages). The system may identify  the receiver to the sender.

A `mailbox` may be owned either by a process or by the `operating system`.

### `Synchronization:`
- Communication between processes takes place thrpugh calls to `send()` and `recieve()` primitives. There are different design options for implementing each primitive.
- Message passing may be either `blocking ` or `nonblocking`- also known as `synchronous` and `asynchronous`.

#### `Block Send:` 
The sending process is blocked until the message is received by the receiving process or by the mailbox.

#### `Nonblocking send:`
The sending process sends the message and resumes operation.

#### `Blocking receive:`
The receiver blocks until a message is available.

#### `Nonblocking receive:`
The receiver retrieves either a valid message or a null.

### `Buffering:`
Whether communication is `direct ` or `indirect,` messages exchanged by communicating processes reside in a temporary queue.
Such queues can be implemented in three ways:
- `Zero Capacity:` The queue has a maximum length of `zero`; thus, the link cannot have any messages waiting in it. In this case, the sender must block until the recipient receives the message.
- `Bounded Capacity:` The queue has finite `length n`; thus, at most n messages can reside in it. If the queue is not full when a new message is sent, the message is placed in the queue and the sender can continue execution without waiting. The link capacity is finite, however. If the link is full, the sender must block until space is available in the queue.
- `Unbounded capacity:` The queue `length` is `potentially infinite;` thus, any number of messages can wait in it. The sender never blocks.


### `Sockets`
Used for communication in  Clinet-Server Systems. 
- A socket is defined as an endpoint for communication.
- A pair of processes communicating over a network employ a pair of sockets- one for each process.
- A socket is identified by an IP address concatenated with a port number.
- The server waits for incoming client requests by listening to a specified port. Once a request is received, the server accepts a connection from the client socket to complete the connection.
- Servers implementing specific services (such as talent, `FTP`, and `HTTP`) listen to well-known ports(a talent server listens to port 23, an FTP server listens to port 21, and a web, or `HTTP`, server listens to port 80).
- All ports below `1024` are considered well-known; we can use them to implement standard services.

![image](https://github.com/nishant05gaurav/Notes/assets/140972654/5d3ea30b-4a2c-43b6-ade1-93549478813a)


### `Remote Procedure Calls (RPC)`
Remote Procedure Call (RPC) is a protocol that one program can use to request a service from a program located in another computer on a network without having to understand the network's details.
- It is similar in many respects to the IPC mechanism.
- However,  because we are dealing with an environment in which the processes are executing on separate systems, we must use a message-based communication scheme to provide remote service.
- In contrast to the IPC facility, the messages exchanged in RPC communication are well structured and are thus no longer just packets of data.
- Each message is addressed to an RPC daemon listening to a port on the remote system, and each contains an identifier of the function to execute and the parameters to pass to that function.
- The function is then executed as requested, and any output is sent back to the requester in a separate, message.

#### The semantics of RPCs allow a client to invoke a procedure on a remote host as it would invoke a procedure locally:
- The Rpc system has the details that allow communication to take place by providing a stub on the client side,
- Typically, a separate stub exists for each separate remote procedure.
- When the client invokes a remote procedure, the RPC system calls the appropriate stub, passing it the parameters provided to the remote procedure. This stub locates the port on the server and marshals the parameters.
- Parameter marshaling involves packaging the parameters into a form that can be transmitted over a network.
- The stub then transmits a message to the server using message passing.
- A similar stub on the server side receives this message and invokes the procedure on the server.
- If necessary, return values are passed back to the client using the same technique.

![image](https://github.com/nishant05gaurav/Notes/assets/140972654/65e2fc88-d460-4d0f-ae1f-d992dd023721)

### `Execution of a remote procedure call (RPC):`

**TO BE**


### Threads:

> A thread is a basic unit of CPU utilization.

- Thread comprises of:
  - A thread ID
  - A program counter
  - A register set
  - A stack

- It shares with other threads belonging to the same process its code section, data section, and other operating-system resources, such as open files and signals.
- A traditional/heavyweight process has a `single thread` of control.
- If a process has `multiple threads` of control, it can perform `more than one task at a time`.
     
![image](https://github.com/nishant05gaurav/Notes/assets/140972654/9c9358e3-6c2f-43d7-a3d0-d1718af45d44)


### `Benefits`
- The benefits of multithreaded programming can be broken down into four major categories:
  - `Responsiveness`
    - Multithreading an interactive application may allow a program to continue running even if part of it is blocked or is performing a lengthy operation,thereby increasing responsiveness to the user.
  - `Resource Sharing`
    -  By default, threads share the memory and the resources of the process to which they belong. 
    -  The benefit of sharing code and data is that it allows an application to have several different threads of activity within the same address space.
  - `Economy`
    - Allocating memory and resources for process creation is costly.
    - Because threads share resources of the process to which they belong, it is more economical to create and context-switch threads.
  - `Utilisation of multiprocessor architecture`:
    - The benefits of multithreading can be greatly increased in a multiprocessor architecture, where threads may be running in parallel on different processors.
    - A single-threaded process can only run on one CPU, no matter how many are available.
    - Multithreading on a multi-CPU machine increases concurrency.

### `Multithreading Models and Hyperthreading`:
- Types of threads:
  - `User Threads`- Supported above the kernel and are managed without kernel support.
  - `Kernel Threads`- Supported and managed directly by the operating system.

Ultimately, there must exist a relationship between user threads and kernel threads.
There are three common ways of establishing this relationship:
- Many-to-One-Model
- One-to-One Model
- Many-to-Many Model

![image](https://github.com/nishant05gaurav/Notes/assets/140972654/c1ae0bd2-7231-4ab8-8df9-b81a6a9b7e0d)
![image](https://github.com/nishant05gaurav/Notes/assets/140972654/fd3d0e62-8e92-466e-8854-714dfcb072c8)


#### `Hyperthreading  OR   Simultaneous Multithreading (SMT)`
- Hyperthreading systems allow their processor cares' resources to become multiple logical processors for performance.
- It enables the processor to execute `two threads,` or sets of instructions, at the same time.` Since hyper-threading allows two streams to be executed in parallel, it is almost like having two separate processors working together.

### The `fork()` and `exec()` System Calls:
- `fork(): ` The `fork()` system call is used to create a `separate, duplicate process`.
- `exec(): `When an `exec()` system call is invoked, the program specified in the parameter to exec() will `replace the entire process` - including all threads.

### `Threading Issues:`
```
 The semantics of the `fork()` and `exec()` system calls change in a multithreaded program.
```
- **`Issues`:** If one thread in a program calls `fork()`, does the new process duplicate all threads, or is the new process single-threaded?
- **`Solution`:** Some UNIX systems have chosen to have two versions of `fork()`, one that duplicates all threads and another that duplicates only the thread that invoked the `fork()` system calls.

```
Which version of fork() to use and when?

If a thread invokes the exec() system call, the program specified in the parameter exec() will replace the entire process -including all threads.
```

### Which of the two versions of `fork()` to use depends on the application:
#### If the `exec()` is called immediately after forking: 
- Then duplicating all threads is unnecessary, as the program specified in the parameters to `exec()` will replace the process.
- In this instance, duplicating only the calling thread is appropriate.
#### If the separate process does not call exec() after forking:
- Then the separate process should duplicate all threads.
  - If the multiple threads are concurrently searched through a database and one thread returns the result, the remaining threads might be canceled.
  - When a user presses a button on a web browser that stops a web page from loading any further, all threads loading the page are canceled.
- A thread that is to be canceled is often referred to as the target thread.

#### Cancellation of a target thread may occur in two different scenarios:
- **`Asynchronous cancellation`**: One thread immediately terminates the target thread.
- **`Deferred cancellation`**: The target thread periodically checks whether it should terminate, allowing it an opportunity to terminate itself ordinarily.

#### Cancellation of a target thread may occur in two different scenarios:
- **`Asynchronous cancellation`**: One thread immediately terminates the target thread.
- **`Deferred cancellation`**: The target thread periodically checks whether it should terminate, allowing it an opportunity to terminates itself in an ordinary fashion.

#### Where the difficulty with cancellation lies:
- **In situations where:**
  - Resources have been allocated to a canceled thread.
  - A thread is cancelled while iin the midst of updating data it is sharing with other threads.
- Often, the OS will reclaim system resources from a canceled thread but will not reclaim all resources.
- Therefore, caceling a thread asynchronously may not free a necessary system-wide rsource. 

#### **With Deferred cancellation**:
- One thread indicates that a target thread is to be canceled.
- But cancellation occurs only after the target thread has checked a flag to determine if it should be canceled or not.
- This allows a thread to check whether it should be canceled at a point when it can be canceled safely.

### **CPU SCheduling**:

- CPU scheduling is the basis of multiprogrammed operating systems.
- By switching the CPU among processes, the operating sysytem can make the computer more productive.
-  In a single-processes system, only one process can run at a time.
- Any others must wait until the CPU is free and can be rescheduled.
- The objective of multiprogramming is to have some process running at all times, to maximize CPU utilization.
- A process is executed until it must wait, typically for the completion of some I/O request.
- In a simpler computer system, the CPU then justsitd idle. All this waiting time is wasted; no useful work is accomplished.
- With multiprogramming, we try to use this system takes the CPU away from that process and gives the CPu to another and this pattern continues.

### **CPU and I/O Burst Cycles**:
 ![Alt text](https://imgur.com/rqBuFtg.png)

 Evetually, the final CPU burst ends with a system request to terminate execution.

 ![Alt text](https://imgur.com/VwRzBvd.png)

 ### **Preemptive and Non-Preemptive Scheduling**:

 - **CPU Scheduler**:
   - Whenever the CPU becomes idle, the operating system must select one of the processes in the ready queue to be executed. The selection process is carried out by the short-term scheduler (or CPu scheduler ). THe scheduler selects a process from the processes in memory that are ready to execute and allocates the CPU to the that process.
- **Dispatcher**:
  - The dispatcher is the model that gives control of the CPu to the process selected by the short-term scheduler.
  - The time it takes for the dispatcher to stop one process and start another running is known as the dispatch latency.
-  CPU-scheduling decisions may take place under the following four circumstances:
 - Whwn a process switches from the running state to the waiting state.
 - When a process switches from the running state to the ready state (for example, when an interrupt occurs.)
 - When a process switches from the waiting state to the ready state (for example, at completion of I/O).  
 - When a process terminates.
  
  For situations 1 and 4, there is no choice in terms of scheduling. A new process (if one exists in the ready queue) must be selected for execution. However, there is a choice for situations 2 and 3.

  When scheduling takes place only under circumstances 1 and 4, we say that the scheduling is nonpreemptive or cooperative; optherwise, it is preemptive.

### **Scheduling Criteria**

![Alt text](https://imgur.com/uWxKjvE.png)

#### ***``CPU Utilization``***:
We want to keep the CPU as busy as possible. Concepttuslly, CPU utilization can range from 0 to 100 percent. In a real system, it should range from 40 percent (for a lightly loaded system) to 90 percent (for a heavily used system).

#### ***``Throughput``***
If the CPU is busy executing process, then work is being done. One measure of work is the number of processes that are copleted per time unit, called throughput.

#### ***``Turnaround time``***
From the point of view of a pr\articular process, the important criterion is how long it takes to execute that process. The interval from the time of submission of a process to the time of completion is the turnaround time. Turaround time is the sum of the periods spent waiting to get into memory, waiting in the ready queue, executing on the CPU, and doing I/O.

#### ***``Waiting Queue``***:
The CPU scheduling algorithm does not affect the amount of time during which a process executes or does I/O; it affects only the amount of time that a process spends waiting in the ready queue. Waiting time is the sum of the periods spent waiting in the ready queue.

#### ***``Response Time``***:
In an interactive system, turnaround time may not be the best criterion. Often, a process can produce some output fairly early and can continue computing new results while previous resultts are being output t the user. Thus, another measure is the time from the submission of a request until the first response is produces. This measure, called response time, is the it takes to start  responding, not the time it takes to output the response. The turnaround time is generally limited by the speed of the output device.

### **Scheduling Algorithms**:
 
#### (First-Come,First-Served Scheduling)
- By far the simplest CPU-schedulnig algorithm.
- The process that requests the CPU first is allocated the CPU first.
- The implementation of the FCFS policy is easily managed with a ``FIFO queue``.
  ![Alt text](https://imgur.com/4296fsm.png)
- Whwn a process enters the ready queue, its PCB is linked onyo the tail of the queue.
- When the CPU is free, it is allocated t o the process at the head of the queue.
- The running process is then removed from the queue.
- This reduction is substanial. Thus, the average waiting time under an FCFS policy is generally not minimal and may vary substantially if the processes CPU burst times vary greatly.
- The FCFS scheduling algorithm is ``non-preemptive``.
- Once the CPU has been allocated to a process, that process keeps the CPU until it releases the CPU, either by terminating or by requestinhg I/O.
- The FCFS algorithm is thus particularly troublesome for time-sharing systems, where it is important that each user get a share of the CPU at regular intervals.
- It would be disastrous to allow one process to keep the CPU for an extende period.

### Convey Effect:
If processes with higher burst time arrived before the process es with smaller burst time, then, smaller processes have to wait for a long time for a long time for longer processes to release the CPu.
![Alt text](https://imgur.com/nvhFnJv.png)
![Alt text](https://imgur.com/dspklpP.png)
![Alt text](https://imgur.com/uK4NaTG.png)
![Alt text](https://imgur.com/g1vWTDp.png)
![Alt text](https://imgur.com/5FYjJeO.png)

### ``Shortest-Job-First-Scheduling``:
- This algorithm associates witch each process the length of the processes next CPU burst.
- When the CPU is available, it is assigned to the process that has the smallest next CPU burst.
- If the next CPU bursts of two processes are the same, FCFS scheduling is used to break the tie.
  

``SJF algorithm can be either preemptive or non-preemptive.``

- A more appropriate  term for the   scheduling method would be  the `Shortest-Next-CPU-Burst Algorithm` because scheduling depends on the length of the next CPU burst of a process, rather than its total length.

![Alt text](https://imgur.com/sGQ4lzn.png)

![Alt text](https://imgur.com/CPKaRwV.png)

### Problems With SJF Scheduling:
- The real difficulty with the SJF algorithm is knowing the length of the next CPU request.
- Although the SJF algorithm is optimal, it cannot be implemented at the level of short-term CPU scheduling.
- There is no way to know the length of the next CPU burst.

### One Approach is:
- To try approximate SJF scheduling.
- We may not know the length of the next CPU burst, but we may be able to predict its value,
- We expect that the next CPU burst will be similar in length to the previous one.
- Thus, by computing an approximation of the length of the next CPU burst, we can pick the process with the shortest predicted cpu burst.

![Alt text](https://imgur.com/S71bmYS.png)
![Alt text](https://imgur.com/CaTmf8V.png)
![Alt text](https://imgur.com/3cLKeoL.png)
![Alt text](https://imgur.com/xmzBBfT.png)

### `Priority Scheduling`:
- A priority is associated with each process, and the CPU is allocated to the process with the highest priority.
- Equal-priority processes are scheduled iin FCFS order.
- An SJF algorithm is simply a priority algorithm where the priority is the inverse of the (predicted) next CPU burst.
- The larger the CPU burst, the lower the priority, and vice versa.

``Priority scheduling can be either preemptive or non-preemptive``
- A ``preemptive`` priority scheduling algorithm will preempy the CPU if the priority of the newly arrived process is higher than the priority of the currently running process.
- A ``nonpreemptive priority`` scheduling algorithm will simply put the new process at the head of the ready queue.

![Alt text](https://imgur.com/lRmn6NU.png)

### `Problem with Priority Scheduling` :
- A moajor problem with priority scheduling algorithm is indefinite blocking, oe starvation.
- A process that is ready to run but waiting for thr CPU can be considered blocked.
- A priority scheduling algorithm can leave some low priority processes waiting indefinitely.
- In a heavily loaded computer system,a steady stream of higher-priority processes can prevent a low
```
Important interview Questions
1. Difference b/w multi-programming, multi-tasking, and multi-processing OS.
2. Where does the bootstrap program resides?
3. About System Call.
```

---
Important Intrview Questions:
1. What is the role of process management in an Operating System?
2. 
