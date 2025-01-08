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

____

6 Jan 2025

* Why is HTTPS a Stateless protocol.
each HTTP request is independent and doesn't rely on the previous request which simplifies the communication between the client and server. The server also doen't keep track of client's state as to if they are logged in or not or their selections.    
Since HTTP protocol itself if stateless, Applications can implement state management through methods like cookies or sessions, to remember user data across multiple requests.

* What is the S for and how is it more secure.
S is there to represent that HTTPS is secure version of HTTP which is happening through two things, Encryption through SSL/TLS to protect the data exchange and Authentication of the server as authentic through the browser using Digital certificates issued by a trusted Certificate Authorities

* What are sessions and cookies
A Session is created for the user to store data and that session id is sent from the server when a site is visited , the cookie restricted to 4 kb only contains the session id and the session data on the other hand is stored on the server side.    
The stored cookie is sent to the server with every HTTP request, which is read by the server to remember the previous actions and update or add items.    
This is useful for persistent state management (to stay logged in).
session cookies and persistent cookies.

Session id might expire after sometime, deleting the session data or through logout.
This way of not storing data on the browser makes it more secure than cookies. Allows more data storage 


* What is a web browser and what are web apps 
It is the interface to the internet which requests information from servers using URL's (Networking)
They translate the code of web pages (JS, CSS, HTML) using rendering engines into what can be seen and interacted with. 
Handles security through HTTPS. Handles cookes

Web app runs in a web browser and doesn't need to be installed, Their processes run on the server itself.
Platform independent, realtime updates, rely on cookies for user specific information


* Deployment modules - public, private, hybrid, community and other remaining?
Ownership, access and management of resources.
Distributed cloud - resources are distributed but centrally managed.
Multi Cloud - Multiple providers

* SaaS, PasS, IaaS and remaing?
Desktop as a service - providing virtual desktops
Function as a service - To run a code in response to triggers
Backend as a service - databse, authentication, storage, server side logic.
Container as a service - Container management 
Machine as a service  Physical hardware instead of virualized infrastructure
Testing as a service - Software testing




* SLA? What does the limit mean
Service level agreement between provider and customer
What are the standards for cloud services in different providers, how will be in shifting from one service provider to another.
The limit is the maximum values or boundaries set for certain service metrics.


* what is the difference between the high mid and low level languages and why are they called as such, is it about the language being interpreted and compiled?
How far (abstraction) or near it is to the actual instruction given to the machine. Very little abstraction between the source code and the machine code. no memory management. (Machine code, Assembly language). Have to know how the processes works to make the program.

Middle provides some hardware control, some memory management, portability and mostly compiled language. (C, C++)

High level are abstracted far from the underlying hardware, focus on logic more than the system architecture. Automatic memory management, ease.
(Python, Java, Ruby, Javascript, Swift)
No concern on how the computer executes the code



* Trap command in Linux - trap signal numbers or exit statements?

interrupts, exceptions


crontab - for managing the processes that has to happen during a certain time.
Used for batch execution?


