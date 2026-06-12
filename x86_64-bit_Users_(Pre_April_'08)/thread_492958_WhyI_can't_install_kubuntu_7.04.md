---
title: "WhyI can't install k/ubuntu 7.04 ???"
date: 2007-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ippo 2001 on 2007-07-05
Hi to everybody, I tryed to install Ubuntu and Kubuntu 7.04 to my workstation but it doesn't go on after the first part where you can choice what to do.
this is my configuration:

Intel Quad 6600
Asus P5B deluxe
XFX7600GT XXX
A-data 2x2GB pc5300
Samsung 320GB SATAII 16MB
NEC 7173A (IDE)

please help me, i need to install linuxin order to work with openfoam...

here are some other information given to other guys in " Absolute Beginner Talk":

> **splintercellguy said:**
> So you're stuck after the LiveCD menu, is this correct? What happens after you select Install Ubuntu?

thanks for your help, with k/ubuntu 7 the sistem freeze after about 20 seconds while there is the scrolling (I don't know the correct name) is moving. 
please forgive my bad english.

p.s. sometimes I can see little artefact during this procedure. I'm sure this isn't an hardware problem I used this machine with windows xp64bit and I have no problem. I made also some test (memtest and orthos) to verify if the sistem is stable.


> **beniwtv said:**
> The black screen you get after the scolling bar is normal, I get that too on the LiveCD.

How long did you wait for it to boot up? Also, does the CD-Drive stop reading at some point?

the problem is that the sistem freeze during the process while the scrolling bar is moving . how can I explain what happen. After I select to install k/ubuntu the process start and appear the scrolling bar with a slider that move from left to the right and from right to left. during this movement of the slider the sistem freeze.

 this is the best way I have to explain what happens.



> **djchandler said:**
> Is this the 64-bit version of Kubuntu you are trying to install? Is this going to be a dual boot system?

yes, I'm trying to make a dual boot system, the Hard drive is divided in 3 part 40GB for XP 64bit, 30GB are not formatted for linux, and the remaing space is formatted in NTFS file system for storage.

> **djchandler said:**
> Your motherboard and processor combination is *way* out on the bleeding edge compared to most of us. You are going to need to find someone with similar hardware. If you are installing the 64-bit version, you may need to also post in the 64-bit discussion group. one more question. What is the chipset on the motherboard? :o

can you give me the link of the 64-bit discussion group?  the motherboard ha an intel 965P chipset.

> **djchandler said:**
> PS Before you give up, try version 6.06, Dapper.

I tried the 6.06 but I have some similar problem.

---

### Post by bigken on 2007-07-05
have you tried it in safe mode you could also give the alternate cd a try

---

### Post by Ippo 2001 on 2007-07-05
> **bigken said:**
> have you tried it in safe mode you could also give the alternate cd a try

I tryed in the safe mode, but no results at all ... tomorrow I'll try with the alternate cd, can you explain what's the different between the desktop version and the alternate one ?

---

### Post by bigken on 2007-07-05
the desktop you can run the os from the cd the alternate installs in a dos like enviroment

---

### Post by jespdj on 2007-07-05
So you have an Asus P5B and 4 GB RAM?

Try booting with the following kernel parameter: agp=off

(You can specify kernel parameters somewhere in the boot menu when you boot off the Live CD).

Do a search in the forums here for "Intel P965", there seems to be a problem with the kernel which incorrectly detects the P965 chipset as a G965 (with integrated graphics) and this can be a problem if you have 4 GB RAM.

See this very useful thread: [ Installing Ubuntu with 4GB of RAM](http://ubuntuforums.org/showthread.php?t=375853)

---

### Post by Ippo 2001 on 2007-07-05
> **jespdj said:**
> So you have an Asus P5B and 4 GB RAM?

Try booting with the following kernel parameter: agp=off

(You can specify kernel parameters somewhere in the boot menu when you boot off the Live CD).

Do a search in the forums here for "Intel P965", there seems to be a problem with the kernel which incorrectly detects the P965 chipset as a G965 (with integrated graphics) and this can be a problem if you have 4 GB RAM.

See this very useful thread: [ Installing Ubuntu with 4GB of RAM](http://ubuntuforums.org/showthread.php?t=375853)

thx very much I'll follow your suggest even if I no access to kernel input the system freeze before this step

---

### Post by Ippo 2001 on 2007-07-06
ok I tryed with kubuntu 6.06 alternate and I don't have the problem I had before, but during the first process of installation it doesn't recognize the cd.rom and ask me for driver from cd-rom. where can i found them.
the correct name of the dvd-rw is OPTIARC DVD RW AD-7173A (ide version)
thx

---

### Post by jespdj on 2007-07-06
Did you try the agp=off kernel parameter or not? You can specify that somewhere in the boot menu on the live CD. Or don't you get to see the menu at all?

Is your CD-ROM connected to the IDE controller or to a SATA interface? The P5B motherboard uses the Intel P965 chipset which does not have its own IDE interface. Because of that Asus put a separate IDE controller on the motherboard, the JMicron controller.

The Linux kernel in Ubuntu 6.06 has a bug, so that it does not recognise the CD-ROM if it is connected to the JMicron controller. So, you cannot boot Ubuntu 6.06 from CD-ROM if you have this setup. You will need to use a SATA CD-ROM drive or use a newer version of Ubuntu.

---

### Post by Ippo 2001 on 2007-07-06
> **jespdj said:**
> Did you try the agp=off kernel parameter or not? You can specify that somewhere in the boot menu on the live CD. Or don't you get to see the menu at all?

no i didn't select agp=off.

> **jespdj said:**
> Is your CD-ROM connected to the IDE controller or to a SATA interface? The P5B motherboard uses the Intel P965 chipset which does not have its own IDE interface. Because of that Asus put a separate IDE controller on the motherboard, the JMicron controller.

The Linux kernel in Ubuntu 6.06 has a bug, so that it does not recognise the CD-ROM if it is connected to the JMicron controller. So, you cannot boot Ubuntu 6.06 from CD-ROM if you have this setup. You will need to use a SATA CD-ROM drive or use a newer version of Ubuntu.

yes my cd rom is connected to the jmicron. I tryed with the 7.04 and I solve this problem. But I have another problem, during istallation the process stops at 85% and seems don't go on even if I wait 5 or 10 minute for example.

---

### Post by Ippo 2001 on 2007-07-06
ok the system go further 86% and complete the installation but it isn't stable and rebbot everytime

---

### Post by marwooj on 2007-07-17
> **Ippo 2001 said:**
> ok the system go further 86% and complete the installation but it isn't stable and rebbot everytime


The same for me :-(

---

### Post by Ippo 2001 on 2007-07-17
> **marwooj said:**
> The same for me :-(

this is very strange, on the other side I have the same problem with other linux OS for example CentOS open suse and so on ... I can't belive it

---

### Post by jespdj on 2007-07-17
> **Ippo 2001 said:**
> no i didn't select agp=off.



yes my cd rom is connected to the jmicron. I tryed with the 7.04 and I solve this problem. But I have another problem, during istallation the process stops at 85% and seems don't go on even if I wait 5 or 10 minute for example.
So why did you not try the agp=off kernel boot parameter?

Do you think for some reason that that's not a good idea or do you not know how to set it? There is an option in the boot menu of the CD to set boot parameters.

---

### Post by Ippo 2001 on 2007-07-17
> **jespdj said:**
> So why did you not try the agp=off kernel boot parameter?

Do you think for some reason that that's not a good idea or do you not know how to set it? There is an option in the boot menu of the CD to set boot parameters.

No unfortunatley i didn't find the way to select agp=off in the kernel menu. At the end I installed but the systen went on rebboting ...

---

### Post by jespdj on 2007-07-17
[list]
[*]Put the Ubuntu CD in your CD/DVD drive.
[*]Reboot so that your computer boots from the CD.
[*]You will see a menu. Press **F6** (Other Options).
[*]Type: agp=off
[*]Press Enter.
[/list]
Note that there is also F1 (Help) in the menu, where you can find information on all the possibilities of the boot menu from the CD.

---

