***What is an operating system?*** 
A computer’s OS is a collection of programs that, as a whole, support our use of the computer through managing hardware resources and running processes. 
Operating systems usually comprise many different programs. The heart of the OS is a single program called the kernel. The kernel is loaded into memory when a computer is booted, and it remains resident in memory until the computer is shut down. 

The kernel’s role is to handle process and resource management, among other tasks. The kernel calls upon other OS components to accomplish some of its tasks. Some of these components are loaded and run as needed.

Users may also call upon some of these other OS components, again loaded and run as needed.


***The Operating System Kernel***
Kernel is responsible for the most of the important tasks of the OS.

There are three different types of kernel: **monolithic**, **microkernel** and **hybrid**. 

***A monolithic kernel*** is one in which the kernel is a single program which operates solely within the computer’s privileged mode and in its own address (memory) space. 
Communication between the user side (running applications) and the kernel side is handled through system calls. 
A system call invokes a specific portion of the OS kernel. Upon receiving a system call, the kernel changes from user mode to privileged mode. 
The kernel then ensures that the user program’s request is legitimate, meaning that the user program (or user) has an appropriate level of access for the call to be carried out.

Early operating systems used a monolithic kernel. But, as these operating systems governed computers with limited amounts of memory and few system resources, the kernel was not asked to do a great deal and so the kernel was fairly small (in comparison to later OS kernels). As computer capabilities grew, operating systems became larger and monolithic kernels became more and more complex.

In Microlithic kernel, communication is similar to monolithic but the smaller kernel calls on the various servers to handle the many operations.
microkernel is smaller and simpler, but system calls occur between the kernel and servers as well as between the application software and servers.

Among the server components are file system servers, network servers, display servers, user interface servers and servers that can directly communicate with device drivers. Remaining in the kernel are the process scheduler, memory manager (including virtual memory) and interprocess
communication between OS components


The hybrid kernel compromises between the two extremes where the kernel is kept small but server-like components are added on. Here, the server components run in kernel mode but often in the user’s address space. In this way, processes can call upon the servers more easily than with the microkernel approach and bypass some time consuming system calls.


Monolithic kernals are broken into modules of kernel which are loaded as needed and this way linux can be kept small based on the modules loaded.


Linux is a monolithic kernel supported by modules that can be loaded and unloaded.
In Linux, a system call is not directly intercepted by the kernel but instead handled by a wrapper function which place the arguments of the function call into appropriate hardware registers where the kernel expects them to switch processor mode from user mode to privileged mode.

Linux is portable OS which means it is not written for any particular hardware but to be run in many different platforms



___

***Roles of OS Kernel***

Role : Meaning : Example

Auditing and Accounting
Keep track of users logged in and the resources allocated to them: log the events.
Auditing and logging programs.

Device management
Ability to add, remove and interface with peripheral devices.
Mounting disk drives, adding devices via USB port.

File Management
Ability to open, close, create, save, rename and copy files and directories.

Interprocess communication
Info sharing between the running processes.

Interrupt handling
dealing with device interrupt and running situations.
Timer interrupt, I/O interrupt, interprocess interrupt

Memory management
Manage memory allocation and deallocation; Protect areas of memory from memory vilolation; move code and data into and out of memory as needed.

ex: Virtual memory (demand paging, demand segmentation), contiguous memory allocation and compaction, memory overlay.


Process management
Start new process; monitor process as they run to initiate the handling of requests; detect and initiate the process of handling of errors; switch between process; remove process from the computer when they terminate.
ex: single tasking, batch processing, cooperative multitasking, pre-emptive multitasking, multithreading.

Protection
Ensure a process can only access the memory available to that process or to that process owner.
ex: user account and login process, user mode versus privileged mode.

Resource management
Grant a process access to a resource, maintain mutually exclusive access; maintain process liveness.
ex: synchronization mechanism, deadlock handling mechanisms.

Scheduling
Determine the order with which process will run.
Priority round robin, first come first serve

Security
Extend protection across a computer network
encryption

User interface
Provide a means for the user to interface with the OS, running applications and hardware.
GUI, CLI, menu driven interface

____
