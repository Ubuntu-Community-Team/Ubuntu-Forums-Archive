---
title: "Corrupt files after simple copy - even on ramdisk"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by grisi on 2008-07-05
Hello,

few days ago I installed Ubuntu 8.04 (amd64) on my new PC. It seams to run very stable inclusive running VMware (I had no operation system crash at all) but some suspicious things happend. I could reduce to problem as follows:
1) copy a big file (200MB or 1GB) to the same disk
2) compare the copy with the original using md5sum -> there is a difference in about 50% of the tries when copying 1 GB (lower rate when copying smaller files)
3) no error messages on the console or in /var/log/messages
4) this problem happens on a local disc (ext3), on an external USB disk (vfat) and on a ramdisk.
5) I had the same behavior when booting the rescue system of the Ubuntu 8.04 Alternate CD with i386 and with amd64 (with text console only)
6) It seams to be that the problem is while writing. Reading the files seams to work because running md5sum several times on the same file provides always the same result (even with cleaning the cache in between).
7) I check the RAM with Memtest86 v1.70 - everything was fine.

My hardware config:
* Linux version 2.6.24-16-generic (64bit)
* Intel Q6700 quad core CPU, 2.66 GHz, stepping 0b
* mainboard Gigabyte GA-P35-S3G (F2) with Intel chip set P35 and ICH9
* 8 GB RAM (1066 MHz)
* 1TB hard disk

Can anybody give me a hint?

Thanks in advance

grisi

---

### Post by Yellow Pasque on 2008-07-05
Can you feel the north bridge and south bridge heatsinks while the system is in operation? If Gigabyte is anything like MSI, they use cheap thermal pads on these chips, and the P35 uses a good bit of power too. Make sure the heatsinks aren't too hot and are mounted tightly.

---

### Post by grisi on 2008-07-06
Hi,

thanks for the answer. I check the heatsinks - they seam to be mounted correctly but were quite hot. I used a big fan to cool them down - but the corruption didn't disapear.

I also reduced the number of used CPUs with kernel parameter "maxcpus=1" because I had the idea that I could have to do with multi core processing: with one CPU probability of data corruption seams to be reduced, but the bug is still there.

Any ideas?

grisi

---

### Post by soxs on 2008-07-06
Did you try to copy files from ramdisk to ramdisk? If that will still give you corrupted md5sums, it is atl east no hard drive failure. The fact that the og. messages don't show any errors doesn't really help, could be a mainboardboard defect (one of these black things might be blown up, this happens especially on somewhat older mainboards > 2a)
Another idea would be to check if fedora/gentoo/debian have the same issues, and if they don't try reinstallin ubuntu from scratch.

---

### Post by grisi on 2008-07-08
> Did you try to copy files from ramdisk to ramdisk?
Yes. I tries ramdisk->ramdisk and hard disk->hard disk, both operations lead to corrupt files.


I checked out several distributions - here is my result:
* Ubuntu 8.04 amd64(installed on disk): problem occured
* Ubuntu 8.04 amd64 (booted from Alternate CD without X): problem occured
* Ubuntu 8.04 i386 (booted from Alternate CD without X): problem occured
* Ubuntu 8.04 amd64 (booted from Live CD): problem occured
* Fedora 9 x86_64 (booted from Live CD): problem occured, system crashed quite soon
* Fedora 8 i686 (booted from Live CD): problem occured, system crashed quite soon with system log entry "Kernel: Buffer I/O error on a^@^@^@^@..."
* Windows XP 32bit (without service pack, no mainboard specific drivers except for network card): everything works fine!


Do I have to use Windows XP now?

Thanks for any hint in advance,

grisi

---

### Post by Robstarusa on 2008-07-09
Have you run a memtest on your memory?

Also: Check the specs on your ram for correct voltage. Some BIOS's either misdetect this or undervolt.

I'd run the memtest for _at_least_ 48 hours.

---

### Post by grisi on 2008-07-31
Hi Robstarusa,

sorry for my late response - I was on holiday.

With your hint I found the problem: after about 24 h runnung memtest without any error I got the first error message. Only the test type "5" was affected. Then I was trying out the different combination of my 2*2 DIMMs and found the bad DIMM. 

Maybe the problem also has to do with the wrong voltage because I had two DIMMs with 2.1V (as printend on the DIMM) and two with 2.2V. One of the 2.2V DIMMs was the bad one, andt my mainbord only seams to detect 2.1V ...

Now I'm running the PC with 4 GB and everything works fine. I hope this remians unchanged when I upgrade to 8 GB with new DIMMs.

Thanks a lot!

grisi

---

### Post by soxs on 2008-08-01
Plx mark as solved

---

### Post by sake on 2008-08-02
Thank you for your post! I had exactly the same problem on my new system, your post helped me in finding the culprit (one pair of memory strips having problems).

My hardware config:
* Intel Q6600 quad core CPU, 2.40 GHz
* mainboard Gigabyte GA-P35-DS4 with Intel chip set P35 and ICH9
* 8 GB RAM (800 MHz 4-4-4-12)
* 150GB 10k-RPM WD Raptor
* 4x Samsung 750GB in RAID5

I now run on 4GB RAM until the bad strips are replaced.

---

