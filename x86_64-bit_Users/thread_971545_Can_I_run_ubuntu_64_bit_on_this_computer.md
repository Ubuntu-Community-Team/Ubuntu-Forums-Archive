---
title: "Can I run ubuntu 64 bit on this computer?"
date: 2008-11-05
forum: x86 64-bit Users
---

### Post by mannaa on 2008-11-05
Hi all!
I have recently bought a new laptop, FSC amilo pi3540. My question is if this computer should be able to operate wih a 64 bit OS(meaning of course ubuntu 8.10), with the hardware installed on it. [http://www.komplett.no/mlf/produkt/diverse/FSC/Amilo/2008_Q3/ds-AMILO-N-Pi-3540%20-%20CCE_NOR-110138-001.pdf]("http://www.komplett.no/mlf/produkt/diverse/FSC/Amilo/2008_Q3/ds-AMILO-N-Pi-3540%20-%20CCE_NOR-110138-001.pdf") The link is to the product sheet of the computer. Looking at the hardware, should I be able to install and run ubuntu 8.10 64 bit?

Thank you[COLOR="Black"]****[/COLOR]

---

### Post by hyper_ch on 2008-11-05
Does it have:

- a mainboard that supports 64bit?
- a cpu that supports 64bit?

If yes, you can run a 64bit OS.

---

### Post by mannaa on 2008-11-05
thank u hyper for the fast reply. Intel core 2 duo P8400 should support 64 bit. But I know nothing of the motherboard. The chipset are pm45 + ICH9M. Does it say something?

---

### Post by pansz on 2008-11-05
Yes, PM45 obviously has no problem supporting 64bit CPU.

In fact, the easiest way to check whether your system is for 64-bit is to insert any 64-bit live-cd (the ubuntu 8.10 64bit desktop cd is one of those) and boot it. If the CD can boot, then your system support 64bit, if the CD cannot boot the your system does not.

---

### Post by felker2 on 2008-11-05
As pansz says: the best way is to just boot the 64-bit Ubuntu 8.10. Download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I expect no 64-bit problems, cosidering the Intel Wifi and Realtek Audio chipsets: I think they have open-source, and thus 64-bit, drivers.

---

### Post by mannaa on 2008-11-05
Thank you all for the replys. I burnt the CD, and it loads while in windows and when I reboot the system it boots in to the installation meny. But then there is problem, when I choose to install or run ubuntu without changes etc, the system reboots once again, and after start up it enters the installation meny once more. The same thing happens over and over. I have already posted this issue on another thread. Here is the link [http://ubuntuforums.org/showthread.php?t=963907&highlight=mannaa]("http://ubuntuforums.org/showthread.php?t=963907&highlight=mannaa") 

So far none of the suggestions have helped. If anyone has the time and knowledge to give me anymore tips I would be thankful.

---

### Post by mannaa on 2008-11-10
bunmp

---

### Post by dabl on 2008-11-10
It sounds like there is something hokey with your hardware there (and unrelated to "64-bit", by the way).  Choosing an item on the menu of the Live CD should not trigger a reboot, if things on the computer are working correctly.

Things to look at:

1. BIOS -- should be set to boot first from CD, then hard drive.

2. Optical drive -- does it seem to work correctly, in any OS?  Plays audio CDs without error?  Shows data on data CDs?  Can it boot any other Live CDs, like Knoppix or GParted or sidux, for example?

3. Live CD quality -- did you verify the md5sum on the downloaded ISO image file?  Did you burn it at 4X speed, DAO mode?

4. Other hardware problems?  Rum memtest86 overnight to verify memory is working.

---

### Post by dptxp on 2008-11-10
You can try any other 64-bit OS (live CD).

---

