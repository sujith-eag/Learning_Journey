To solve a particular problem

### Components of an Application
Storage: Server, file formats etc
Computation: Indexing, searching
Presentation

### Platforms
Desktops
Mobile
Web-based
Embedded: Single function with limited scope


### Architecture of Systems
Client-Server
Distributed  Peer-to-peer

***Client-Server Model***
Has explicit server and explicit client differentiation with network connecting both.
It can be *local system* or *a Machine client* with no user interaction
Principle is, There is a server for storage and computation, The client is to make requests and process the final data that comes back for the user interaction.

Variants of Client-Server Model
Multiple servers, Single queue, multiple queues, load balancing front ends


***Distributed***
Data can flow both ways, with no client or server explicitly
All peers are considered "equivalent"
Error tolerance
	Masters / Introducers
	Election / re-selection of masters on failure
Shared information

Ex Bittorrent, Blockchain based systems, IPFS




# Software Architecture Patterns
`MVC  MVA  MVP  HMVC  MVVM`

#### Design pattern
A general, reusable solution to a commonly occurring problem with software design.
Observing "patterns" in software code
Reusing these patterns can make design and development faster
Guide the design and thought process


## M-V-C paradigm
***Model:***
	Core data to be stored for the application
	Databases; Indexing for easy searching, manipulation
***View:***
	User-facing side of application
	Interfaces for finding information, manipulating
***Controller:***
	"Business logic" - how to manipulate data


User
Uses **Controller**
to manipulate **Model**
that updates **View**
that user sees


In an email
Model: Storing emails on servers, index, ready to manipulate
View: Display the list of emails, read individual emails
Controller: Sort emails, delete, archive