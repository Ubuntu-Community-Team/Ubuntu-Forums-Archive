---
title: "[SOLVED] Office 2003 - Excel freezes"
date: 2008-05-01
forum: Wine
---

### Post by ChrisMP1 on 2008-05-01
I recently installed Office 2003 in Ubuntu 8.04. I had to copy a few DLLs over from a Windows installation. All is smooth sailing, except for Excel. Whenever I change a value in a cell that affects a formula, the program freezes. No errors are shown on the command line. Any ideas?

---

### Post by pepso on 2008-05-02
Exactly the same Excel problem here. :confused: Fresh installation of Gutsy and Office 2000.

---

### Post by AciiiD on 2008-05-15
Same here, I just upgraded yesterday evening, and now, Excel 2002 (aka XP) and Excel 2003 are freezing sometimes.

At first I though it was an add-ons problem, but I'm not so sure about it now.

Moreover, the freeze happens with the new wine, but also with the (not changed during gutsy upgrade) old crossover-pro 6.2.0-1 !!!

Weird, and definitly a stopper for me as I _need_ Excel for my work :\

Any ideas ?

---

### Post by AciiiD on 2008-05-24
bump!

---

### Post by alex-v on 2008-06-20
I found that the solver add-in was the culprit. I couldn't even disable it in Excel - it froze upon hitting OK button in add-ins window. I had to edit the user.reg file to remove all references to solver add-in. Now Excel seem to be working file even with lots of macros.

---

### Post by Huntington Coal Miner on 2008-06-26
I had the same problem but did not have the solver add-in installed. I am Wine that came with Crossover to run windows applications. I found this fix by codeweavers (makers of Crossover): 

[URL="http://www.codeweavers.com/support/wiki/CXOffice62_Ubuntu804dosmem"]

** Windows applications do not launch, or have started acting strange**.

Running Crossover on recent versions of Linux (in particular Ubuntu 8.04, Hardy Heron) may generate errors or warnings such as

*preloader: Warning: failed to reserve range 00000000-60000000 err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space*

and may refuse to run applications, especially ones that use Win16 or DOS calls. For instance, Microsoft Word 2000 will crash after a few seconds.

The workaround is to give the command:

sudo sysctl -w vm.mmap_min_addr=0

This fixes the problem until the next time you reboot. (It also reduces security slightly.)

To avoid having to give that same command every time you reboot, also edit the file /etc/sysctl.conf with the command

sudo gedit /etc/sysctl.conf

and change the line that reads:
vm.mmap_min_addr = 65536
to:
vm.mmap_min_addr = 0

That will apply the workaround for you when the system starts

This worked for Excel as well as Word.

---

### Post by ChrisMP1 on 2008-07-13
Wow - I had forgotten about this thread. THANK YOU so much! (Sysctl person.) Works perfectly. \\:D/ =D>

---

### Post by ssarkarhyd on 2008-08-19
Hi,

The solution for Excel did not work for me. Word, Powerpoint, Publisher, Access, Infopath, Groove all work except for Excel 2003

Any suggestions

---

