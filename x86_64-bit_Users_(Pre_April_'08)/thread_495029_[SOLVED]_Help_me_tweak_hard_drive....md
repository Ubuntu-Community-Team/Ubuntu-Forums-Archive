---
title: "[SOLVED] Help me tweak hard drive..."
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-07
Okay, so I'm really liking ubuntu a lot on my main system.  No wireless headaches.  I've got the instructions on how to tweak my HD for a write-back cache.  I uses this on the kids computers and the speed up was great.

I need to know a couple of things.

1) I have several HD's in this system.  How do I find out which drive (hda, hdd1, etc...) is the linux drive that I need to tweak?

2) how do I determine that my drive (or all of them for that matter) are set with DMA enabled?

Thanks...

---

### Post by John.Michael.Kane on 2007-07-07
To determine what the partition is called and what file system it is running use the command below
```
sudo fdisk -l
``` 

To check for dma stats use this command, and replace hda with the letters that correspond to your drive
```
sudo hdparm -i /dev/hda 
``` 


Also heres three guides. That may help with what you wish to do.
[HOWTO: Speed Up Your Hard Drives]("http://ubuntuforums.org/showthread.php?t=459101&highlight=hard+drive+speed")
[HOWTO: Tweak your ext3 file system for a performance boost]("http://ubuntuforums.org/showthread.php?t=107856&highlight=hard+drive+speed")
[HOW TO: get a free speed boost from your hard drive]("http://ubuntuforums.org/showthread.php?t=24416&highlight=hard+drive+speed")

Hope this helps.

---

### Post by crjackson on 2007-07-07
**Okay - so what am I doing wrong here?**

charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm -I /dev/hdd |grep DMA:
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm –c1 /dev/hdd
–c1: No such file or directory
charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm -I /dev/hda |grep R/W multiple sector transfergrep: multiple: No such file or directory
grep: sector: No such file or directory
grep: transfer: No such file or directorycharles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm -I /dev/hda |grepUsage: grep [OPTION]... PATTERN [FILE]...Try `grep --help' for more information.charles@K8N-Neo4-Platinum-SLI:~$

---

### Post by crjackson on 2007-07-08
charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm -I /dev/hdd |grep DMA:
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm &#8211;c1 /dev/hdd
&#8211;c1:** No such file or directory**
charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm -I /dev/hda |grep R/W multiple sector transfergrep: multiple: **No such file or directory**
grep: sector: No such file or directory
grep: transfer:** No such file or directory**
charles@K8N-Neo4-Platinum-SLI:~$ sudo hdparm -I /dev/hda |grepUsage: grep [OPTION]... PATTERN [FILE]...Try `grep --help' for more information.
charles@K8N-Neo4-Platinum-SLI:~$

---

### Post by crjackson on 2007-07-09
**[SIZE="3"]Any ideas what I'm doing wrong here?[/SIZE]**

---

### Post by John.Michael.Kane on 2007-07-09
> **crjackson said:**
> **[SIZE="3"]Any ideas what I'm doing wrong here?[/SIZE]**

Might help if told us which one of those guides your using.

---

### Post by crjackson on 2007-07-09
This is where I started, but as you can see I didn't get very far...

[http://ubuntuforums.org/showthread.php?t=459101&highlight=hard+drive+speed]("http://ubuntuforums.org/showthread.php?t=459101&highlight=hard+drive+speed")

---

