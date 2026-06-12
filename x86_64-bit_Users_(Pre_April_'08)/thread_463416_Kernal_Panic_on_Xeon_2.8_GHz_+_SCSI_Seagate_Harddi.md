---
title: "Kernal Panic on Xeon 2.8 GHz + SCSI Seagate Harddisk"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by shashank314 on 2007-06-03
I tried xubuntu alternate installation on my HCL global infiniti line workstation with an old Xeon single core processor (2.8 GHz) and two SCSI Hardisks. The installation was not at all smooth and the system freezed quite often during the installation. 
During the installation upon pressing ctrl+alt+F4
I could see 

jun   3 19:54:30 kernal: [9769.722559] mptscsih: ioc1: attempting task abort! sc=f21cf800)
jun   3 19:54:30 kernel: [9769.722559] sd 5:0:0:0:
jun   3 19:54:30 kernel: 00 00 00 00 00 00
jun   3 19:54:30 kernel: [9769.722559] mptbase: ioc1: IOCStatus(0x0048):SCSI Task Terminated
jun   3 19:54:30 kernel: [9769.722559] mptscsih: ioc1: task abort: SUCCESS (sc=f6d5cb00)

there was a repetition of errors of the form 

  
After about 12 hours xbuntu 7.04 installtion was complete but after booting the computer I could see only the grub prompt.
I tried the following commands at the GRUB prompt

root (hd0,0)
kernel /vmlinuz root=/dev/sda1
boot

I got a kernel panic.

I would like to know whether installing a 64-bit version of Xubuntu may solve the problem or not. 
I would also like to know whether it will be a good idea to recompile the kernel. I have never recompiled the kernel before so I would like to know whether it is a worthwhile thing to do, before actually trying it.

---

### Post by RAOF on 2007-06-03
Installing a 64bit version of Xubuntu is very unlikely to help.  Those errors look a bit like the kernel thinks your SCSI system is dying in some way, although the actual text of kernel panic would probably be useful.

I'd suggest running a memtest, to check out whether the RAM's OK.

Since grub hasn't been installed correctly, it's a fair bet that some other part of the system hasn't been installed correctly too.

---

### Post by gaurab on 2007-06-05
Hi,
I did the memory test and the everything is fine. Even I thought that there might be some problem with the SCSI drive but I have two Hard disks on the system and both disks are giving the same problem. I tried keeping one of them unformatted and using only the other one. Are any extra drivers required for Seagate Cheetah 36 GB hard disks? Does anyone have any experience running Ubuntu on Seagate Cheetah 36 GB hard disks?

---

### Post by shashank314 on 2007-06-05
Sorry for the wrong login name in my previous post

---

### Post by RAOF on 2007-06-06
> **gaurab said:**
> Hi,
I did the memory test and the everything is fine. Even I thought that there might be some problem with the SCSI drive but I have two Hard disks on the system and both disks are giving the same problem....

Are they both attached to the same SCSI controller?

You also might want to check out [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) - particularly the "noacpi" and similar options.

---

### Post by shashank314 on 2007-06-11
I dont know. How does one check whether they are connected to the same controller. I tried the options acpi=off and ide=nodma. None of them helped. Is it a problem if they are connected to the same controller.

---

### Post by RAOF on 2007-06-12
> **shashank314 said:**
> I dont know. How does one check whether they are connected to the same controller. I tried the options acpi=off and ide=nodma. None of them helped. Is it a problem if they are connected to the same controller.

It's not a problem, it just might suggest that it is the **controller** which is faulty (if both drives show the same behaviour).

That said, it still could be a kernel bug.  In fact, a [quick google search](http://www.google.com.au/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Yix&q=mptscsih+task+abort&btnG=Search&meta=) suggests that it is a known problem in at least some versions of the driver in the 2.6.x kernels.

I would suggest filing a bug on launchpad.net against the "linux-source-2.6.*appropriate-kernel-revision*" package.  The "approprate kernel revision" is going to depend on what version of Ubuntu you are trying to install - it's 2.6.*15* for Dapper (Ubuntu 6.06), 2.6.*17* for Edgy (Ubuntu 6.10), and 2.6.*20* for Feisty (Ubuntu 7.04).

---

