
Program is a static entity.
A process is a running program, it has a `state` which changes over time.
The programs are identical but the processes all differ because each will have its own unique state. 

A process is described in many ways,
Is it currently being run by the CPU or waiting?
if waiting, where?
What are the values of its variables? where in memory is it stored?
If in memory, what resources does it have assigned to it?
The answers to these questions are just some of the ways we describe a process.

Whenever a process runs, Linux kernel keeps track of it through process ID (PID).
The first process the kernel starts after it is loaded is `systemd`.
`systemd` is responsible for for starting the run-time environment and then monitering the environment.
`systemd` is given PID of 1, each new process gets the next available PID.

In Linux, a process can only be created by another process (except `systemd`).

Creating process is referred to as `parent` and created process is `child` where parent process spawns the child process.
Spawning of a process utilizes the system call of the parent process to the Linux kernel.

____


***Several forms of child process creation system calls.***
* `fork()`  Creates a duplicate process of the parent but with its own PID, own memory and its own resources. Parent and child an run concurrently.

* `vfork()` Same as `fork` except parent is temporarily suspended and child might be permitted to use the parent's memory space.

* `clone()` Like `fork` except there is more control over the child process produced with respect to what is duplicated and what is shared between parent and child.

* `exec()` take an existing process and replace its image (executable code) with new image.

* `wait()` Suspended parent process to wait for an event of a child process.

The current process (parent) invokes one of the system call function like `fork()` `clone()`. There are several different clone systems `clone() clone2() clone3()`
The difference between `clone fork vfork` is how much will be shared between the parent and the child.

`vfork()` suspends the parent process while the child runs.
Another option is to create a child with `clone or fork` and then have the parent `wait`

There are several wait systems,
with `wait()` the parent is suspended till one child terminates.
with `waitid()`  `waitpid()` the parent suspends until the child with the specified PID terminates.
These can be modified to make the parent resume under different circumstances also. This makes `wait()` more flexible than `vfork()`


`exec()` 
`fork, clone, vfork` create a child that has the same executable code as the parent.
(calling `wc` from `bash`, the child created by `fork` is still `bash`, here `exec` replaces the child code with `wc`)
`exec` replaces the parents code with the child with the image of the program the child should be. 

There are several versions of `exec()` known as `exec` family of system calls.
`execl()` `execle()` `execlp()` `execv()` `execve()` and `execvp()`.
The difference between them is the parameters passed to them.


It is common to pair up `fork()` and `exec()`

______


CPU stores information about the running process via its registers. These register values changes as the process executes.
The program counter (PC) stores the address of the next instruction to fetch from memory.
The Instruction register (IR) stores the current instruction.
status flag (SF) register
stack pointer (SP)

 The Operating system must keep track of the process's state and does so through a data structure  called the `process control block` (PCB).
 PCB collects the most important data about the running process.

***Process Control Block Information***

* Process State : Run-time state of the process; usually one of `new, ready, running, suspended, terminating, waiting`
* Process ID : Usually a numeric designer to differentiate the process from others.
* Other process data : Parent process, process owner, priority, scheduling information, accounting data such as CPU time elapsed.
* Process Location : Which queue the process resides in (ready, wait, job)
* Process privilege/state : What mode the process runs in (user, Privileged, some other)
* Hardware-stored values : PC, IR, SF, SP (possibly data register values) and interrupt masks.
* Resource allocation : I/O devices currently allocated to the process; memory in use; page table.

The operating system is also in charge of scheduling when process run, and of changing the process status as needed doing `process management`.


### Single process execution

OS starts a process and the CPU attention is entirely held by that one running process until it terminates or requests some operation from OS.

Batch processing, scheduling programs, process requests (jobs)

During batch processing era, different scheduling algorithms were developed.
Simplest and fairest is `first come first serve` `FCFS` or `First in first out` `FIFO`

Ordering jobs statistically from shortest to longest is known as `shortest-job first`
opposite would be `longest-job first`
A `priority` schedule may be used with `FIFO`.
A series of queues are used to order the process by priority


### Concurrent Processing

It is to switch from a waiting process to a process ready to execute leading to improved form of process management called `multiprogramming`.
CPU executes single process but if that process needs to perform time-consuming I/O then that process is set aside and another process is executed.

There will be atleast two queues, ready queue and wait queue. There might be multiple I/O wait queues. It is the OS job (scheduler) to choose which process the CPU should switch to.
This is `cocurrent processing`, multiprogramming is one of concurrent processing.

The changing of CPU from one process to another is called `context switch` where OS gets involved.
`coopeartive multitasking`, `rendezvous`

The next evolution of process management is to `force a context switch` so that no single process can monopolize the CPU.
A hardware called `timer` which counts cock cycles.
It is initialized to some value, gets decremented and when it reaches 0, the timer alerts the OS to perform a context switch.
The running process is moved to the `ready queue` and the CPU resumes the process next in line in the ready queue.

This becomes `preemptive multitasking` which is multitasking or previously known as `time sharing`

`round robin sheduling`  `time slice` `quanta` 

Setting 1000 * (process priority)
Priority 1 gets 1000 each time while priority 10 gets 10,000 each time to finish faster.

They can be made to age process to lessen the priority over time.

Threads?? New concepts 
`multithreading`

___

Linux by default uses cooperative and preemptive multitasking and multi-threading.
It can also perform batch processing on request using `batch` instruction.

___


### Interrupt Handling

CPU repeatedly fetches and runs program instructions (fetch-execute cycle) until it finishes executing the current process.
The timer reaching 0 is an example where some hardware component needs the CPU's attention, where it can interrupt the CPU's fetch-execute cycle and request the CPU focus its attention on hardware component to handle whatever situation arose.
Naturally, interrupting the CPU is called `interrupt`,
and process of requesting an interrupt is an `interrupt request` (IRQ)

`IRQ` might originate from hardware or software.
Hardware through reserved line on the bus to CPU
for software `IRQ` is submitted as an interrupt signal.

Upon receiving an interrupt request, the CPU finishes the current fetch-execute cycle.
CPU determines which device or software raised the interrupt.
CPU acknowledges the IRQ to the interrupting device.
To handle interrupt, CPU switches from `user porocess` to `operating system` which is privileged.

For every type of interrupt, the OS contains an interrupt handler.
It is a piece of code written to handle a specific type of interrupting situation.
CPU performs a `context switch` from current process to proper `interrpt handler`, 
requiring that CPU saves what it was doing with respect to the user process.

The interrupt handler executes and upon completion, the OS switches back to the process that had been running (or new process if the interrupt was from the timer reaching 0), also changing mode back to `user mode`.

IRQ's are prioritized, if the CPU is currently handling an IRQ and higher priority IRQ arrives, the CPU will postpone the lower IRQ for newer one.

___

In Linux, interrupt handlers are part of Kernel.
The information about the interrupt is recorded in `/proc/interrupts`

The file `/proc/stat` also contains interrupt information.











