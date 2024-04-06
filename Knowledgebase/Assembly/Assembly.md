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

<br>

- JA/JNBE (above) : jump if superior (unsigned)
- JNC/JAE/JNB : jump if C=0 (if greater than or equal to unsigned)
- JC/JB/JNAE (below) : jump if C=1 (lower in unsigned)
- JE/JZ : jump if Z=1 (if equality after CMP or subtraction)
- JNE/JNZ : jump if Z=0 (different)
- JP/JPE : jump if P=1 (even parity)
- JNP/JPO : jump if P=0 (odd=odd)
- JO : jump if O=1 (capacity overflow in signed numbers)
- JNO : jump if O=0
- JS : jump if S=1 (negative signed number)
- JNS : jump if S=0
- JG/JNLE (greater) : jump if greater (signed numbers)
- JGE/JNL : jump if greater than or equal (signed numbers)
- JL/JNGE (less) : jump if lower (signed numbers)
- JLE/JNG : jump if less than or equal (signed numbers)
- JCXZ : jump if CX=0 (for example to test how a LOOPZ REPZ ended).

<br>

- sete:

    The sete instruction (and its equivalent, setz) sets its argument to 1 if the zero flag is set or to 0 otherwise. The zero flag is set if the last comparison or arithmetic instruction yielded equality or a result of zero. Thus in your case, sete sets al to 0 or 1 according to the result of the preceeding cmp instruction. 

 

Aus <https://stackoverflow.com/questions/53011701/what-does-the-instruction-sete-do-in-assembly>  

- CDQE: 

    The CDQE instruction sign-extends a DWORD (32-bit value) in the EAX register to a QWORD (64-bit value) in the RAX register.  
    https://stackoverflow.com/questions/54618685/what-is-the-meaning-use-of-the-movzx-cdqe-instructions-in-this-code-output-by-a  
    https://www.felixcloutier.com/x86/cbw:cwde:cdqe  

Compiler Explorer: https://godbolt.org/  
Decompiler: https://dogbolt.org/