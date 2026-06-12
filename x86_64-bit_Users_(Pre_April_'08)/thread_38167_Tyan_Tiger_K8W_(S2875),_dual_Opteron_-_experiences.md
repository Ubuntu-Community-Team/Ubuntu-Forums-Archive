---
title: "Tyan Tiger K8W (S2875), dual Opteron - experiences"
date: 2005-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by macsek on 2005-05-30
I'd like to share some experiences with concerning the Tyan Tiger K8W with dual Opteron CPU's.

1. USB hot plug not working: USB devices was not recognized when plugged in with ubuntu kernel (Bugzilla Bug 11235). I had to compile vanilla 2.6.11.10 kernel, which resolved the problem. :)

2. The hdparm -d 1 /dev/hdc did not work (permission error)---could not set DMA for CDROM drive (neither for IDE disks which tried later). I had to insert the amd74xx ide module into /etc/modules:

```

 ide-cd
 ide-disk
 **amd74xx**
 ide-generic
 lp
 mousedev

```
 
Now it works! (The amd74xx module has to be loaded before the ide-generic.) :)

3. SATA disks: we have two Seagate 7200.8 250GB disks connected to the mobo, they get recognised during the install and work great. And they are silent, too! :)

4. sensors... downloaded the appropriate sensors.conf from Tyan web site ([ftp://ftp.tyan.com/software/lms/lms_s2875.tgz)](ftp://ftp.tyan.com/software/lms/lms_s2875.tgz)), but could not get gkrellm working...  :? It needs further investigations.

5. We had second PCI video card (ATI Radeon 9250) beside the AGP one (Radeon 9100), but the installation failed it it was plugged in. I had to remove it to had the installation succeed. (I have not tried yet to use a second display.)

to be continued  ;-)

---

### Post by macsek on 2005-06-29
Well, this machine is usable overall, but there are too many segfaulting applications. :( 

The latest is ksCD, when I tried to set digital playback - it won't play just crashes or just freezes...

---

### Post by FrzzMan on 2005-06-30
woohoo... you have exactly the same motherboard as mine...

I'm using 2.6.11-xx (I don't remember the xx part, I'm on a Windoze machine) and the USB hot-plug works.

---

