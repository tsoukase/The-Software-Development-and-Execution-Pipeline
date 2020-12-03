# The Software Development and Execution Pipeline

**Importand Note: this is an onging, amateur, hobby work. I am a doctor, not a CSist neither a SEer.**

> Computer science is mathematics with discrete, finite data instead of infinite numbers.  
> Software engineering is computer science applied on hardware.

### Introduction

The fundamental concept of every System's Design is Abstraction in layers, where each layer abstracts (= removes, hides) the details of the lower one in the hiearchy.  

This project aims to present the Software Development and Execution phases as a piped process, from App conception to bare electrons.  

It consists of the classical SW Development Lifecycle (phases 1-3) and the its execution on hardware (phases 4-5).

Each higher layer abstracts the lower and is a specification which is stated declaratively as data.

Each lower layer is the implementation of the higher one, presents a standard interface to it and is literally a virtual machine composed by data and algorithms.

The five (plus phase 0) distinct phases, with six IO-structures piping through each one, are:  

|Phase  | -process>      | Output        | Language     | Machine  |  
|:---:  |:---:           |:---:          |:---:         |:---:     |
|0      | -              | [Application](#application)|-|-         |  
|[1](#1)| -requirements> | Specification | natural      | human    |  
|[2](#2)| -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3)| -programming>  | SourceCode    | programming  | human    |
|[4](#4)| -translation>  | MachineCode   | intermediate | machine  |
|[5](#5)| -execution>    | Electr state  | VHDL         | machine  |

Almost 90% of human time and effort is devoted to phases 2 (architecture) and 3 (coding). Phases 4 and 5 are the machine's job (except reverse engineering) and 1 (requirements) is relatively light-weight, albeit very important too.

### Phase 0. Application
Applications are the primary motive and need to use a computer in the first place.
Almost all Apps belong to the following categories based on usage domain are:
* system & development (eg. OS, utilities, network, compilers, GUIs ...)
* scientific & education  (eg. mathematics, scientific, AI, school ...)
* entertaiment & communication  (eg. A-V stuff, games, messenger apps ...)
* bussiness & professional (eg. office, enterprise, manufacturing, government ...)

### <a name="1"></a>Phase 1. requirements -> Specification
Types: functional (do) + operational-evolutionary-environmental (be)

* Most important Specs: reli-avail-maintain-port-scal-us-ability, correct-secur-perform-compliance...
* Substeps: inception/elicitation, analysis/negotiation, modeling, specification, validation, management 

### <a name="2"></a>Phase 2. architecture-design -> Diagrams
Types: Structural (eg class-diagram), behavorial (eg. sequence). Goal: simplicity

#### Design Principles:
They can be categorized as related to:
* Modularization: do-one-thing in a single-point-of-truth, pipe/layer design  
* Dependency: low Coupling (everything->interace, encapsulate-what-changes)  
* Extensibility: associat (composit) >> general (inherit), segreg (base:derived=1:1)

#### Algοrithms
* Types: recursive, dynamic-prog, backtrack, X-&-conquer, greedy, brute-force, randomized  
* ML-algorithms: un-supervised:clust-dimension.reduction, SV:classification-regression

#### Single Computer: HW<>Kernel
* HW: adrMem/blkStor -bus- (cache)<CntlU><ALU/branch> / -network-... / -graph&hid-Hum
* Kern: -isa/firmw-driver-logic-virtual:Task(Page-Inod-Pack)[buff-cch]- Sched/irq/monit -sysc>

Notes:
* HW line lays out the usual computer architecture:
  * (cache)<CntlU><ALU/branch> is the CPU or GPU with registers and cache
  * - symbolizes movement of data through a bus
  * volatile Memory is orginized in addresses and persistent Storage in blocks
  * 'network' interfaces with other Computers' network
  * 'graph' and 'hid' interface with a Human
* The Kernel has two classes of jobs, one static and one dynamic:
  1. the static is to abstract every hardware device and provide data-structures to access and control each
    * approximately every HW device class corresponds to a kernel subsystem and a main data structure (see table below)
    * the abstraction layers are: firmware (ISA form CPU) -> device driver -> logical level -> virtual level -> system call
    * there are caches and buffers for read/writes between subsystems
    * all functionalities (eg IPC, concurrency, user management) are performed by using the above data structures
  2. the dynamic is to schedule the running processes, to respond to interrupts or exceptions and to monitor/log the system function. These functionalies are considered the only kernel logic

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

#### Language Translation
* Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IntermRepres  
* Compiler: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  
* Interpreter: TODO

#### GPU pipeline
* TODO: -> libwin -> glibc/mesa -> libdrm -> syscall -> KMS ->cnt/DRM -> GPU

### <a name="3"></a>Phase 3. programming -> Source Code
Goal: readability through elegance, defensiveness, error checking and testing  

#### Programming Language = syntax + semantics
* lexical elements (keywords-literals-IDs-comments) + (non)native libraries (types-math-strings-IO-error-net...)
* Declar: [create] Access modif (space-time/memberof) Type (struct-class / scalar-compos-newType-function()) Refer (pointer-array) ID  
* Expr: [read] access-refer Literal/ΙD [numer] NumericOp (arithm-logical-relat) // Statem: [update] AssignOp [control] Flow(condit-jump)
* Shell: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev -home=~/. ...
* The user (root or non) executes binaries/applications and uses libraries while being in an environment (opened files, sockets etc)

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
  * 'numer' is the computation of a numerical operation
  * 'control' is program flow control
* Also, in PLs:
  * 'numeric' and 'read' constitute expressions which are to be evaluated
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
  * 'numer': `+`, `-`, `||` ...
  * 'control': `if/else`, `goto`
* Bonus hint about OOP: object orientation is synonymous to synchronous message passing. When Alan Kay [spoke](https://news.ycombinator.com/item?id=11966570) about message passing he had ment the asynchronous one, which is the Actor model.     

|                           |Memory access |Execution |  
|:---:                      |:---:         |:---:     |
|**Expression - Both Pdgms**| read         | numer    |
|**Statement  - Imperative**| update       | control  |


### <a name="4"></a>Phase 4. translation -> Machine Code
eg ELF file format: program header-sections-section header

### <a name="5"></a>Phase 5. execution -> Electronic state
Electronic state: digital devices -> analog devices -> physics particles  

Note: in phases 4 and 5 we do not have much to say as they are run by the machine

===

### Please contribute / correct if there is any error or vagueness.
