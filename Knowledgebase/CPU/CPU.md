
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


### **MSP430**
- https://phas.ubc.ca/~michal/phys319/MSP430Reference-RyansEdit.pdf 


## Endianness

Endianness is the order in which bytes within a word of digital data are transmitted over a data communication medium or addressed (by rising addresses) in computer memory.

![Beschreibung des Bildes](/Knowledgebase/CPU/images/th-4221105878.jpg)  
Example: https://youtu.be/L3BwXbRDQM4?t=87


### Big Endian

A big-endian system stores the most significant byte of a word at the smallest memory address and the least significant byte at the largest.
Big-endianness is the dominant ordering in networking protocols, such as in the Internet protocol suite, where it is referred to as network order, transmitting the most significant byte first.

### Little Endian 

A little-endian system, in contrast, stores the least-significant byte at the smallest address.
little-endianness is the dominant ordering for processor architectures (x86, most ARM implementations, base RISC-V implementations) and their associated memory. File formats can use either ordering; some formats use a mixture of both or contain an indicator of which ordering is used throughout the file.

### Middle Endian

Numerous other orderings, generically called middle-endian or mixed-endian, are possible.

The PDP-11 is in principle a 16-bit little-endian system. The instructions to convert between floating-point and integer values in the optional floating-point processor of the PDP-11/45, PDP-11/70, and in some later processors, stored 32-bit "double precision integer long" values with the 16-bit halves swapped from the expected little-endian order. The UNIX C compiler used the same format for 32-bit long integers. This ordering is known as PDP-endian.

UNIX was one of the first systems to allow the same code to be compiled for platforms with different internal representations. One of the first programs converted was supposed to print out Unix, but on the Series/1 it printed nUxi instead.

A way to interpret this endianness is that it stores a 32-bit integer as two little-endian 16-bit words, with a big-endian word ordering:

**Storage of a 32-bit integer, 0x0A0B0C0D, on a PDP-11**

| byte offset | 8-bit value | 16-bit little-endian value |
|:-----------:|:-----------:|:--------------------------:|
|      0      | 0B          |                            |
|      1      | 0A          | OAOB                       |
|      2      | 0D          |                            |
|      3      | 0C          | OCOD                       |