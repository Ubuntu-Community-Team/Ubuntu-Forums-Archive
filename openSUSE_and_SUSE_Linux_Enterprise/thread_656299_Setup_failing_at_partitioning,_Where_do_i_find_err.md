---
title: "Setup failing at partitioning, Where do i find error codes?"
date: 2008-01-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by bartos on 2008-01-02
Motherboard P5B-E, Hard drives all SATA

When installing 10.3, it fails at portioning with an error -12004. Deleting device mapper volume /dev/mapper/isw_cebghifaf_XP
XP is my first drive (sda) and also where I load grub so I can't disconnect it or format it.
It also shows my SDC as a raid when it is not and won;t allow me to make a mount point for it.

I would really like to install 10.3 as I have used SUSE before and would like to use it again.
So any help would be appreciated.

Thanks
B

---

### Post by RedDwarf on 2008-01-02
I have a P5B and works without problems. But I put the SATA controller in AHCI mode, not IDE emulation (that is less efficient, but up to where I know needed to run Windows XP).

---

### Post by bartos on 2008-01-02
Thanks
I have setup also to AHCI mode but that is a normal fix for not seeing cdrom.It is the harddrives that I am having trouble with.

---

