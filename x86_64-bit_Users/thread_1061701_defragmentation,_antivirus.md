---
title: "defragmentation, antivirus"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by jayanramesh on 2009-02-06
Dear buddies,

My(our) ubuntu 8.1 intrepid ibex 64 bit now started running bit slow on my system. Are there any defragmentation software and antivirus available?.And what are the possible factors which cause this? Please, can anyone solve this prob.?
My system is -intel core 2 duo E8400-3 ghz
               MB              DG 35EC
               RAM (800MHZ)    2GB

THANK YOU.
JAYANRAMESH
KOMBAI
TAMIL NADU 
INDIA

---

### Post by cometa2k7 on 2009-02-06
There are no defragmentation programs that I know about - Linux doesn't suffer the same problems as Windows with it's filesystems.

Antivirus would be pretty much a useless piece of software - you don't need it because there are so few viruses (if any).

I can't diagnose an exact problem, but perhaps this will help you a little.

You can always try 'top' in a terminal - that will tell you what processes are using your system resources the most.

Or you can go to: 'System > Administration > System Monitor' - that will also show what's using your system, and allow you to close unneeded processes.

---

### Post by Svensk023 on 2009-02-06
If you're still worried about viruses however, go to add/remove applications and search for "virus scanner" and that will get u one

---

### Post by jespdj on 2009-02-06
Defragmentation and viruses are Windows things. Forget your Windows habits - Ubuntu is a different operating system that doesn't need defragmenting and because of the way security is set up on Ubuntu, it's (almost) impossible to write viruses for Ubuntu.

Here's a recent tread with more info:
[http://ubuntuforums.org/showthread.php?t=1055797](http://ubuntuforums.org/showthread.php?t=1055797)

---

### Post by jayanramesh on 2009-02-06
Dear COMETA 2K7,SVENSK023
THANK YOU SO MUCH FOR YOUR GUIDANCE.I FOUND TWO VIRUSES AND GOT IT REMOVED BY THE HELP OF VIRUS SCANER.

THANK YOU,
JAYANRAMESH

---

### Post by lakersforce on 2009-02-06
But your viruses was proberly Windows viruses and thus have no performance penalty on the Linux kernel.

---

### Post by jayanramesh on 2009-02-06
May be you are right -lakersforce

---

### Post by hyperdude111 on 2009-02-06
> **jayanramesh said:**
> May be you are right -lakersforce

He is right.

Because the linux kernel is completley different from the windows NT kernel in every way all these windows viruses do not affect linux, the fact they are there does not mean the actually do anything.

2nd Because linux uses EXT3/EXT4 for its filesystem instead of the windows NTFS filesystem linux does not need to be defragmented.

---

### Post by hyper_ch on 2009-02-06
neither defragmentation nor antivirus is needed on linux

---

### Post by donkyhotay on 2009-02-06
A slow ubuntu system is usually a result of extra services being loaded. Best option is to find out what services are being launched and confirming whether or not you need them.

---

