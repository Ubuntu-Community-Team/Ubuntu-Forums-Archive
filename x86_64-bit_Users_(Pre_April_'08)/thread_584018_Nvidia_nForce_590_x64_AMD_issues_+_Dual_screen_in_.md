---
title: "Nvidia nForce 590 x64 AMD issues + Dual screen in Gutsy / Feisty ..."
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by MiiJaySung on 2007-10-20
Has anyone here managed to have much luck with the SATA support built into the NForce 590?

Specifically, I have issues installing Feisty (using 32bit) and Gutsy (x64) on my machine. Firstly the system used to hang while booting early on. I found noapic got round this and more recently a BIOS flash has managed to stop most of these messages.

Having got past that, the normal Live CD will not install. It generally screwup when dealing with partitions. I believe dodgy SATA drivers are to blame here. I had this with my last motherboard (Via KT800 based I think) and this current motherboard (nForce 590 based M2N32 WS Pro). To install, I've managed to get round this through the clever use of VMware for the install stage. However I still find occasionally when running outside of VMware I get issues with the harddisk. Normally large copy operations trigger this and when doing this in txt mode (i.e. on TTY1) I get a register dump / stack trace of some sort relating to the SATA related issues. I get a bit further using the alternate install CD because the GFX card and other GNOME issues don't seem to appear, however again I get partitioning issues.

I have a Marvell SATA controller as well as the Nvidia SATA controller, which I might try. However I'm put off by using this as I've seen that many people have issues with this, especially Windows users who need the special boot driver to install this.

Like I said my motherboard is a ASUS M2N32 WS Pro, which I brought because I saw from reviews (Albeit mainly Windows based tests) that this board was a good relieable and solid performer and that it had been out a year now, long enough I would have thought for driver issues to be ironed out good support to be about. Also, ASUS supposedly are supposed to be good motherboard manufacturers.

I see there are many posts related to this, but none seem to have any definate answer. Most of them seem to have a reply saying something like "check your install CD is OK etc", or add the noapic option. 

Has anyone got anoy other solid suggestions based on experience or know of any alternative drivers etc. Currently I am having to use Ubuntu via VMware from Windows, running it full screen on my secondary screen, which is not ideal as it's much slower, not to mention I'd rather have Windows running in VMware, and make use of the hardware accelerated effect in Compiz etc, if everything was stable enough.

---

