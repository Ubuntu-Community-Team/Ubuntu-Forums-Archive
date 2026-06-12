---
title: "Best SATA-II controller for RAID in 6.06 Server x64"
date: 2007-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Matzu on 2007-05-25
Dear forum-members,

I am building a VMWare Server host, and plan on using 6.06 LTS x64 (I could go for either 6.10 or 7.04 if necessary, but would prefer to stick with the LTS release). The mainboard is P5M2 which has 4x SATA, but I need to add 8 SATA-II harddisks (WD raid edition). I plan on using two RAID 10 arrays two maximise performance and reliability.

I could do one of the following:

1) Use a compatible 8 port PCI-X SATA RAID board like the 3Ware 9550-SX and configure drives as two RAID 10 sets for max performance + reliability.

2) Get a 4 port SATA-II (preferably PCI-X) and use Linux Software RAID to configure the disks.

My questions are:

a) Is two RAID 10 sets the best way to use the eight disks?

b) Which of 1) and 2) are preferable, and which controller card should I get? I am looking for a good price/performance option, but I am willing to spend a reasonable sum to get a good solution.

Your advice and experience in this matter is greatly appreciated! :D

---

### Post by Tilo on 2007-05-31
I would recommend to use RAID-6 

the question is if you want to use software RAID or hardware RAID..  how much money do you want to throw at this? 

I recommend getting a cheap SATA-II controller card, and use software RAID6.

[http://www.excaliberpc.com/Supermicro_8-port_SATA-II_Card/AOC-SAT2-MV8/partinfo-id-553538.html](http://www.excaliberpc.com/Supermicro_8-port_SATA-II_Card/AOC-SAT2-MV8/partinfo-id-553538.html)

---

