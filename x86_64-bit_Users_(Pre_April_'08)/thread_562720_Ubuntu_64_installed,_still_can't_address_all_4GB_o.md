---
title: "Ubuntu 64 installed, still can't address all 4GB of RAM"
date: 2007-09-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by notaname on 2007-09-29
Hi there...

I installed the 64-bit version of Ubuntu (7.04), have a 64-bit CPU, but my computer is still only addressing 3.2GB out of my installed 4GB.

I'm pretty sure it's not BIOS-related, because the BIOS lists 4GB as available.  

Here are the uname, lshw and meminfo outputs to illustrate my situation.  I've also attached dmesg's output (archived b/c of attachment size limitations), if it'll help.

Do you have any ideas?  Any help would be greatly appreciated!

dan@dyna:~$ uname -a
Linux dyna 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
dan@dyna:~$ sudo lshw -C CPU
Password:
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
       slot: Socket 775
       size: 1998MHz
       capacity: 4GHz
       width: 64 bits
       clock: 333MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
dan@dyna:~$ cat /proc/meminfo
MemTotal:      3348948 kB
MemFree:       2657396 kB
Buffers:         12784 kB
Cached:         266052 kB
SwapCached:          0 kB
Active:         333556 kB
Inactive:       189104 kB
SwapTotal:     4000144 kB
SwapFree:      4000144 kB
Dirty:              64 kB
Writeback:           0 kB
AnonPages:      243888 kB
Mapped:          64720 kB
Slab:            33828 kB
SReclaimable:    13072 kB
SUnreclaim:      20756 kB
PageTables:      11408 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   5674616 kB
Committed_AS:   531848 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     16160 kB
VmallocChunk: 34359722107 kB

---

### Post by dcstar on 2007-09-29
> **notaname said:**
> Hi there...

I installed the 64-bit version of Ubuntu (7.04), have a 64-bit CPU, but my computer is still only addressing 3.2GB out of my installed 4GB.

I'm pretty sure it's not BIOS-related, because the BIOS lists 4GB as available.  
..........B

What happens if you add:

```
mem=4000M
```
to the end of your Grub boot string?

---

### Post by notaname on 2007-09-29
> **dcstar said:**
> What happens if you add:

```
mem=4000M
```
to the end of your Grub boot string?

Hrm...  I still only get 3.2 GB.  Thanks for the idea, any others?

---

### Post by ptn107 on 2007-09-29
My machine does the same thing.  I have 2Gb (2097152k) installed, but Ubuntu only sees 1.9Gb (1944936k).  The BIOS also reports I have the full 2Gb.  What I found was that Ubuntu never sees the full amount because a BIOS setting tells the os to share some ram (approx. 128mb [131072k]**) with my video card.  You may have the same situation and not know it (I didn't for quite a while).

**The math doesn't quite add up though, but that's what's going on. 2097152k-194936k=152216k, meaning 20.6mb (21144k) is unaccounted for :(.

---

### Post by |Eric| on 2007-10-01
there is a few reasons why you would not see the full 4 Go 

1- as said kernel not set to see  4Gb
2- as said shared mem from graphic card 
3- Cheap un Even memory (yes it can happen ) meaning: they advertise 4Gb but its just an aproximate ... or 3. somthing instead of 4x1024Ko 
ie: you got screwed !

4- PCI yes PCI ! to access some device the system maps some  adresses to the uper 4Go so you end up with less mem you usualy have to enable a remap of that pci adresse range, an option in the bios 


5- aliens just ate your memory bars...

---

### Post by auquicu on 2007-10-04
> **notaname said:**
> 
I installed the 64-bit version of Ubuntu (7.04), have a 64-bit CPU, but my computer is still only addressing 3.2GB out of my installed 4GB.

I'm pretty sure it's not BIOS-related, because the BIOS lists 4GB as available.  

       product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
 


I had the same problem. This solved it:
Go into the BIOS (press DEL) and switch Advanced->Chipset->North Bridge Configuration->Memory Remap Feature to Enabled. Now both BIOS and Linux report 4GB.

---

