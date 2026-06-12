---
title: "Dual monitors on power g4"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by august on 2005-11-30
Hi,

I have tried to search for a solution, but as I don´t really know what to look for, I need to ask here..!

How can i get my dual monitors to work? It seems like there are some sort of connection: during boot, the second monitor has a grey background and displays:

[COLOR="Gray"]copying of device tree ... done
initializing fake screen NVDA,Display-a
calling quiesce
returning 0x00130000 from prom_init[/COLOR]

But as soon as the boot is done, and X starts up, the second monitor is all wierd colors and stuff.

Right after X starts up, it seems like the second monitor has a badly distorted version of the text displayed during boot.

Then, on something that seems a random cue, the monitor once in a while change from this to all sorts of wierd colors, seemingly random patterns etc.

Can anyone please help? I have a Nvidia GeForce4 MX, on a AGP bus. It seems like it is regarded as a PCI card in what I can manage to get out of the xorg.conf file (that is the X config, isn´t it?). The main monitor is on a ADC port with a ADC to DVI connector cable, the second monitor is directly on the DVI port on the card.

Anyone?


I wish things were a bit more plug and play on linux..!

---

