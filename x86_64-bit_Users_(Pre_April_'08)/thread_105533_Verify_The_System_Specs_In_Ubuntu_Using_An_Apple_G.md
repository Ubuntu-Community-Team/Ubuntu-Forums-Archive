---
title: "Verify The System Specs In Ubuntu Using An Apple G3 Computer"
date: 2005-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by gconn77 on 2005-12-18
Hello everyone... I just got Ubuntu 5.10 installed successfully on my Apple G3 B&W Computer....

Now... in Windows,  you right click on My Computer to view your processor speed and the amount of memory installed....

How do you do this in Ubuntu?

---

### Post by gruepig on 2005-12-18
You can find a lot of information from System -> Administration -> Device Manager.

You can also access all of this information from the command line.  /proc is a special filesystem that allows you to access a bunch of kernel information.  Use 'cat' (short for concatenate) to read any of the files in proc.

 'cat /proc/cpuinfo' will tell you about the processor.  'cat /proc/meminfo' will tell you about the memory (as will running 'free' or 'top').  In /proc/pci, you'll find information about PCI devices.  For a list of mounted partitions, see /proc/mounts (or run 'mount' or 'df').  Etc.

---

### Post by MonolithTMA on 2005-12-18
Applications / System Tools / *System Monitor* will give you some good info too.

---

