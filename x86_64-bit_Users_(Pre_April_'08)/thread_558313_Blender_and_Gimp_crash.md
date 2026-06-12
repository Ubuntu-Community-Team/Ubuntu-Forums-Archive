---
title: "Blender and Gimp crash"
date: 2007-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by nixi on 2007-09-23
Hello 64 bit users! 

I am rendering a 3d model with Blender/Yafray, but the renderings tend to crash under FeistyAMD64. Here are a couple of messages from the system log: 

[COLOR="Sienna"]Sep 20 23:46:55 [username]-desktop kernel: [ 7243.109827] blender-bin[14911]: segfault at 00002a9eb4211fb0 rip 00002aaaae65eaa9 rsp 000000004097cbe0 error 4

Sep 22 01:42:39 [username]-desktop kernel: [12359.876952] blender-bin[19750]: segfault at 00000001fffffffc rip 00002ab26bcff268 rsp 00007fff43987f00 error 4[/COLOR]

Both messages were copied after Blender/Yafray crashed. Also the image editor Gimp crashed in a similar manner (but I haven't had time to try to reproduce it for getting a system log message).

I hope someone here can help me understand those messages, and perhaps find a solution. 

Hardware: 
CPU  AMD 5600+ (two cores)
Mobo  Asus M2N32WS (nf590)
DDR2  2 GB Corsair twin...
GPU  Nvidia Quadro FX 1500
HD  WD Raptor 150 GB (2 partitions: Feisty64 and XP)

On the same computer I also have a partition with Windows XP 32 bit, and when using it and the corresponding version of Blender/Yafray the 3d model renders without crashing (albeit slower than on Feisty). 

Therefore it seems the problem is in the 64bit operating system; not in the hardware. The 3d model also renders without crashing on an old P4 computer with Feisty 32 bit...

When the programs do not crash rendering is very fast with Feisty, or with Linux in general.


Regards, Nixi


P.S. The program versions are  Blender 2.44 and 2.45, and Yafray 0.0.9.

---

