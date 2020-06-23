# The Software Development and Execution Pipeline

**Importand Note: this is an onging work. I am a doctor, not a CSist neither a SEer.**
> Computer science is mathematics with discrete and finite Data instead of infinite numbers.  

> Software engineering is computer science applied on hardware.

### An short note about System Design

The fundamental concept of System Design in layers is Abstraction, where each layer abstracts (= removes, hides) the details of the next one in the hiearchy.  

The above layer is the specification which is stated declaratively and composed by data, while the lower layer in the implementation which is composed by data and algorithms.


This project aims to present the Software Development phases as a piped process, from App conception to bare electrons.  
It consists of the classical Development Lifecycle phases (1-3) and the regular execution on hardware (4-5)

The five distinct phases/processes, with six IO-structures piping through each one, are:  

|Phase  | -process>      | Output        | Language     | Processor|  
|:---:  |:---:           |:---:          |:---:         |:---:     |
|0      | -              | [Application](#application)|-|-         |  
|[1](#1)| -requirements> | Specification  | natural      | human    |  
|[2](#2)| -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3)| -programming>  | SourceCode    | programming  | human    |
|[4](#4)| -translation>  | MachineCode   | intermediate | machine  |
|[5](#5)| -execution>    | Electr state  | VHDL         | machine  |

The process can be seen in two dimensions:
1. as a succession of process->output phases, where the output of one phase is input for the next  
2. as an abstaction, where each layer is a specification or declaration and the next one is its implementation

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
    * approximately every HW device class corresponds to a kernel subsystem and a main data structure (see table below)
    * the abstraction layers are from the lowest to highest: firmware -> device driver -> logical level -> virtual level -> system call
    * a relevant job is to provide caches and buffers for read/writes between subsystems (eg Memory <> Storage)
    * IPC, concurrency, user management and other functionalities (which?) are made possible by using the above data structures
  2. the dynamic is to schedule the running processes, to respond to interrupts or exceptions and possibly to monitor the whole system function through logging. These functions are considered the only logic that the kernel performs
* The user (either root or regular) executes binaries/applications and uses libraries while being in an environment (opened files, sockets etc)

|HW      | Subssytem  | Data Structure |  
|:---:   |:---:       |:---:           |
|CPU     | Scheduler  | `task`         |
|Memory  | MMU        | `page`         | 
|Storage | File System| `inode`        |
|Network | Net subsys | `packet`       |
|GPU/IO  | Graph/IO   | ...            |

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
* [read] access-reference Literal/ΙD [num] NumericOp (arithm-logical-relationall) // [update] AssignOp [control] Flow(conditional-jump)

Notes:
* This is the shortest possible encoded presentation of syntax of almost all programming languages
* In CS, there are only three fundamental operations from which every other is consisted of:
  1. CRUD (create, read, update, delete) a value from/to a memory location
  2. computation of a numerical operation and
  3. control program flow (sequential as default, conditional branching and jumping)
* In the context of programming languages:
  * 'create' is the declaration of IDs (variables/contstants/functions) plus their initialization (with = or {}) with values  
  * 'read' is the return of a value from memory, call of a function or substitution of a literal
  * 'update' is the reassignment operation of a mutable variable (:=) 
  * 'delete' is the manual or automatic freeing of memeory, which is ommited in the syntax
  * 'num' is the computation of a numerical operation
  * 'control' is program flow control
* Also, in PLs:
  * 'num' and 'read' constitute expressions which are to be evaluated
  * 'update' and 'control' constitute statements which are to be executed
* The programming paradigms use different sets of operations:
  * imperative PLs use all of the five
  * pure functional PLs use only the 'create', 'read' and 'eval' and discard (or implement indirectly? - explanation needed) 'update' and 'control'
  * logic PLs use only 'create' and discard everything else (which becomes the language translator's job)
* `struct` and `class` keywords are not types but define newTypes of struct and class type respectively. The rest (scalar, composite and function) are regular types, either native or user defined
* Examples:
  * 'create': `static` (space), ' (time in Rust), `private`, `public` (member-of), `*` (pointer), `[]` (array), myfunc(args) (function)
  * 'read': `*x`, `x[]`, `*x->y` (acc-ref ID), `'hello'` (Literal)
  * 'update': `=`
  * 'num': `+`, `-`, `||` ...
  * 'control': `if/else`, `goto`
* Bonus hint about OOP: object orientation is synonymous to synchronous message passing. When Alan Kay [spoke](https://news.ycombinator.com/item?id=11966570) about message passing he had ment the asynchronous one, which is the Actor model.     

|              |Memory access | Execution |  
|:---:         |:---:         |:---:      |
|**Both Pdgms**| read         |num        |
|**Imperative**| update       |control    |


### <a name="4"></a>Phase 4. translation -> Machine Code
eg ELF file format: program header-sections-section header

### <a name="5"></a>Phase 5. execution -> Electronic state
Electronic state: digital devices -> analog devices -> physics particles  

Note: in phases 4 and 5 we do not have much to say as they are run by the machine

===

### Please contribute / correct if there is any error or vagueness.
