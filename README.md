# The Software Engineering Pipe

> Computer science is mathematics with finite discrete data instead of infinite numbers.
> Software engineering is computer science applied on hardware.

This project aims to present the Software Engineering (SE) stages as a piped process, from App conception to bare electrons.  

In SE there are five distinct stages (processes), with six IO-structures piping through each one:  

|Stage  | -process>      | Output        | Language     | Processor|  
|:---:  |:---:           |:---:          |:---:         |:---:     |
|0      | -              | [Application](#application)|-|-         |  
|[1](#1)| -requirements> | Specification | natural      | human    |  
|[2](#2)| -architecture> | Diagrams      | ADL/UML      | human    |
|[3](#3)| -programming>  | SourceCode    | programming  | human    |
|[4](#4)| -translation>  | MachineCode   | intermediate | machine  |
|[5](#5)| -execution>    | Electr state  | VHDL         | machine  |

## Computer Theory
* Algorithm-function-interface-behavior-verb (computability-complexity)
* Data-structure-state-attribute-noun (automata-languages, data structures)
Hint: The name 'Computer science' is wrong as it is not science but theory... 

### Application
It refers to the primary need to use a computer in the first place.
Categories:
* system-development (eg. OS, utilities, compilers ...)
* scientific-education  (eg. mathematics, scientific, school ...)
* entertaiment-communication  (eg. AV stuff messenger ...)
* bussiness-professional (eg. enterprise, government ...)

### <a name="1"></a>1. requirements -> Specification
do(functional)-be(operational-evolutionary-environmental)
            
### <a name="2"></a>2. architecture-design -> Diagrams
simplicity <- structural (eg class-diagram), behavorial (eg. sequence)      
            
  Principles: Module: do-one-thing, one-point-of-thuth  
              Dependencies: lowCoupling(interace<-, encapsulation)  
              Extention: association >> generality (base:derived=1:1)
            
  Algοrithms: recursive, dynamic programming, backtrack, ...-&-conquer, greedy, brute-force, randomized  
     ML-algorithms: un-supervised:clust-dimension.reduction, SV:classification-regression
     
  SW-architecture:  message (async, SOA, event-driven, publish-subscribe, master-slave),  
          distributed (client-server, p-2-p, broker)  
   N-tier: Client<>Server: Pres(MV*)<>Logic(μServ)<>Data(no/sqlDB)
   
  [HW: <ProccessingUnit: AL-Control(Registers)> keyedMemory / blockedlkStorage
   / <net>... / <graph-io> Human] -isa/fw-  
    Kernel: -driver-logical-virtual(buffer/cache): task(page-inode-packet)- Scheduler/IRQ/monitor -systemcall>  
    User: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev ...  
  
  Translation :Front-end: -preproc>SCode-lexer>Token -parser>AST -semantic>Graph -generator>IRep  
    >Compiler: -instructionSelect-registerAlloc-instrSchedul>AsmCode -asm>ObjCode -link>MachineCode  
    >Interpreter:

### <a name="3"></a>3. programm -> SourceCode
readability <- elegant-defensive,error-testing  

  Lang (syntax-semantics): lexical (keywords-literals-ID-comments)  
                          + native/libraries (types-mathem-strings-IO-error-network...)  
  [creat] Access modifier (space-time/memberof)  
            Type (string-class / scalar-composite-newType-function()) Reference (pointer-array) ID  
  [read] access-reference Literal/ΙD [eval] Numerical (arithm-logical-relationall) //  
            [update] Assignment [control] Flow(conditional-jump)

### <a name="4"></a>4. translation -> MachineCode
program header-sections-section header

### <a name="5"></a>5. execution -> Electronic state
digital -> analog -> physics
