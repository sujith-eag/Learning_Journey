(19 Dec 24)

Function of OS function
OS is a System software,

Software- is a collection of programs used to operate computers and perform specific task.

Types of software : Acts as a bridge between the hardware and the user applications.

Looking into the basic questions of Computer

> MIME, VLC, Stack vs Heap

Application software - has categories (productive, Web browsers, media players, games, design software)

The diagram of the Application software over System software and Basic hardware parts (DSP, Timers, DMA, I/o Peripherals, Memory)


____

(21 Dec 24)

Hardware (CPU, I/O devices, Memory) form the hardware. 
These provide the basic computing resources for the system.

Application programs such as word processors, spreadsheets, compilers, browsers define the ways in which these hardware resources are used to solve the user problems.

OS controls the hardware and co-ordinates these among the various application programs for the various users.

**System View**
OS is resource allocator,
Trap, interrupt, system call

> middleware 

> firmware

Self Introduction Beyond the basics

> Virtual box - two OS running simultaneously

**Virtualization** - Guest OS running on Host OS as virtual machines by sharing the CPU and RAM storage.
**Emulation** of hardware resources is done by the virtual layer between the hardware and the guest OS. 
Each OS runs in an isolated environment.
Utilizing various ***Privilege modes***, less than kernel, more than user.
The Guest OS runs in user mode where the virtualization layer intercepting the calls, ***translates*** it to Host OS compatible, to ensure it doesn't interfere with the host OS or hardware directly.

Virtual box is using the Host Os to run the hardware system calls so there is a overhead.


> Thin client system

Heavy reliant on centralized server for processing power, storage, and resources.
They are primarily an interface to access applications, data and services hosted on a server.
OS is a stripped down version which is optimized for accessing the remote server.
Server will be running virtual machines, remote applications.


> MIME implications

***Multipurpose Internet Mail Extensions*** is a standard that expands the format of email messages to include multimedia contents.
Uses `content-type` header to define the type of data being sent.
Allows the mails to be interpreted by mail clients. (inter-operability)



>  VLC, LINUX

VideoLan Client
Universal Serial Bus
Basic Input Output System
Wireless Fidility

>  Stack vs Heap examples

Can grow dynamically, Longer lasting data, 


> Virtual box for Fedora, Kali, Arch

> Nokia % , IOS, Android