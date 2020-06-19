# The Software Engineering Stack
The full SE stack, from App to bare electrons

develAPP (sysdevel,sciedu,entercom,bussiprof)
     Algor-func-iface-beh-verb -> Data-struct-state-attr-noun  [Language]
-hum1: requirems -> Specificats: do(func)-be(oper-evol-envir)   [natural]
-hum2: archdesgn -> Diagrams: simpl<struct:class,behav:seq      [ADL/UML]
  Princ: Mod:do1/1nce, Dep:loCou(iface</encap), Ext:asoc>gen(1:1)
  Algοr: recurs, dynaprog, backtrack, ...&conquer, greedy, brute, rand
    ML: unSV:clust-dim.red, SV:class-regres-gener-discr
  SW:  msg (async, SOA, evnt, pub-sub, mstr-slv), distr (clnt-srv, p2p, brokr)
    N-tier: Client<>Server: Pres(MV*)<>Logic(μServ)<>Data(no/sqlDB)
  [HW: <PU:al-cntl(rx)> keyMem/blkStor/<net>.../<graph-io>H] -isa/fw-
    Krnl: -drv-log-virt(buf/cch): task(page-inod-pck)- Sched/irq/mon -sysc>
    Usr: LD=/lib /bin/exec -app=/usr -conf=/etc 2>/var/log -iof=/dev ...
  Transl:Front: -prep>SC -lex>Tkn -pars>AST -sem>Graph -gen>IRep
    >Compil: -instSel-regAlloc-instSched>AsmC -asm>ObjC -link>MC
    >Interpr:
-hum3: programm -> SourceCode: read<eleg-defens,err-test        [program]
  Lang (synt-sem): lex (kw-lit-ID-#) + nativ/lib (typ-math-str-io-err-net...)
   [creat] Acc(sp-tm/mbr) Typ(str-clas/scal-comp-Tnew-fnc()) Ref(pnt-arr) ID
   [read] acc-refLit/ΙD [eval] Num(ar-lg-rl) // [upd] Asgn [cntl] Flow(cond-jmp)
                                                         
-mach1: translation -> MachineCode: prog.hd-sects-sect.hd      [intermed]
-mach2: execution -> Elect.state-off: digital>analog>physics     [VHDL]
