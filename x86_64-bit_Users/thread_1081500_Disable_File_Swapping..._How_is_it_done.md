---
title: "Disable File Swapping... How is it done?"
date: 2009-02-26
forum: x86 64-bit Users
---

### Post by Patt on 2009-02-26
I built a 64 bit machine and am still in the process of configuring it using Ubuntu. I am new to linux so please dumb it down a bit for me because I am not proficient with the terminal commands yet. I would like to disable the file swapping so that my system utilizes more of my ram. How would I go about doing this?

- 2x EVGA 01G-P3-N959-TR GeForce 9500 GT 1GB 128-bit GDDR2 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card 

- AMD Athlon 64 X2 5600 Brisbane 2.9GHz Socket AM2 65W Dual-Core Processor Model ADO5600DOBOX

- ASRock K10N750SLI-110dB AM2+/AM2 NVIDIA nForce 750a SLI ATX AMD Motherboard

- 2X (8 GB total) OCZ Platinum 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual

- Ubuntu 8.10 64bit (Whichever is the default on download currently)

- Mythbuntu

---

### Post by smani on 2009-02-26
What do you mean with file swapping? If you mean the swap parition:
It is not because you disable swapping that your system will use more ram - the system will use as much ram as it needs and only if it there is no space left will start writing to swap - you can monitor the usage of the swap partition in the device manager. I really do not recommend turning off the swap partition..

---

### Post by Patt on 2009-02-26
> **smani said:**
> What do you mean with file swapping? If you mean the swap parition:
It is not because you disable swapping that your system will use more ram - the system will use as much ram as it needs and only if it there is no space left will start writing to swap - you can monitor the usage of the swap partition in the device manager. I really do not recommend turning off the swap partition..
You are correct I meant the swap partition, but as I understand it the swap partition on most OS is used by default and the memory is allocated based on what the program needs in order to operate. TomsHardware had a [article]("http://www.tomshardware.com/reviews/vista-workshop,1775.html") on improving Vista performance using this method. I would like to see how it effects linux. If there is no swap partition the entire program is written to RAM and should increase performance. Assuming Linux allocates memory in a similar fashion to windows.... That phrase being said I don't care for any debate on the preference of linux over windows. I'm here aren't I?

---

### Post by issih on 2009-02-26
First some reading that might be interesting:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you still really want to play with it just do this:

```
swapoff -a
```

to turn it off, and then:

```
swapon -a
```

to turn it on again, more details can be found here - [http://linux.die.net/man/8/swapoff](http://linux.die.net/man/8/swapoff)

Hope that helps

---

### Post by smani on 2009-02-26
The problem is how windows swaps: it creates a swap file which does not even have fixed size, which in no time results in a disaster concerning harddisk fragmentation and so on. Usually the best thing on windows is to fix the swap parition size (put minimum equal to maximum). Linux is totaly different here, there is an entire parition that does not influence the other file system only for swapping. Therefore, you will not see any advantage here by disabling swap. Additionally, allthough I admit that with 8 GB this is somewhat unlikely, if you did run out of ram, without a swap partition your system would probably behave quite oddly at best, probably crash. Swap is used as a last resort to avoid allocation errors, and it gives you the chance to emergency-kill the program that is eating up all your ram before the system crashes, losing all your possibly unsaved data.

---

### Post by Patt on 2009-02-26
Thank yall for the info, this is really helpful.

---

### Post by Yellow Pasque on 2009-02-26
You can control the swap behavior of the kernel with swappiness, but most desktop users will want to leave this alone. Linux does a much better job than Windows at managing virtual memory. [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by kevmitch on 2009-02-26
I use gkrellm system monitor which among other useful things has a swap monitor. It tells you how much is in use and the swap in/out rate. If you run that for a while while you're using your system you'll probably find that the swap is pretty much never used unless you actually run out of RAM.

---

