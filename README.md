# The Software Development and Execution Pipeline

> Computer science is mathematics with finite discrete data instead of infinite numbers.  

> Software engineering is computer science applied on hardware.

This project aims to present the Software Development (SD) stages as a piped process, from App conception to bare electrons.  
It consists of the classical Development Lifecycle phases (1-3) and the normal execution on hardware (4-5)

The five distinct stages/phases/processes, with six IO-structures piping through each one, are:  

|Stage  | -process>      | Output        | Language     | Processor|  
|:---:  |:---:           |:---:          |:---:         |:---:     |
|0      | -              | [Application](#application)|-|-         |  
|[1](#1)| -requirements> | Specification | natural      | human    |  
|[2](#2)| -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3)| -programming>  | SourceCode    | programming  | human    |
|[4](#4)| -translation>  | MachineCode   | intermediate | machine  |
|[5](#5)| -execution>    | Electr state  | VHDL         | machine  |

### Computer Theory
A short reference to theory.  
There are two fundamental concepts in mathematics, computers and literaly any human thought:  
* the static Stand and  
* the dynamic Change

They succeed each other in that manner: (D) -> (S) -> (D) -> (S) ...  
Computer theory studies them in depth giving them the following names:
* Data-structure-state-attribute-noun (automata-languages, data structures)  
* Algorithm-function-interface-behavior-verb (computability-complexity)  
As you are reading Github, you are probably knowledgeable with these names :)   
Hint: The name 'Computer science' is wrong as it is not science ... 

### Application
It refers to the primary need to use a computer in the first place.
Categories (based on application domain):
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

#### SW Architecture styles
* message (async, SOA, event-driven, publish-subscribe, master-slave),  
* distributed (client-server, p-2-p, broker)  
* N-tier: Client<>Server: Pres(MV*)<>Logic(μServ)<>Data(no/sqlDB)

#### Computer System (HW->SW)
* {HW: <ProcUnit: AL-Cntl(Regs)> keyMemory / blockStorage / <network>... / <graph-IO> Human} -isa/fw-  
* Kernel: -driver-logical-virtual(buffer/cache): task(page-inode-packet)- Scheduler/IRQ/monit -syscall>  
* User: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev -home=~/. ...

#### Translation
* Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IRep  
* Compiler: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  
* Interpreter: TODO

#### Graphics pipeline
* TODO

### <a name="3"></a>3. programm -> Source Code
readability <- elegant-defensive,error-testing  

#### Programming Language = syntax+semantics
* lexical (keywords-literals-ID-comments) + native/libs (types-math-strings-IO-error-net...)
* [create] Access modifier (space-time/memberof) Type (struct-class / scalar-composite-newType-function()) Reference (pointer-array) ID  
* [read] access-reference Literal/ΙD [eval] NumericOper (arithm-logical-relationall) // [update] Assignment [control] Flow(conditional-jump)

Notes:
* The above is the shortest encoded syntax of almost all programming languages
* In CS, there are only three fundamental operations from which every other is consisted of: CRUD (create, read, update, delete) a value from a memory location, evaluate a numerical formula and control program flow (basically conditional branching and jumping, as the sequential flow is implicit)
* In programming languages the 'create' is the declaration, the 'read' is the derefencing and 'update' is the assignment. The 'delete' is intuitively the garbage collection, which is ommited in the syntax!
* Pure functional programming languages use only 'create', 'read' and 'eval' and discard 'update' and 'control'
* Logic programming languages uses only 'create' and discards everything else
* Struct and class are meta-types (that is, types that define types), the rest are regular types either native or user defined
* 'newType' is defined either by 'struct' or 'class' keywords and create a new struct or class respectively
* Examples:
  * 'create': `static` (space), TODO (time eg in Rust), `private`, `public` (member-of), `*` (pointer), `[]` (array)
  * 'read': `*x`, `x[]`, `*x->y` (acc-ref ID), `'hello'` (Literal)
  * 'eval': `+`, `-`, `||` ...
  * 'update': `=`
  * 'control': `if/else`, `goto`

### <a name="4"></a>4. translation -> Machine Code
program header-sections-section header

### <a name="5"></a>5. execution -> Electronic state
digital -> analog -> physics

