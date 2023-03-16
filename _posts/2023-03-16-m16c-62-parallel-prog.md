---
title: "Mitsubishi/Renesas M16C/62 group: parallel I/O programming"
date: 2023-03-16
---

Hello there, it's been a while now. Sorry about that, as usual, life happens.

Today I wanted to write down an important tidbit pertaining to a rather arcane and outdated piece of Japanese tech, namely the M16C/62 group of 16-bit microcontrollers authored by Mitsubishi engineers, and its "parallel I/O programming" mode of operation. While self-programming and serial I/O programming are rather well explained [in the manual](https://www.renesas.com/us/en/document/mah/m16c62-group-users-manual), the parallel programming mode description is unfortunately omitted:

```
In this mode, the M16C/62 (flash memory version) operates in a manner similar to the flash memory
M5M29FB/T800 from Mitsubishi. Since there are some differences with regard to the functions not avail-
able with the microcomputer and matters related to memory capacity, the M16C/62 cannot be programed
by a programer for the flash memory.
Use an exclusive programer supporting M16C/62 (flash memory version).
Refer to the instruction manual of each programer maker for the details of use.
```

Compare that to, say, group 28:

```
In parallel input/output mode, the user ROM can be rewritten by a parallel programmer supporting the
M16C/28 group. Contact your parallel programmer manufacturer for more information on the parallel pro-
grammer. Refer to the user’s manual included with your parallel programmer for instructions.
```

Some light was shed by a [datasheet](https://web.archive.org/web/20200216123623/https://www.mqp.com/ad558.htm) for programming adapters (used to be) made by a certain MQP Electronics. This datasheet generously provides a complete pin mapping from their programmer to M16C pins! What a stroke of luck. Unfortunately, they only ever made an adapter for this specific family and none of the others (I asked).

Looking at the pin mapping, there are several interesting points:

* The /RESET line is tied to VSS, so the CPU core should not be running in this mode at all
* Pins brought out indeed correspond to M5M29FB/T800
* D15/A-1 is brought out on P2.0 instead of P1.7 for some reason, but this seems to click with the subsequent address pins being brought out on P2 as well
* Address pins go from P2 onwards and sequentially
* /RP and CE are on the pins documented in serial I/O programming mode
* /OE, /WE, /BYTE are also on P5, with /CE

This may or may not apply to other groups/families.

A lingering question is, if nothing is running, how does the code readout protection mechanism work then?.. Some power-on sequencing?..
