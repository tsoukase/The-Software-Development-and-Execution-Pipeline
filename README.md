# The Software Engineering Stack

This project aims to follow the Software Engineering (SE) stages, from App conception to bare electrons.  

There are five distinct stages (processes) in SE, with six IO-structures:  

|#| -function>     | Application   | Language     | Processor|  
|---|:---:         |:---:          |:---:         |:---:     |
|1| -requirements> | Specification | natural      | human    |  
|2| -architecture> | Diagrams      | ADL/UML      | human    |
|3| -programming>  | SourceCode    | programming  | human    |
|4| -translation>  | MachineCode   | intermediate | machine  |
|5| -execution>    | Electr state  | VHDL         | machine  |

In detail:

Application
: Categories:  
  system-development  
  scientific-education  
  entertaiment-communication  
  bussiness-professional

Theory
: Algorithm-function-interface-behavior-verb (computability-complexity)
: Data-structure-state-attribute-noun (automata-languages, data structures)

Stages:  
Human1: -requirements> Specification:  
            do(functional)-be(operation-evolution-environment)
            
Human2: -architectur-design -> Diagrams:  
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

Human3: programm -> SourceCode: readability <- elegant-defensive,error-testing  
  Lang (syntax-semantics): lexical (keywords-literals-ID-comments)  
                          + native/libraries (types-mathem-strings-IO-error-network...)  
  [creat] Access modifier (space-time/memberof)  
            Type (string-class / scalar-composite-newType-function()) Reference (pointer-array) ID  
  [read] access-reference Literal/ΙD [eval] Numerical (arithm-logical-relationall) //  
            [update] Assignment [control] Flow(conditional-jump)

Machine1: translation -> MachineCode: program header-sections-section header

Machine2: execution -> Electronic state: digital -> analog -> physics
