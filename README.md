# Systems, Computers and Software

** Note: this is an amateur, onging project. I am a Doctor, not a CSist :-) **

### Introduction

Any human endeavour can be modelled by a System which is composed and can be described by two concepts, its static Structure and its dynamic Operation.

In order to communicate any information between humans a Language is needed which has to obey two (hopefully consistent) conditions: syntax (format) and semantics (meaning).

A System is described by a Language with a specific detail, the amount of which defines an Abstraction layer.

In Software Development and Engineering (SW Dev&Eng) there are three general abstraction layers, beginning from the top-general to the low-specific..

These three layers correspond to the three stages/phases of software development.

Each higher layer is a specification which is stated declaratively and abstracts the lower.

Each lower layer is the implementation of the higher and presents a standard interface to it. 

|Phase   | -process>      | Output        | Language  |  
|:---:   |:---:           |:---:          |:---:      |
|[1](#1) | -requirements> | Specification | natural   |  
|[2](#2) | -architecture> | Diagrams      | AD/UML    |
|[3](#3) | -coding>       | Code          | program   |

Almost 90% of human working time and effort is devoted to phase 3. Phases 1 and 2 are relatively light-weight, albeit very important.


## <a name="1"></a> 1. Requirements -> Specification 

Applications are the primary motive to use a computer in the first place.
Application type is the ultimate, most abstract description.
Almost all Apps belong to the following categories based on usage domain:
* system & development (eg. OS, utilities, network, compilers, GUIs ...)
* scientific & education  (eg. mathematics, scientific, AI, school ...)
* entertaiment & communication  (eg. A-V stuff, games, messenger apps ...)
* bussiness & professional (eg. office, enterprise, manufacturing, government ...)

Two main types of Specification: DO's (functional) and BE's (operational-evolutionary-environmental)
* Some important Specs are: reli-avail-maint-port-scal-us-read: ability / correct-secur-safety-perf-compl...


## <a name="2"></a> 2. Architecture-Design -> Diagrams

At this stage Diagrams are generated based on the Specifications.

Two main types of Diagrams: Structural (eg class) and Behavorial (eg. sequence)

### Design Principles:

They can be categorized related to:
* Modularization: do-one-thing in a single-point-of-truth  
* Dependency: low Coupling (eg. encapsulate what changes, program to an interface, communicate through sharedMem of sentMessages)  
* Extensibility: association (composition) better than generalization (inheritane), segregation (base:derived=1:1)

## <a name="3"></a>3. Programming -> Source Code

Lexical (keywords-lits-IDs-comments) + (non)native Libraries (types-math-strings-runt-sys-IO-extern...)

#### Declaration [=bind] Access modif (space/member.of) typeSet-Type (primit-relat (X)set /refer) VAR-assgn-VAL
#### Expression [=call] NumOperat(mathm,access,refer)-functID(OperID) / Cond (if,else)
#### Statement [=update] reassign/del, goto/ret

Notes about Conding:
* The above is the shortest possible, encoded representation of syntax of almost all programming languages
* In CS there are only three fundamental operations from which every other is consisted of:
  1. CRUD (create, read, update, delete) a value from/to a memory or register location
  2. computation of a numerical operation 
  3. decide based on condition
* In the context of programming languages:
  * 'assign' is the declaration of Keys (variables, functions etc) plus their initialization/implementation
  * 'call' is either:
    * the execution of an Op/Cond
    * the return of a value from memory
    * the call of a function
    * the substitution of a literal
  * 'update' is the change of a mutable variable (either a variable or program pointer which leads to a jump) 
  * implicit update ops are the deletion of a variable or the return from a function

* Data Types:
  * Primitive and function are regular types, either native or user defined.
  * Group can be either `struct` or `class` that define newTypes of struct and class respectively. 
* Note: popular Object Orientation is synonymous to synchronous message passing. When Alan Kay [spoke](https://news.ycombinator.com/item?id=11966570) about message passing he had ment the asynchronous one, which is the Actor model.     

* Each programming paradigm is defined from the set of operations that uses:
  * Functional programming uses only Declarations and Expressions
  * Imperative programming uses Statements, too
    

## Computer Architecture

#### Layers: (HW) gate-μarch- (KRN) fw/drvr-logic-virtual<Sched/Irq/Mon>sysc-

Notes:
* HW lays out the usual computer architecture:
  * <ProcU:cntl/al/br> is the CPU (or GPU) with registers
  * '-' symbolizes movement of data through a bus
  * 'mem': volatile Memory (RAM) is accessed by addresses and persistent Storage by blocks
  * 'netw' interfaces with other computers' network
  * 'graph' and 'HID' interface with a Human
* The Kernel has two types of jobs, one static and one dynamic:
  * the static is to abstract every hardware device and provide data-structures to access and control each one
    * every important HW device class corresponds to a kernel subsystem and a main data structure (see table below)
    * the abstraction layers are: firmware (ISA for CPU) -> device driver -> logical level -> virtual level -> system call
    * there are caches and buffers for read/writes between subsystems
    * all functionalities (eg IPC, concurrency, user management) are performed by using the above data structures
  * the dynamic functions (which are the only kernel logic) are to schedule the running processes, to respond to interrupts or exceptions and to monitor/log the system function.
 
|HW      | Subssytem   | Data Struc |  
|:---:   |:---:        |:---:       |
|CPU     | Scheduler   | `task`     |
|Memory  | MMU         | `page`     | 
|Storage | File System | `inode`    |
|Network | Net subsys  | `packet`   |
|GPU     | Graphics    | `drm/kms`  |

### Please contribute / correct if there is any error or vagueness.
