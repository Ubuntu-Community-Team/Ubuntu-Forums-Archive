---
title: "RT61 wi-fi card and Feisty 64 bits"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fredtoy on 2007-09-20
I bought a new machine recently and it has a 64 bit processor (Athlon 64 X2 4400+). I just installed Feisty 64 bits on it to give a try. Now, I can´t get my D-Link DWL-G510 wi-fi card to work. Feisty detected it just fine as a RT61 card (it has a Ralink chipset). But, my system started freezing so badly that I barely could install Feisty. After doing some research, I found that the RT61 driver has a bug with multiple core CPUs. I blacklisted the RT61 module and the system stoped freezing. With Feisty 32 bits I could get a workaround with ndiswrapper and the card worked fine. I tried the same workaround in Feisty 64 bits, but, could not find a 64 bit Windows driver to use. Anyone here have the 64 bit driver for Windows or managed to get this card working in Feisty 64 bits with an Athlon X2 CPU?

Sorry for any bad english (not my native language) and thanks.

---

