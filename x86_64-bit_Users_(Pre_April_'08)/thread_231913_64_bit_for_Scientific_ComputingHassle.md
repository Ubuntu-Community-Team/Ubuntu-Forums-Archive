---
title: "64 bit for Scientific Computing/Hassle"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattyj on 2006-08-08
Hello,

I work at a kids hospital and we are doing finite element modeling of defibrillation in kids which requires a pretty fast system and alot of memory.  I have been using Ubuntu 32 bit on a Pentium D and could not be happier, but I think performance would greatly benefit from a 64 bit machine.  I am concerned about compatibility however, and don't want to order a system and not be able to use it easily.  I am an end user with a physics and engineering background looking to model, not spend too much time hacking with the OS.  We were thinking a mac, but with it not being full 64 bit until Spring 07 and ubuntu being so stellar we are looking hard at Ubuntu 64 on a fast machine.

Questions:
1:  We are looking to get a dual opteron system or dual Xeon(Woodcrest) system with a nVidia 7900GTX video card.  Something like this:

AMD Opteron 200 Series Processor 2 x AMD Opteron 270 2.0GHz - HyperTransport - Dual-Core - 2MB Cache
 
AMD Opteron Processor Heatsink Standard Heatsink
 
AMD Opteron 200 Series Mainboard - Fully Custom Tyan Thunder K8SE S2892G3NR - mainboard - SSI EEB 3.0
 
DDR ECC/Registered Memory 4 x Crucial 1GB PC3200 400MHz DDR ECC Registered
 
PCI Express or Integrated Video MSI nVidia 7900GTX 512MB GDDR3 PCI Express ( 2xDVI )
 
All Cases Lian-Li PC-60 ATX Chassis - No PS (Silver)
 
EPS Power Supply Antec TruePower 2.0 TP2-550EPS12V - power supply - 550 Watt
 
3.5" Drive(s) 1.44Mb 3.5" Floppy Drive Black
 
5.25" Drive(s) Sony 16x DVD+/-RW Dual Layer
 
Hard Drives 250GB Serial ATA 7200 RPM - Seagate Barracuda 7200.9
 
Data RAID Level - 1/5/50 No HDD RAID
 

Are there any issues installing the drivers, or is it as easy as 32 bit?

2:  Are there any other pitfalls for a system like this?  I am mostly compiling code from source and will primarily be using it for modeling and visualization. I am not as worried about Realplayer not working etc.
3:  Are there as many packages for 64 bit ubuntu, i.e. can you just click in synapic and get things like cmake etc that make your life easier?

I would greatly appreciate your expertise. I really enjoy working  with ubuntu so far and greatly appreciate the efforts of those who help create it.

Thank You,

mattyj

---

### Post by RAOF on 2006-08-08
1) All those drivers should be as easy to install (those that you need to) as in 32bit Ubuntu

2) Apart from Flash, Realplayer, and Wine, there's not much that doesn't work exactly as in Ubuntu32.

3) See point 3.  Kilz has checked out the repositories; there's something in the order of 100 packages less for AMD64, out of ~13,000 (from memory).  Anything that you need will be in the Ubuntu64 repositories :)

---

### Post by milia on 2008-04-21
You can also install 32bit programms in your 64bit OS without (many?) problems.

How? You'll have to download drivers supporting 32bit programms.

That's how I run 32bit Firefox, skype on Ubuntu 7.10 64bit @ my Intel core2 duo 1.67GhZ laptop.

I was wondering about some benchmarks for 64bit OS's, just to check out in which calculations
they're faster than 32bit OS's.

A friend told me that BOINC could be 15-20% faster in 64bit OS...
We'll see..

(I just wonder what happens with other calculations as huge matrix diagonalisations or monte carlo methods..)

---

