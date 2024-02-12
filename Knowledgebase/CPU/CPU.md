
## **Tutorials**
### **How a CPU works and Introduction to Assembler**
- [How a CPU works and Introduction to Assembler - bin 0x04](https://www.youtube.com/watch?v=6jSKldt7Eqs&list=PLhixgUqwRTjxglIswKp9mpkfPNfHkzyeN&index=7)

## **Hex**
### Read a memory dump
Registers:
```
pc  448a  sp 439a  sr 0000  cg 0000
r04 0000 r05 5a08 r06 0000 r07 0000 
r08 0000 r09 0000 r10 0000 r11 0000 
r12 0000 r13 0000 r14 0002 r15 439c 
```
Problem: get the content where r15 points at.

original memory dump:
```
4380: 0000 0000 0000 0000 0000 0000 1645 0000   .............E..
4390: 6045 0200 9c43 6400 8844 5044 0000 0000   `E...Cd..DPD....
43a0: 0000 0000 0000 0000 0000 0000 0000 0000   ................
```

formatted memory dump:  
```
      00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f
      -----------------------------------------------
4380: 00 00 00 00 00 00 00 00 00 00 00 00 16 45 00 00   .............E..
4390: 60 45 02 00 9c 43 64 00 88 44 50 44 00 00 00 00   `E...Cd..DPD....
43a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00   ................
```

![Beschreibung des Bildes](/Knowledgebase/CPU/images/hex_editor_01.png)

To get the value from the adress in r15, we have to look at the line 4390 and count till c.  
Then we can select it in the HexEditor to se the decoded text value.  

![Beschreibung des Bildes](/Knowledgebase/CPU/images/hex_editor_02.png)


### Big- and Little Endian
![Beschreibung des Bildes](/Knowledgebase/CPU/images/th-4221105878.jpg)  
Example: https://youtu.be/L3BwXbRDQM4?t=87


### **MSP430**
- https://phas.ubc.ca/~michal/phys319/MSP430Reference-RyansEdit.pdf 
