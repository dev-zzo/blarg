---
title: "Deprocessing attempt 3"
date: 2024-07-28
---

Greetings and salutations! Today I am attempting to deprocess a third sample of [Siemens M1327A3](https://siliconpr0n.org/archive/doku.php?id=infosecdj:siemens:m1327a3), hopefully with more success than previously. I thought I'd take notes while I am at it. Recapping the previous attempts...

Sample 1 was ruined due to unevenness and over-etching: some of poly was already etched away while parts of passivation oxide were not removed from the top.

Sample 2 was kinda okay, with some of the metal getting etched away in a controlled manner. However, apparently due to the prolonged use of NaOH(aq) in an attempt to etch more metal and oxide away, poly got also damaged. Most importantly, only about half of metal got etched away.

# Preparation

The ingredients are:

* "Red ceramic etch" containing HF, to attack the passivation silicon oxide layer on top of the die
* NaHCO3(aq) in decent concentration, to neutralise the etchant
* NaOH(aq) in an arbitrary but decent concentration, to attack aluminium metal when it gets exposed
* HCl in decent concentration (I used 30%), to etch the metal away
* Water in a squirt bottle for washing the slide and sample
* A microscope to inspect the process

![Red ceramic etch packaging](/blarg/assets/20240728/red-ceramic-etch.jpeg)

**DANGER**: compounds containing HF are toxic for living organisms (that means YOU). Observe all required precautions when handling them.

Note that NaOH gets hot when being dissolved; prepare it in advance so it can cool down to a comfortable temperature.

# Execution

I followed this schedule:

* First run: 60s of etching
* Subsequent runs: 20s of etching
* Final run: 15s of etching
* About 60s in NaOH(aq) to see if metal has been reached

The etchant, a translucent gel, is applied to the sample so that the die is covered uniformly and without bubbles, and the countdown starts. When the countdown is close to the end, the sample is transferred to a beaker with NaHCO3(aq) to quickly neutralise the etchant. The sample is then washed with water and transferred to a beaker with NaOH(aq). After that, the sample is washed again and inspected to decide if another run is necessary.

I judged the passivation etching to be good enough after all metal traces have started getting eaten away by NaOH(aq).

![Image of metal getting etched away starting at vias (500x mag)](/blarg/assets/20240728/deproc1.jpg)

When that point was reached (about 2min 40s total etch time), I switched to the HCl solution to finalize the etching. Previously I attempted to use NaOH(aq) for etching off the metal completely as well, but it seems it was too aggressive for poly and attempted to etch it away as well. The expectataion is that HCl will only attack metal.

After about 15 min in HCl:

![Image of metal getting etched away (500x mag)](/blarg/assets/20240728/deproc3.jpg)

The die will be left in HCl until all the metal is dissolved. However, long wires may be a challenge.

![Image of metal NOT getting etched away (500x mag)](/blarg/assets/20240728/deproc4.jpg)

# Analysis and conclusions

Depending on the oxide thickness, the first and subsequent runs may need to be shorter. Handling less than 10s runs is challenging though.

The passivation oxide layer was not etched completely. Due to apparent unevenness of this layer or unevenness of the etchant, it seems risky to continue etching beyond the point where metal is reachable on the sharp edges where oxide was the thinnest. After all, this is how the sample of attempt 1 was ruined.

Etching with pure HCl is rather slow; need some way to speed it up. Adding H2O2 resulted in a lot of unpleasant gas coming out of solution; working outside is highly recommended. But it did seem to quicken the process somewhat.

Etching metal in long wire runs is rather slow. This is because etchant has to travel all the way and be present in enough concentration while being constantly consumed. Recall the oxide layer is still present on top of the wire.

Overall, this time the majority of metal was removed without damaging any other structures. This is as close to a success in deprocessing as I ever got to date.

Until next time!

XOXO,
/DJ
