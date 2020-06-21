# The Software Development and Execution Pipeline

Importand Note: this is an onging work. I am a doctor not a CSist, neither 
> Computer science is mathematics with finite discrete data instead of infinite numbers.  

> Software engineering is computer science applied on hardware.

This project aims to present the Software Development (SD) stages as a piped process, from App conception to bare electrons.  
It consists of the classical Development Lifecycle phases (1-3) and the normal execution on hardware (4-5)

The five distinct stages/phases/processes, with six IO-structures piping through each one, are:  

|Stage  | -process>      | Output        | Language     | Processor|  
|:---:  |:---:           |:---:          |:---:         |:---:     |
|0      | -              | [Application](#application)|-|-         |  
|[1](#1)| -requirements> | Specification  | natural      | human    |  
|[2](#2)| -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3)| -programming>  | SourceCode    | programming  | human    |
|[4](#4)| -translation>  | MachineCode   | intermediate | machine  |
|[5](#5)| -execution>    | Electr state  | VHDL         | machine  |

### Computer Theory
A short reference to theory.  
Note: The name 'Computer science' is wrong as it is not science ... 
There are two fundamental concepts in mathematics, computers and literaly any human thought:  
* the static Stand and  
* the dynamic Change
They succeed each other in that  manner: (D) -> (S) -> (D) -> (S) ...  

Computer theory studies them in full depth and, depending on context, gives them the following names:
* Data, structure, state, attribute, noun
* Algorithm, function, behavior, interface, verb
As you are reading here, you are probably knowledgeable about these names :)   

The main topics are Formal Methods, Automata, Programming Languages, Data Structures, Computability, Complexity and Information Theory

### Application
The Application is the primary need to use a computer in the first place.
Categories (based on usage domain):
* system-development (eg. OS, utilities, network, compilers, GUIs ...)
* scientific-education  (eg. mathematics, scientific, AI, school ...)
* entertaiment-communication  (eg. A-V stuff, games, messenger apps ...)
* bussiness-professional (eg. office, enterprise, manufacturing, government ...)

### <a name="1"></a>1. requirements -> Specification
do(functional)-be(operational-evolutionary-environmental)
            
### <a name="2"></a>2. architecture-design -> Diagrams
simplicity <- structural (eg class-diagram), behavorial (eg. sequence)      

#### Principles:
* Module: do-one-thing, single-point-of-thuth  
* Dependencies: low Coupling (interace<-everything, encapsulate-what-changes)  
* Extention: association (composit) >> generality (inherit), base:derived class=1:1
            
#### Algοrithms
* Types: recursive, dynamic-prog, backtrack, X-&-conquer, greedy, brute-force, randomized  
* ML-algorithms: un-supervised:clust-dimension.reduction, SV:classification-regression

#### SW Architecture styles (TODO)
* message (async, SOA, event-driven, publish-subscribe, master-slave)  
* distributed (client-server, p-2-p, broker)  
* N-tier: Client<>Server: Pres(MV*)<>Logic(μServ)<>Data(no/sqlDB)

#### Computer System (HW->SW)
* {HW: <ProcUnit: AL-Cntl(Regs)> keyMemory / blockStorage / <network>... / <graph-IO> Human} -isa/fw-  
* Kernel: -driver-logical-virtual(buffer/cache): task(page-inode-packet)- Scheduler/IRQ/monit -syscall>  
* User: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev -home=~/. ...

Notes:
* The HW line lays out briefly the usual computer architecture:
  * Memory and Storage are data holders in contrast with ProcUnit, network etc which channel data (hence the <>)
  * 'ProcUnit' (either CPU or GPU) is in the center and everything else connects to it as peripheral (barring DMA)
  * 'keyMemory' means that memory is indexed so a key (eg. address) is needed to access its contents
  * 'Storage' is any block device, while the others are character ones
  * the 'network' interfaces with another ProUnit and eventually with its Memory/Storage
  * 'graph' and 'IO' interface with Human
* The OS-Kernel has two jobs:
  * to abstract all hardware devices and provide data-structures to access and control them
    * the levels are: firmware -> device driver -> logical level -> virtual level -> system call
    * popular data structures are `task` for CPU, `page` for memory, `inode` for storage and `packet` for network
    * relevant job is to provide caches and buffers for read/writes between them
    * IPC, concurrency, user management and other functions are made possible by using only the above structures
  * to schedule the running processes, respond to interrupts or exceptions and possibly monitor the system through logging, which are considered the only dynamic logic that the kernel performs

#### Translation
* Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IRep  
* Compiler: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  
* Interpreter: TODO

#### Graphics pipeline
* TODO

### <a name="3"></a>3. programm -> Source Code
Principles: readability <- elegant-defensive, error-testing  

#### Programming Language = syntax + semantics
* lexical (keywords-literals-ID-comments) + native/libs (types-math-strings-IO-error-net...)
* [create] Access modifier (space-time/memberof) Type (struct-class / scalar-composite-newType-function()) Reference (pointer-array) ID  
* [read] access-reference Literal/ΙD [eval] NumericOper (arithm-logical-relationall) // [update] Assignment [control] Flow(conditional-jump)

Notes:
* This is the shortest possible encoded syntax of almost all programming languages I know of
* In CS, there are only three fundamental operations from which every other is consisted of
  * CRUD (create, read, update, delete) a value from a memory location
  * evaluate a numerical formula and
  * control program flow (basically conditional branching and jumping, as the sequential flow is implicit)
* In programming languages the CRUD is:
  * 'create' is declaration of IDs (variables/constants)
  * 'read' is the return or derefencing of a value
  * 'update' is the assignment operation
  * 'delete' is the garbage collection (either manual or automatic), which is ommited in the syntax
* The programming paradigms use different set of operations:
  * imperative PLs use all five
  * pure functional PLs use only the 'create', 'read' and 'eval' and discard (or implement indirectly? explanation needed) 'update' and 'control'
  * logic PLs use only 'create' and discard everything else (which become the translator's job)
* Struct and class keywords are not types but define newTypes, struct or class respectively. The rest are regular types either native or user defined
* Examples:
  * 'create': `static` (space), TODO (time eg in Rust), `private`, `public` (member-of), `*` (pointer), `[]` (array)
  * 'read': `*x`, `x[]`, `*x->y` (acc-ref ID), `'hello'` (Literal)
  * 'update': `=`
  * 'eval': `+`, `-`, `||` ...
  * 'control': `if/else`, `goto`
* Bonus hint about OOP: object orientation is synonymous to synchronous message passing. When Alan Kay [spoke][(https://news.ycombinator.com/item?id=11966570) about message passing he had ment the asynchronous one, which is the Actor model.     

### <a name="4"></a>4. translation -> Machine Code
eg ELF file format: program header-sections-section header

### <a name="5"></a>5. execution -> Electronic state
digital devices state -> analog devices state -> physics particles state

