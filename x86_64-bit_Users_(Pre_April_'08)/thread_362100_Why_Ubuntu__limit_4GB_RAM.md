---
title: "Why Ubuntu  limit 4GB RAM"
date: 2007-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by marcusbb on 2007-02-15
Hi,
We bought new server and we want to run Ubuntu 64 bit on it. We started with 4GB RAM and it was working. When we add 6GB to 10GB Ubuntu crashed during booting.
Then we  start it from GRUB with mem=4048M and it work.
The question is what shell we do make it working with 10GB. Bio can see all 10GB RAM.
According all information I got it seems that 64Bit kernel have build in support for 64GB RAM. 
When we was trying to build own kernel than there was not "High memmory support " in xconfig menu.
Please help 

Marcus

---

### Post by aim on 2007-02-15
was it a -generic or a -k8 kernel? try with -k8!

---

### Post by cmost on 2007-02-15
Check out this post:

[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

---

### Post by koshcu on 2007-02-15
The 64bit version works just fine with more then 4GB of ram. I currently run 8GB of ram in an S2915 board with dual opteron 2218s. Just run the standard 64bit kernel and that is all that is needed.

Are you sure you are running 64bit edgy?

linux-image-2.6.17-11-generic  That is the current kernel I am running and it is working just fine.

An easy way to test if you are running a 32 or 64bit system is by running

python -c "import sys; print sys.maxint"
If the number is 9223372036854775807 you are running 64bit, if it is smaller then that you are running 32bit.

---

### Post by marcusbb on 2007-02-15
The machine have Xeon CPU.

---

### Post by patrickfromspain on 2007-02-15
Having xeon cpus doens't mean they are running 64bit ubuntu.

---

### Post by marcusbb on 2007-02-15
Yes I have 64bit system. I burned 64bit  installation and the kernel is 64bit.
I found more out that the problem could be ATI FIREGL V3100 PCIExpress card or somethink else.
When I booted with iommu=off option than System booted without problems. But I do not think is the best solution.
What is your suggestion?

Marcus

---

### Post by koshcu on 2007-02-15
Could you please run

python -c "import sys; print sys.maxint"

and post what number you get?

---

### Post by marcusbb on 2007-02-15
9223372036854775807

/Marcus

---

### Post by koshcu on 2007-02-15
That is so strange, you have a 64bit system running in 64bit mode and it won't access more then 4GB of ram. However others of us here are running more then that with no issues at all. I did not even configure a single thing and it worked.

On a 64bit platform there is no need for building in support for high memory, that is only needed on 32bit systems so there is no reason to rebuild the kernel.

linux-image-2.6.17-11-generic  That is the kernel you should be running.

---

### Post by marcusbb on 2007-02-16
It is only working when I start with iommu=off option.
Installation from the dvd also hangs, therefore the only solution is to take away rest off the RAM install system with 4GB RAM. After installation add the rest of the RAM and start with  iommu=off option.
Does it have to do with ATI FIREGL PCI express card, or it have nothing to do with graphic card.  iommu - need more information.

The machine I have is HP XW8400 with 10GB RAM and ATI FireGL V3100 PCI express Graphic card, and last BIOS from the 1 February 2007.

Marcus

---

### Post by panholt on 2007-02-16
Have you tried messing with the memory remapping settings in the BIOS?

---

### Post by Shay Stephens on 2007-02-16
Anyone consider bad ram?

---

### Post by marcusbb on 2007-02-16
RAM is okay. It is working with  iommu=off option. Tested ram for 24 hours and it is okay.
There no posibilty to change any such things in HP bios.

Marcus

---

### Post by Princey on 2007-02-19
> **marcusbb said:**
> RAM is okay. It is working with  iommu=off option. Tested ram for 24 hours and it is okay.
There no posibilty to change any such things in HP bios.

Marcus

ATI cards tend to be flaky under linux, I don't know why. It's a long short here, but if you have an nVidia card lying around, try it and see. The boot problems you talk about, I got it with 1GB of memory as well. And guess what, I use an ATI X600 PCI Express video card. Thinking of ditching it for an nVidia with all the issues I'm having with it.

---

