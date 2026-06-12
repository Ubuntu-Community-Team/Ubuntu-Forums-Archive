---
title: "Installing in Multi Boot System"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by RedDuck on 2005-12-17
Hi, I'm about to install Ubuntu-AMD64 in a Multi Boot System using a third part bootmanager. The bootmanager (Bootstar, highly recommended!) shows two partitions in the Master Boot Record  at this time (reserved for Ubuntu), other partitions are currently not shown. What I would like to know is how the installer behaves. Does is automatically install in the reserved partitioned space, or does it by any chance use (and thus mess up) the unpartitioned space on my disk (which is not realy unpartitioned, just not shown in the MBR at this time)? Which  installation option should I use to accomplish this neatly?

Thanks.

---

### Post by Suger on 2005-12-17
The "manually decide the partitions" or whatever, should be the last but one.

---

### Post by RedDuck on 2005-12-17
Okay, but being new to this distribution, do I need the 'linux' or 'expert' option at the start of the installation to be able to get to the 'partition'-question?

---

### Post by linbetwin on 2005-12-17
Just press ENTER to begin the installation and you should reach the partitioning screen.

---

### Post by RedDuck on 2005-12-17
Tnx, that's what I needed...

---

