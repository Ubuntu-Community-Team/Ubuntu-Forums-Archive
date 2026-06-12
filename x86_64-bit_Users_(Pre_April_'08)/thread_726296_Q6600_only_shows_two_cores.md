---
title: "Q6600 only shows two cores"
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jim Stickney on 2008-03-16
I just got a Q6600 quad core and a Gigabyte GA-EP35-DS3R motherboard.  I'm only seeing two cores,  I get the attached output from the command dmesg | grep CPU

Any idea what's wrong?  How do I tell if they forgot to put half of the blue smoke into my CPU?


[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Initializing CPU#0
[   25.759322] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   25.839821] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.839889] CPU: L3 cache: 4096K
[   25.839927] CPU 0/0 -> Node 0
[   25.840002] CPU: Physical Processor ID: 0
[   25.840040] CPU: Processor Core ID: 0
[   25.840082] CPU0: Thermal monitoring enabled (TM2)
[   26.222281] Initializing CPU#1
[   26.299099] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.299100] CPU: L3 cache: 4096K
[   26.299101] CPU 1/1 -> Node 0
[   26.299103] CPU: Physical Processor ID: 0
[   26.299103] CPU: Processor Core ID: 0
[   26.299108] CPU1: Thermal monitoring enabled (TM2)
[   26.299525] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   26.299628] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   26.320024] Brought up 2 CPUs
[   26.320122] CPU0 attaching sched-domain:
[   26.320130] CPU1 attaching sched-domain:
[   26.367113] Switched to high resolution mode on CPU 0
[   26.368037] Switched to high resolution mode on CPU 1
[   27.158987] ACPI: Processor [CPU0] (supports 8 throttling states)
[   27.159100] ACPI: Processor [CPU1] (supports 8 throttling states)

---

### Post by wheredidrealitygo on 2008-03-16
do a ```
uname -a
``` and tell us what kernel it comes up with. SMP (symmetric multi-processing) or "multi-core" boxes need an SMP kernel.

I have the same processor and my 'uname -a' comes up with: Linux andy-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

You may need to switch to the 'generic' kernel.

---

### Post by Wiebelhaus on 2008-03-16
> **wheredidrealitygo said:**
> do a ```
uname -a
``` and tell us what kernel it comes up with. SMP (symmetric multi-processing) or "multi-core" boxes need an SMP kernel.

I have the same processor and my 'uname -a' comes up with: Linux andy-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

You may need to switch to the 'generic' kernel.

Same here.

---

### Post by Jim Stickney on 2008-03-16
I dont' think that's it, when I run 

```

uname -a

```
I get
Linux bender 2.6.24-12-generic #1 SMP Wed Mar 12 22:31:43 UTC 2008 x86_64 GNU/Linux

Plus, its finding two of the four cores.

---

### Post by fjgaude on 2008-03-16
You are running Alpha Hardy and that could be the issue. Even updates to Alpha 6 is not complete yet.

Have you tied to see what System Monitor says of your installation? In System/Adminstartion and on the extreme left menu item of System Monitor.

Have you tried Gutsy?

---

### Post by Jim Stickney on 2008-03-16
Actually, I tried Gusty first, and had the same problem.  Also, the System monitor is only showing two cores.

---

### Post by fjgaude on 2008-03-16
> **Jim Stickney said:**
> Actually, I tried Gusty first, and had the same problem.  Also, the System monitor is only showing two cores.

You have the latest BIOS for your mainboard? I can't remember when it came out but maybe before the quads. Many here have reported four cores with various Gigabyte boards, and Asus ones too.

Go to:

[http://www.gigabyte.com.tw/](http://www.gigabyte.com.tw/)

and navigate to your board and see if you have the latest, likely not, eh?

Also, from where did you acquire your CPU?

---

### Post by Jim Stickney on 2008-03-16
I already flashed the latest version of the BIOS, and I double checked that my motherboard supports the CPU. 

I got the OEM CPU from New Egg--it came only with the bare chip.

---

### Post by fjgaude on 2008-03-16
Send it back, and ask for another one... I think you got a dual-core remarked as quad. Just my opinion.

P.S. When you boot up does the BIOS show a Q6600, a quad, and at what speed?

---

### Post by Jim Stickney on 2008-03-16
Ya, I think I'll try to get another one.  Such a pain.  

It does show up as a quad core in the BIOS.  From what I understand the Q6600 is two dual cores in a single package.  Maybe one of the two cores was defective.

---

### Post by fjgaude on 2008-03-16
It does looks that way, defective, so Egghead will certainly honor your request for a replacement.

---

### Post by Yellow Pasque on 2008-03-16
> **Jim Stickney said:**
> Ya, I think I'll try to get another one.  Such a pain.  

It does show up as a quad core in the BIOS.  From what I understand the Q6600 is two dual cores in a single package.  Maybe one of the two cores was defective.
That kind of leads me to believe the problem isn't with the CPU, but I guess if you're willing to pay shipping, no problem with trying another.

---

