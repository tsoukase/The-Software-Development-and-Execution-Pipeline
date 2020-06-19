# The Software Engineering Stack

This project aims to follow the Software Engineering (SE) stages, from App conception to bare electrons.\

There are five distinct stages (processes) in SE, with six structures:\

Application\
1) -requirements> Specification\
2) -architecture> Diagrams\
3) -programming> SourceCode\
4) -translation> MachineCode\
5) -execution> Electronic state\

The first three are run by Human and the last by Machine.\

In detail:\

Application categories:\
  system-development\
  scientific-education\
  entertaiment-communication\
  bussiness-professional\

Algorithm-function-interface-behavior-verb -> Data-structure-state-attribute-noun  [Language]\
-hum1: requirems -> Specificats: do(func)-be(oper-evol-envir)   [natural]\
-hum2: archdesgn -> Diagrams: simpl<struct:class,behav:seq      [ADL/UML]\
  Princ: Mod:do1/1nce, Dep:loCou(iface</encap), Ext:asoc>gen(1:1)\
  Algοr: recurs, dynaprog, backtrack, ...&conquer, greedy, brute, rand\
    ML: unSV:clust-dim.red, SV:class-regres-gener-discr\
  SW:  msg (async, SOA, evnt, pub-sub, mstr-slv), distr (clnt-srv, p2p, brokr)\
    N-tier: Client<>Server: Pres(MV*)<>Logic(μServ)<>Data(no/sqlDB)\
  [HW: <PU:al-cntl(rx)> keyMem/blkStor/<net>.../<graph-io>H] -isa/fw-\
    Krnl: -drv-log-virt(buf/cch): task(page-inod-pck)- Sched/irq/mon -sysc>\
    Usr: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev ...\
  Transl:Front: -prep>SC -lex>Tkn -pars>AST -sem>Graph -gen>IRep\
    >Compil: -instSel-regAlloc-instSched>AsmC -asm>ObjC -link>MC\
    >Interpr:\
-hum3: programm -> SourceCode: read<eleg-defens,err-test        [program]\
  Lang (synt-sem): lex (kw-lit-ID-#) + nativ/lib (typ-math-str-io-err-net...)\
   [creat] Acc(sp-tm/mbr) Typ(str-clas/scal-comp-Tnew-fnc()) Ref(pnt-arr) ID\
   [read] acc-refLit/ΙD [eval] Num(ar-lg-rl) // [upd] Asgn [cntl] Flow(cond-jmp)\
-mach1: translation -> MachineCode: prog.hd-sects-sect.hd      [intermed]\
-mach2: execution -> Elect.state-off: digital>analog>physics     [VHDL]\
