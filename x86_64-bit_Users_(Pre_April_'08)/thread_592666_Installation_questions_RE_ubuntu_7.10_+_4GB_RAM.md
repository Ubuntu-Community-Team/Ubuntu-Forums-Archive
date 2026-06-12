---
title: "Installation questions RE ubuntu 7.10 + 4GB RAM"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by SimonHF on 2007-10-26
I've tried running Ubuntu 7.10 on an Intel Core Duo P5B motherboard with 4GB RAM + an NVidia GeForce 7950 graphics card with 1GB on-board memory. When 64bit Ubuntu boots and I run 'top' then it only reports about 2.5GB of usable RAM. Is the calculation as follows: 4GB - 1GB - a bit more for other IO = 2.5GB? If so then is there a way to use the nice graphics card and somehow get closer to 4GB of RAM being available to Ubuntu?

---

### Post by dabl on 2007-10-26
I don't think the 2.5G "usable" reported by top is all of the RAM that Ubuntu recognizes.  I run Kubuntu so I'm a little fuzzy on where you look, but somewhere in the Ubuntu System menus you have a "hardware information" utility that will show the memory situation on your hardware -- it should reflect the "4GB" which is indeed 4 billion bytes but turns out to be only 3.7M kilobytes (1k = 1024 bytes).

As far as "sharing" with the Nvidia card, I think that 1GB of memory is available to the GPU on the card, but I haven't heard that you can make it available to the CPU.  That sounds like a problem because the PCI bus is not running at the same speed as your main memory bus to the CPU -- not sure how that would work.  :neutral:

---

### Post by Eberbachl on 2007-10-26
I'm afraid that I can't be much help, except to say that my system seems to recognise my 4GB RAM no trouble:

[quote=top]Mem:   4052160k total,   901988k used,  3150172k free,[/quote]

Specs: Ubuntu 7.10 AMD64 - AMD Athlon 64 bit 4000+, 4GB DDRII RAM, Nvidia Geforce 7200 GS 128MB video.

---

### Post by ian dobson on 2007-10-27
Hi,

Try going into the BIOS have enabling the option "memory remapping" or "memory relocation". I had the same problem with 4Gb on my Asus p5B plus until I enabled this option (I can't remember exactly what it's called).

Regards
Ian Dobson

---

