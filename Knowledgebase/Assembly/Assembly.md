## **Assembly**

### Register
- https://mspgcc.sourceforge.net/manual/x82.html

eax, ebx, ecx = das e steht für extended --> 32 bit register  
rax, rbx,, rcx, rdx = 64 bit register  
Sr = status register (z.B zero flag)

## Syscalls
![Beschreibung des Bildes](/Knowledgebase/Assembly/images/syscalls.png)  

Beispielcode:  
![Beschreibung des Bildes](/Knowledgebase/Assembly/images/assembly_code.png)  

Erklärung:
```
Die ID des Systemaufrufes in die Register laden. Hier zweimal die 1, da diese in der tabelle für sys_write steht. Deshalb schieben wir 1 in rax und rdi.  

rsi nimmt einen pointer auf einen Buffer entgegen, weshalb wir dort die Adresse unseres Buffers reinschieben 

lea = load effective address from the hello_world buffer 

rdx nimmt die Länge des Buffers entegegen --> "Hello, World!\n" ist 14 Zeichen lang 
-------------------------------- 
60 steht für den Systemaufruf sys_exit 

rdi enthält den Exitcode --> hier 69 xD (normalerweise 0 oder 1) 

asciz --> ASCII String null terminated 
```


### Commands
- jne = jump if not equal 
- je = jump if equal 
- jg = jump if greater --> ZB wenn man zwei Nummern vergleicht 
- jmp = zu Funktion springen 
- test al,al = prüfen, ob das zero bit gesetzt ist --> true or false


- sete =  

The sete instruction (and its equivalent, setz) sets its argument to 1 if the zero flag is set or to 0 otherwise. The zero flag is set if the last comparison or arithmetic instruction yielded equality or a result of zero. Thus in your case, sete sets al to 0 or 1 according to the result of the preceeding cmp instruction. 

 

Aus <https://stackoverflow.com/questions/53011701/what-does-the-instruction-sete-do-in-assembly>  