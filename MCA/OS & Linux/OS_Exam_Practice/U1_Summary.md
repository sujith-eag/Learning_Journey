

The Operating System (OS) is the core software on a computer, often referred to as the **Kernel**, which manages hardware and system resources.

- User-friendly intermediary: The OS acts as a bridge between the user and the hardware, ensuring a seamless user experience.
- Resource allocator: Manages and allocates resources such as CPU, memory, I/O devices, and storage to processes and users.
- Control program: Ensures correct execution of user programs by preventing errors that may arise from conflicting resource requests.
- User Interface: for user to interact with the system 

#### Operating System Components

To deliver these services, the OS is composed of several integrated components:

- Kernel: The core of the OS, responsible for managing the low-levels operations of CPU, memory, devices, and system calls.

- Process Manager: Controls process lifecycle (creation, scheduling, termination) and manages inter-process communication.

- Memory Manager: Allocates memory (RAM) to active processes and ensures efficient memory use through techniques like paging or segmentation.

- File System Manager: Organizes data on storage media and controls access permissions and file operations.

- I/O System: Manages device drivers and I/O operations to ensure effective communication between hardware and software.

- Security and Protection Mechanisms: Control access to system resources, ensuring user and process isolation and  protects against unauthorized access.

---


#### OS System Services:

- Resource Allocation: Handles allocation of resources in a multi-user environment.
- Program Execution: Loads, manages, and terminates processes, ensuring proper execution.
- File system manipulation: Enables the creation, reading, writing, deletion, and management of files and directories, ensuring data integrity.
- Inter-Process Communication (IPC): Allows processes to communicate with each other through shared memory or message passing.
- I/O Operations: Facilitates interactions between processes and hardware devices, ensuring safe and efficient data transfer.
- Accounting: Tracks resource usage by processes and users for monitoring or billing.
- Protection: Prevents interference between processes, ensuring that each process runs in isolation.
- Security: Protects against external threats and unauthorized access to the system.
- Error Detection: Identifies errors in the system and initiates recovery mechanisms.

#### User Interface:

- CLI (Command-Line Interface): Allows users to interact with the system by typing textual commands (e.g., Linux terminal).

- GUI (Graphical User Interface): Provides a visual environment with windows, icons, menus and pointers (WIMP) (e.g., Windows, macOS).

- Batch Interface: Executes a sequence of commands in a script without user interaction.

- Hybrid Interface: Combines features from multiple interfaces to enhance flexibility and usability.


---

The OS's **system programs** and **application programs** define the user experience, offering tools for interaction, system management, and program execution.

#### System Program Categories:

Along with core OS services, system programs provide additional functionality to interact with system resources to improve user and developer experience:

- **File Management Tools**: Help users manage files and directories (`cp`, `mv`, `ls`, `mkdir`, etc.).

- **System Status Utilities**: Display real-time information about system performance (`top`, `ps`, `df`, `free`, `uptime`).

- **Programming Support Tools**: Include compilers, linkers, interpreters, and debuggers for software development.

- **Communication Programs**: Enable data exchange, remote login, file transfer, and email.

- **Background Services (Daemons)**: Perform tasks such as scheduling, printing, network monitoring, and error logging in the background.

---

#### System Calls

System calls act as the interface between the user space and the kernel space.

A **system call** is a programmatic way through which a user-level program requests a service from the **operating system’s kernel**. 

These services typically involve access to hardware resources or other operations that require privileged access, such as creating a process, accessing a file, or communicating with a device. Since user programs do not have direct access to critical hardware or protected parts of the system (for reasons of security, control, and abstraction).

___

- Interrupt: A signal from hardware (like a keyboard or timer) that notifies the OS that an event needs immediate attention. Interrupts are asynchronous and can occur at any time.

- Trap (or Exception): A software-generated interrupt, often caused by errors (e.g., division by zero) or intentional user program actions that require OS intervention. Traps are synchronous.

- System Call: A specific kind of trap intentionally invoked by a user program to request services from the OS (e.g., `fork()`, `read()`).


The OS is interrupt-driven, relying on traps and interrupts to manage events and ensure smooth functioning.

___

#### Common System Calls:

#### Types of System Calls

**Process Control** : Deals with the creation, execution, termination, and management of processes.
- `fork()` – Create a new process.
- `exit()` – Terminate a process.
- `wait()` – Wait for a child process to finish.
- `exec()` – Replace a process’s memory with a new program.

**File Management** : Handles operations on files and directories like creation, reading, writing, and deletion.
- `open()` – Open a file.
- `read()` – Read data from a file.
- `write()` – Write data to a file.
- `close()` – Close a file.
- `unlink()` – Delete a file.

**Device Management** : Manages input/output devices and their access.
- `read()`/`write()` – Perform I/O operations.
- `open()`/`close()` – Open or close a device (e.g., printer, disk).

**Memory Management** : Allocates and frees memory used by programs during their execution.
- `mmap()` – Map files or devices into memory.
- `munmap()` – Unmap memory.

**Communication (Inter-Process Communication - IPC)** : Enables processes to exchange data and signals.
- `pipe()` – Create a pipe for communication.
- `shmget()` – Create a shared memory segment.
- `send()`, `recv()` – Send or receive data over sockets.
- `signal()` – Send a signal to another process.

#### Application Programming Interfaces (APIs):

While system calls are how user programs interact with the OS, they are not usually called directly. Instead, developers use Application Programming Interfaces (APIs) provided by the OS or standard libraries (like C standard library) to indirectly access system calls.

- POSIX (Portable Operating System Interface) – A standard API for Unix-based systems.
- WinAPI – API for Windows systems.
- Java APIs – Abstract system calls in a platform-independent way.

> APIs provide a user-friendly abstraction and improve portability of applications across different systems.

___

#### Dual Mode: User (1) / Kernel Mode (0)

The OS operates in two distinct modes:

**User Mode** : is used when the user applications are running.
- Access to critical system resources is restricted (e.g., hardware, kernel memory).
- Certain privileged instructions are not allowed in user mode.
- Protects the system from accidental or intentional misuse by user-level programs.

**Kernel Mode** (Supervisor or Privileged Mode)
- Operating system runs in this mode and has full access to all system resources, including hardware and all instructions.
- Can execute privileged operations like memory management, device control, and process scheduling.


### Mode Bit:

A Mode bit is a special hardware-supported bit used to distinguishes the current mode of execution:
- 0 → Kernel Mode
- 1 → User Mode

The system switches between user mode and kernel mode during System Call, Interrupt or Exceptions (Trap).

Each of these transitions causes the CPU to switch to kernel mode, handle the request, and then return to user mode after completing the task.

---

##### Timer

A hardware timer prevents a process from monopolizing the CPU indefinitely. When the timer expires, it generates an interrupt, allowing the OS to regain control and possibly switch to another process.

- This is crucial for preemptive multitasking and system responsiveness.

---

### Traditional Computing

Traditional computing setups refer to systems where computing resources such as servers and workstations are located locally within an organization.

- PC: A single-user system focused on ease of use and performance, but with less emphasis on resource utilization.
- Mainframe: A multi-user system designed for resource maximization and efficient information sharing.
- Workstations: Connected to servers via networks, offering a balance of performance and resource utilization.
- Network Computers / Thin Clients: Focus on easy maintenance and security, with less local processing power.

#### Distributed Systems

A distributed system is a collection of independent computers that appear to users as a single system. These systems distribute workloads across multiple machines to enhance reliability, scalability, and performance.  
Examples: Cloud services, large-scale web applications.

#### Client-Server Computing

This model divides tasks between requesters (clients) and service providers (servers), with servers offering services, data, or resources to clients over a network.

#### Peer-to-Peer Computing

A decentralized network model where each node functions as both a client and a server, sharing resources directly with other nodes, without a central server.

#### Cloud Computing

Cloud computing delivers services over the internet, including storage, networking, databases, software applications, and processing power. Organizations rent computing resources from cloud service providers on-demand, rather than maintaining their own physical infrastructure.

Cloud Types:
- Public Cloud: Resources owned and managed by third-party providers (e.g., AWS, Azure, Google Cloud).
- Private Cloud: Cloud infrastructure used by a single organization, potentially hosted by a third-party provider.
- Hybrid Cloud: A combination of public and private clouds, allowing for data sharing between them.
- Community Cloud: Shared infrastructure used by several organizations with similar requirements.

Cloud Service Models:
- IaaS (Infrastructure as a Service): Provides virtualized computing resources like virtual machines, storage, and networks (e.g., Amazon EC2, Azure Virtual Machines).
- PaaS (Platform as a Service): Provides a platform for developers to build and deploy applications without managing the underlying infrastructure (e.g., Google App Engine, Azure App Services, Heroku).
- SaaS (Software as a Service): Delivers software applications over the internet on a subscription basis (e.g., Google Workspace, Salesforce).
- DBaaS (Database as a Service): Offers database hosting and management without requiring users to manage the infrastructure (e.g., Amazon RDS, Google Cloud SQL).

#### Embedded Systems

Embedded systems are specialized computing systems designed to perform specific tasks with strict requirements, often in real-time environments.

##### Real-Time Operating System (RTOS):

An OS designed to meet the timing constraints of real-time applications. These systems must process inputs and generate outputs within specified time limits to ensure reliability.  
**Examples**: Medical devices (e.g., MRI machines, pacemakers), automotive systems (e.g., ABS, flight controllers).

---

#### System Boot

Booting is the process of starting a computer system by loading the kernel into memory and initializing its execution. The process starts with a small piece of code called the bootstrap program or bootstrap loader, typically stored in ROM (firmware). This program locates and loads the OS kernel into the main memory.

For modern OS like Windows, macOS, or UNIX, the bootstrap loader is stored in firmware, while the OS itself resides on disk.

Boot Disk/System Disk: The disk containing the OS and the boot partition, which is necessary to start the system.

---
