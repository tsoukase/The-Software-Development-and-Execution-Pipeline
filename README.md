# The Software Development and Execution Pipeline

**Importand Note: this is an onging work. I am a doctor, not a CSist neither a SEer.**
> Computer science is mathematics with discrete and finite Data instead of infinite numbers.  

> Software engineering is computer science applied on hardware.

This project aims to present the Software Development phases as a piped process, from App conception to bare electrons.  
It consists of the classical Development Lifecycle phases (1-3) and the regular execution on hardware (4-5)

The five distinct phases/processes, with six IO-structures piping through each one, are:  

|PHage  | -process>      | Output        | Language     | Processor|  
|:---:  |:---:           |:---:          |:---:         |:---:     |
|0      | -              | [Application](#application)|-|-         |  
|[1](#1)| -requirements> | Specification  | natural      | human    |  
|[2](#2)| -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3)| -programming>  | SourceCode    | programming  | human    |
|[4](#4)| -translation>  | MachineCode   | intermediate | machine  |
|[5](#5)| -execution>    | Electr state  | VHDL         | machine  |

Almost 90% of the time and effort is devoted to phases 2 and 3. Phases 4 and 5 are the machine's job and 1 is relatively light-weight, albeit very important too.

### Phase 0. Application
The Applications are the primary need to use a computer in the first place.
App categories based on usage domain:
* system-development (eg. OS, utilities, network, compilers, GUIs ...)
* scientific-education  (eg. mathematics, scientific, AI, school ...)
* entertaiment-communication  (eg. A-V stuff, games, messenger apps ...)
* bussiness-professional (eg. office, enterprise, manufacturing, government ...)

### <a name="1"></a>Phase 1. requirements -> Specification
Types: functional (do) + operational-evolutionary-environmental (be)

* The steps: inception/elicitation, analysis/negotiation, modeling, specification, validation, management 

### <a name="2"></a>Phase 2. architecture-design -> Diagrams
simplicity <- structural (eg class-diagram), behavorial (eg. sequence)      

#### Design and programming Principles:
They can be categorized as related to:
* Module: do-one-thing, single-point-of-truth  
* Dependency: low Coupling (everything->interace, encapsulate-what-changes)  
* Extention: association (compos) >> generality (inher), segreg (base:derived=1:1)

#### Algοrithms
* Types: recursive, dynamic-prog, backtrack, X-&-conquer, greedy, brute-force, randomized  
* ML-algorithms: un-supervised:clust-dimension.reduction, SV:classification-regression

#### Single Computer System (HW->SW)
* HW: <ProcUnit: AL-Cntl(Regs)> keyMemory / blockStorage / <network>... / <graph-IO> Human -isa/fw-  
* Kernel: -driver-logical-virtual(buffer/cache): task(page-inode-packet)- Scheduler/IRQ/monit -syscall>  
* User: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev -home=~/. ...

Notes:
* The first line (HW) lays out briefly the usual computer architecture:
  * 'ProcUnit' consists of Arithmetic-Logic Unit, Control Until and Registers
  * 'Memory' and 'Storage' are data holders while 'ProcUnit', 'network' etc channel data (hence the '<>')
  * 'ProcUnit' (either CPU or GPU) lies in the center and everything else connects to it as peripheral (barring DMA)
  * 'keyMemory' means that a key (eg address) is needed to access memory contents
  * 'Storage' is any block device, while the others are character ones
  * 'network' interfaces with another PC's ProcUnit and eventually with its Memory/Storage: localStorage <ProcUnit> <net> <ProcUnit> remoteStorage
  * 'graph' and 'IO' interface with a Human
* The Kernel has two classes of jobs, one static and one dynamic:
  1. the static is to abstract away every hardware device and in the meantime provide data-structures to access and control them
    * approximately every HW device class corresponds to a kernel subsystem and a main data structure  
|HW      | Subssytem  | Data Struct |  
|:---:   |:---:       |:---:        |
|CPU     | Scheduler  | `task`      |
|Memory  | MMU        | `page`      | 
|Storage | File System| `inode`     |
|Network | Net subsys | `packet'    |
|GPU/IO  | Graph/IO   | ...         |

    * the abstraction layers are from the lowest to highest: firmware -> device driver -> logical level -> virtual level -> system call
    * a relevant job is to provide caches and buffers for read/writes between subsystems (eg Memory <> Storage)
    * IPC, concurrency, user management and other functionalities (which?) are made possible by using the above data structures
  2. the dynamic one is to schedule the running processes, to respond to interrupts or exceptions and possibly to monitor the whole system function through logging. These functions are considered the only logic that the kernel performs
* The user (either root or regular) executes binaries/applications and uses libraries while being in an environment (opened files, sockets etc)

#### System Architecture styles

* structural (components, layered, data-centric)
* message (async communication, event-driver, publish-subscribe)
* distributed (client-server, P2P, SOA, broker) 

Example:
* N-tier: Client <> Server {Presentation(MV*)<>Logic(micro-Services)<>Data(sql/nosqlDB)}

#### Translation
* Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IRep  
* Compiler: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  
* Interpreter: TODO

#### Graphics pipeline
* TODO

### <a name="3"></a>Phase 3. programm -> Source Code
Main goal: readability through elegance and defensiveness, error and testing  

#### Programming Language = syntax + semantics
* lexical elements (keywords-literals-ID-comments) + native/libs (types-math-strings-IO-error-net...)
* [create] Access modifier (space-time/memberof) Type (struct-class / scalar-composite-newType-function()) Reference (pointer-array) ID  
* [read] access-reference Literal/ΙD [eval] NumericOp (arithm-logical-relationall) // [update] AssignOp [control] Flow(conditional-jump)

Notes:
* This is the shortest possible encoded presentation of syntax of almost all programming languages
* In CS, there are only three fundamental operations from which every other is consisted of:
  1. CRUD (create, read, update, delete) a value from a memory location
  2. evaluate a numerical formula and
  3. control program flow (basically conditional branching and jumping, as the sequential flow is implicit)
* In the context of programming languages the CRUD operations are:
  * 'create' is the declarations of ID (variables/constants)
  * 'read' is the return or derefencing of a value
  * 'update' is the assignment operation
  * 'delete' is the garbage collection (either manual or automatic), which is ommited in the syntax
* The programming paradigms use different set of operations:
  * imperative PLs use all of the five
  * pure functional PLs use only the 'create', 'read' and 'eval' and discard (or implement indirectly? - explanation needed) 'update' and 'control'
  * logic PLs use only 'create' and discard everything else (which becomes the language translator's job)
* `struct` and `class` keywords are not types but define newTypes of struct and class type respectively. The rest (scalar, composite and function) are regular types, either native or user defined
* Examples:
  * 'create': `static` (space), ' (time in Rust), `private`, `public` (member-of), `*` (pointer), `[]` (array), myfunc(args) (function)
  * 'read': `*x`, `x[]`, `*x->y` (acc-ref ID), `'hello'` (Literal)
  * 'update': `=`
  * 'eval': `+`, `-`, `||` ...
  * 'control': `if/else`, `goto`
* Bonus hint about OOP: object orientation is synonymous to synchronous message passing. When Alan Kay [spoke][(https://news.ycombinator.com/item?id=11966570) about message passing he had ment the asynchronous one, which is the Actor model.     

### <a name="4"></a>Phase 4. translation -> Machine Code
eg ELF file format: program header-sections-section header

### <a name="5"></a>Phase 5. execution -> Electronic state
Electronic state: digital devices -> analog devices -> physics particles  

Note: in phases 4 and 5 we do not have much to say as they are run by the machine

