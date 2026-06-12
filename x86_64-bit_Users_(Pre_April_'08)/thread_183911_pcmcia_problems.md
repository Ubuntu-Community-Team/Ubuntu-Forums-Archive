---
title: "pcmcia problems"
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by dalabgator on 2006-05-28
I i was given this old ibook clamshell a little bit ago and i finally had a chance to put Linux on it.  My only problem that i have is that the pcmcia slot does not seem to work.  I would like some pointers to see if it is dead or not.  i am brorrowing a Zyair wireless card.  it uses the prism54 chip set and I do let a power light on the card when i plug it in.  

side not:  this card would normally not fit inside this ibook but i did some moding.  I took out the modem and the card fits fine in the slot.  any help would be great.

Thanks in advance.

---

### Post by jdp on 2006-05-29
The internal slot is **NOT** a generic PCMCIA slot.  It is an AirPort slot.  It is designed to have cards that have no antenna on the card to plug into.  Either a real Apple AirPort card, or a Lucent WaveLAN of some sort (Silver or Gold or a later Proxim/ORiNoCo/Agere, etc) will work.  There is also a certain Sony card taht can have the antenna removed and fit a function.  In general, you really want to use an actual AP card or a Lucent.

The AP card is a specially modified Lucent card, designed to work only in AP slots.

---

