# The Software Development and Execution Pipeline

> Computer science is mathematics with finite discrete data instead of infinite numbers.
> Software engineering is computer science applied on hardware.

This project aims to present the Software Development (SD) stages as a piped process, from App conception to bare electrons.  
It extents the Development Lifecycle phases.

In SD there are five distinct stages (processes), with six IO-structures piping through each one:  

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
Both succeed each other in that manner: (D) -> (S) -> (D) -> (S) ...  
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
* Module: do-one-thing, one-point-of-thuth  
* Dependencies: lowCoupling(interace<-, encapsulation)  
* Extention: association >> generality (base:derived=1:1)
            
#### Algοrithms
* Types: recursive, dynamic programming, backtrack, ...-&-conquer, greedy, brute-force, randomized  
* ML-algorithms: un-supervised:clust-dimension.reduction, SV:classification-regression
     
#### SW Architecture styles
* message (async, SOA, event-driven, publish-subscribe, master-slave),  
* distributed (client-server, p-2-p, broker)  
* N-tier: Client<>Server: Pres(MV*)<>Logic(μServ)<>Data(no/sqlDB)

#### Computer System
* {HW: <ProcUnit: AL-Cntrl(Regs)> keyedMemory / blockedStorage / <net>... / <graph-io> Human} -isa/fw-  
* Kernel: -driver-logical-virtual(buffer/cache): task(page-inode-packet)- Scheduler/IRQ/monit -syscall>  
* User: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev ...  

#### Translation
* Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IRep  
* Compiler: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  
* Interpreter:

#### Graphics pipeline
* TODO

### <a name="3"></a>3. programm -> SourceCode
readability <- elegant-defensive,error-testing  

#### Lang (syntax-semantics):
* lexical (keywords-literals-ID-comments) + native/libs (types-math-strings-IO-error-net...)
* [creat] Access modifier (space-time/memberof)  
            Type (string-class / scalar-composite-newType-function()) Reference (pointer-array) ID  
* [read] access-reference Literal/ΙD [eval] Numerical (arithm-logical-relationall) //  
            [update] Assignment [control] Flow(conditional-jump)

### <a name="4"></a>4. translation -> MachineCode
program header-sections-section header

### <a name="5"></a>5. execution -> Electronic state
digital -> analog -> physics
