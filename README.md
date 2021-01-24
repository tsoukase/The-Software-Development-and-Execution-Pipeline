# The Software Development and Execution Pipeline

**Note: this is an onging, amateur, hobby project. I am a Doctor, not a CSist.**

### Introduction

The fundamental concept of every System Design is Abstraction in layers, where each layer abstracts (= removes, hides) the details of the lower one in the hiearchy.

This project aims to present the Software Development and Execution phases as a piped process, from App conception to bare electrons.  

It consists of the classical SW Development Lifecycle (phases 1-3) and the its execution on hardware (phase 4).

Each higher layer is a specification which is stated declaratively and abstracts the lower.

Each lower layer is the implementation of the higher one and presents a standard interface to it. 

The four (plus 0) distinct phases, with five IO structures piping through each one, are:  

|Phase   | -process>      | Output        | Language     | Machine  |  
|:---:   |:---:           |:---:          |:---:         |:---:     |
|[0](#0) | -              | Application   |-             |-         |  
|[1](#1) | -requirements> | Specification | natural      | human    |  
|[2](#2) | -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3) | -coding>       | SourceCode    | programming  | human    |
|[4](#4) | -execution>    | Electr state  | VHDL         | machine  |

Almost 90% of human time and effort is devoted to phases 3 (coding). Phases 1 (requirements) and 2 (architecture) are relatively light-weight, albeit very important too and phase 4 is the machine's job (except when reverse engineering).

### <a name="0"></a>Phase 0. Application
Applications are the primary motive to use a computer in the first place.
Almost all Apps belong to the following categories based on usage domain:
* system & development (eg. OS, utilities, network, compilers, GUIs ...)
* scientific & education  (eg. mathematics, scientific, AI, school ...)
* entertaiment & communication  (eg. A-V stuff, games, messenger apps ...)
* bussiness & professional (eg. office, enterprise, manufacturing, government ...)

### <a name="1"></a>Phase 1. requirements -> Specification
Types: functional ('do's) + operational-evolutionary-environmental ('be's)

* Some important Specs are reli-avail-maintain-port-scal-us-Ability and correct-perform-compli-Ance, security...
* Substeps: inception/elicitation, analysis/negotiation, modeling, specification, validation, management 

### <a name="2"></a>Phase 2. architecture-design -> Diagrams
Types: Structural (eg class-diagram), behavorial (eg. sequence-diagram). Goal is simplicity

#### Design Principles:
They can be categorized as related to:
* Modularization: do-one-thing in a single-point-of-truth  
* Dependency: low Coupling (encapsulate what changes, everything->interface)  
* Extensibility: associat (composit) > general (inherit), segreg (base:derived=1:1)
* Distribution: Message passing (layered,Object,Event,SOA,μ-krn,P2P) vs SharedMemory (DB,blackb,rule)

#### Computer design: HW<>Kernel
* HW: adrMem/blkStor -bus- (cache)<CntlU><ALU/branch> / -network/-graphics/-HID
* Kern: -isa/firmwdriver-logic-virtual:Task(Page-Inod-Pack)[buff-cch]- Sched/Irq/Monit -sysc<>

Notes:
* HW lays out the usual computer architecture:
  * <CntlU><ALU/branch> is the CPU (or GPU) with registers
  * - symbolizes movement of data through a bus
  * volatile Memory (REM) is accessed by addresses and persistent Storage by blocks
  * 'network' interfaces with other computers' network
  * 'graphics' and 'HID' interface with a Human
* The Kernel has two classes of jobs, one static and one dynamic:
  1. the static is to abstract every hardware device and provide data-structures to access and control each one
    * every important HW device class corresponds to a kernel subsystem and a main data structure (see table below)
    * the abstraction layers are: firmware (ISA for CPU) -> device driver -> logical level -> virtual level -> system call
    * there are caches and buffers for read/writes between subsystems
    * all functionalities (eg IPC, concurrency, user management) are performed by using the above data structures
  2. the dynamic functions (which are the only kernel logic) are to schedule the running processes, to respond to interrupts or exceptions and to monitor/log the system function.
 
|HW      | Subssytem  | Data Structure |  
|:---:   |:---:       |:---:           |
|CPU     | Scheduler  | `task`         |
|Memory  | MMU        | `page`         | 
|Storage | File System| `inode`        |
|Network | Net subsys | `packet`       |
|GPU/IO  | Graph/IO   | `drm/kms`      |


#### Application design
* N-tier: Presentation(UI,MV) <> Logic(service,logic,Control) <> Data(DB,log)
Compiler
* Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IntermRepres  
* Back-end: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  

### <a name="3"></a>Phase 3. programming -> Source Code
Goal: readability through elegance, defensiveness, error checking and testing  

#### Programming Language = syntax + semantics
Lexical elements (keywords-literals-IDs-comments) + (non)native libraries (types-math-strings-IO-error-net...)
* Declar: [create] Access modif (space-time/memberof) Type (struct-class / scalar-compos-newType-function()) Refer (pointer-array) ID  
* Expr: [read] access-refer Literal/ΙD [numeric] NumericOp (arithm-logical-relat) // Statem: [update] AssignOp [control] Flow(condit-jump)

Notes:
* This is the shortest possible, encoded representation of syntax of almost all programming languages
* In CS, there are only three fundamental operations from which every other is consisted of:
  1. CRUD (create, read, update, delete) a value from/to a memory location
  2. computation of a numerical (arithemtic) operation and
  3. control program flow (conditional branching and jumping)
* In the context of programming languages:
  * 'create' is the declaration of IDs (variables/functions) plus their initialization (using =/{}) with a value  
  * 'read' is the return of a value from memory, call of a function or substitution of a literal
  * 'update' is the reassignment operation of a mutable variable (:=) 
  * 'delete' is the manual or automatic freeing of memeory (is omitted above)
  * 'numeric' is the computation of a numerical operation
  * 'control' is program flow control (conditional branching and jumping)
* Also:
  * 'create' and 'delete' are declarations that allocate/free memory
  * 'numeric' and 'read' constitute expressions that are to be evaluated
  * 'update' and 'control' constitute statements that are to be executed

|               |Memory access |Execution |  
|:---:          |:---:         |:---:     |
|**Expression** | read         | numeric  |
|**Statement**  | update       | control  |

* Keywords `struct` and `class` are not types but define newTypes of struct and class type respectively. The rest (scalar, composite and function) are regular types, either native or user defined
* Examples:
  * 'create': `static` (space), ' (time in Rust), `private`, `public` (member-of), `*` (pointer), `[]` (array), myfunc(args) (function)
  * 'read': `*x`, `x[]`, `*x->y` (acc-ref ID), `'hello'` (Literal)
  * 'update': `=`
  * 'numeric': `+`, `-`, `||` ...
  * 'control': `if/else`, `goto`
* Note about OOP: object orientation is synonymous to synchronous message passing. When Alan Kay [spoke](https://news.ycombinator.com/item?id=11966570) about message passing he had ment the asynchronous one, which is the Actor model.     
* The programming paradigms use different sets of operations:
  * Logic uses only 'create' and omit everything else
  * Functional uses the above, 'read' and 'numeric'
  * Imperative uses all of the five OPs

### <a name="4"></a>Phase 4. execution -> Electronic state
Electronic state: digital devices -> analog devices -> physics particles  
Note: here we do not have much to say as they are run by the machine

===

### Please contribute / correct if there is any error or vagueness.
