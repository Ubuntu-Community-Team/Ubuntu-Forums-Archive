---
title: "GRUB Error 2 on booting 1st time"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by xwing on 2006-03-28
Ubunteros,
 
System:
AMD 64 x2 4400+
ASUS A8N-E (nForce 4)
 
I just installed Dapper Flight 5 on my external USB 2.0 hard drive. The setup is as follows:
**/boot - 100 MB (primary)**
**/ - 22 GB (primary)**
***[COLOR=seagreen]--start of extended partition--[/COLOR]***
**swap - 4GB**
**Free unpartitioned space - 30 GB**
Windows Partition 1
Windows Partition 2
Windows Partition 3
***[COLOR=seagreen]--end of extended partition--[/COLOR]***
 
[COLOR=black]Do you guys see anything wrong with the above setup? The reason I ask is after installing ***perfectly***, the system reaches Loading Grub stage 1.5 and then craps out with an **Error 2**. [/COLOR]
 
[COLOR=black]Previously, I received an Error 18 the first time I installed, but then someone said that my /boot partition should be separate from / and should be inside the 1023 cylinder limit. (See [https://launchpad.net/distros/ubuntu/+ticket/441]("https://launchpad.net/distros/ubuntu/+ticket/441"))[/COLOR]
 
[COLOR=#000000]Grub Error 2 means "[Selected disk doesn't exist]("http://www.uruk.org/orig-grub/errors.html#stage1_5")". [/COLOR][COLOR=#000000]I can't, for the life of me, figure out the problem.[/COLOR]
 
[COLOR=#000000]Thanks![/COLOR]

---

### Post by queency on 2007-10-30
AMD64 , gusty

I got the same error after perfect installtion.

grub documentation says:
([http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html))
Error 2 : Bad file or directory type

---

### Post by netbandit on 2007-10-30
I had a somewhat similar situation on a system with SATA and IDE hard drives.  Grub would see them in one order, and Linux would see them in another order.

My only resolution was to edit the grub boot line (during boot time:  I think you press E) and try different drives (hd0,0, hd1,0) etc. until I got the one that worked.

It's not a clean solution, but once you figure it out you can edit your menu.lst to reflect the correct setting.

I've never tried USB drives, so my suggestion could be totally off.

good luck!
-nb

---

### Post by meierfra on 2007-10-31
post the output of "cat /boot/grub/menu.lst" and "sudo fdisk -l".

---

### Post by queency on 2007-11-05
qemu  worked perfect on amd64 
alittle slow but worked !
some friend of mind said i should install accelerator called kqemu

---

### Post by dustinkirkland on 2007-11-06
> **xwing said:**
> Ubunteros,
 
System:
AMD 64 x2 4400+
ASUS A8N-E (nForce 4)
 
I just installed Dapper Flight 5 on my external USB 2.0 hard drive. The setup is as follows:
...
[COLOR=#000000]Grub Error 2 means "[Selected disk doesn't exist]("http://www.uruk.org/orig-grub/errors.html#stage1_5")". [/COLOR][COLOR=#000000]I can't, for the life of me, figure out the problem.[/COLOR]
 



I, too, have an Asus motherboard, though with an Nvidia chipset.  I installed to an SD card, similar to your USB hard drive installation.  And I ran into the same grub "Error 2" problem.

This post led me in the right direction:
[https://answers.launchpad.net/ubuntu/+question/7137](https://answers.launchpad.net/ubuntu/+question/7137)

Which was toward the BIOS.  Since I had no IDE drives whatsoever, I disabled IDE various places in the BIOS, and that seemed to solve my problem.

---

### Post by TheOldWolf on 2008-02-02
Good morning.  (Trying to install linux has been a weekend warrior tradition for me...*Sighs*)

I previously had Windows Vista installed on my machine, and had two 500gb hard drives arranged in a Raid configuration.  (Not sure which one...not my expertise...)

I've booted from the Ubuntu disc, partitioned one of the hard drives, installed and rebooted.  (I *think* I installed it.)  There were no errors, until I rebooted.
> 
GRUB loading stage 1.5.



GRUB loading, please wait...
Error 2

When I went into the bios boot drives...it still lists them as being a single hard drive.  I imagine the problem is because Ubuntu is looking for one of the TWO physical drives...but only seeing one logical drive.  (Forgive me if the terms are wrong).  Since the one drive it sees doesn't look like the one it's looking for...well, ERROR 2!

Removed the Raid setup, and turned off DMA for the harddrives...works now.  Thanks!

---

### Post by soydeedo on 2008-03-09
> **dustinkirkland said:**
> I, too, have an Asus motherboard, though with an Nvidia chipset.  I installed to an SD card, similar to your USB hard drive installation.  And I ran into the same grub "Error 2" problem.

This post led me in the right direction:
[https://answers.launchpad.net/ubuntu/+question/7137](https://answers.launchpad.net/ubuntu/+question/7137)

Which was toward the BIOS.  Since I had no IDE drives whatsoever, I disabled IDE various places in the BIOS, and that seemed to solve my problem.

Boy am I glad I found this thread. I had almost given up. I was trying to install xubuntu 7.10 to a usb hd and later to a usb flash drive to see if it made a difference and I kept running into the same stinking errors.

Well like some others in this thread I started out getting error 18 which was remedied by placing a /boot partition within the first 1023 cylinders of my hd. After doing this, however, I promptly got the lovely error 2 instead and was at a loss. The flash drive of course went straight to error 2 since there aren't 1024+ cylinders on it to begin with.

Ok so finally I find this thread and went ahead and tried a couple new switches in the bios. By this point I had already tried plugging in the hd via an IDE cable and booting and that hadn't worked either. I had also tried setting it to LBA mode like some had suggested to no avail.

My next course of action was to follow the guidance quoted above and just disable IDE to see what would happen. I knew this wouldn't fly permanently, of course, since I DO use IDE drives, but it was worth a shot to see what would happen. Well what do you know...it worked.

[COLOR="Red"]**Semi-long story short, I found that I had my cd-rom jumper set to master. If I set it to cable select everything worked out fine.**[/COLOR] There was no slave attached, but there was one once so it must have been left from that. Windows had no issues with it so I had never taken the time to change it. I had noticed that a finnix livecd had hung on detecting my cd-rom before too, even though it still worked. That's kind of how I worked it out. But who cares about that, I can boot off the usb hd and the usb flash drive now!

Anywho, I hope this long story helps someone out. =)

PS - I have a DFI motherboard with an nForce 4 chipset.

---

### Post by wcorey on 2008-03-23
this is all very similar to my problem, installing ubuntu 8.04 beta on top of fedora8 in a striped lvm environment which i laid on top of a vista striped 2 sata drive environment. since the bios and the mother board jumpers worked fine as is with both vista and fedora 8 i don't understand the rationale to change the bios, dma, or hardware jumpers for ubuntu. what i did do that allowed the installed beta to boot was change the bios setting on both sata drives to non raid. however, it appears hardy now only sees sata 1 and not the second drive.

---

### Post by mkalen on 2008-06-04
> **xwing said:**
> Ubunteros,
 
System:
AMD 64 x2 4400+
 
[COLOR=black]Do you guys see anything wrong with the above setup? The reason I ask is after installing ***perfectly***, the system reaches Loading Grub stage 1.5 and then craps out with an **Error 2**. [/COLOR]



Similar problem with installing Hardy Heron 8.04 on a virtual AMD 64 machine in Citrix XenServer 4.1. Totally impossible to get around GRUB load error 2 by using the various device.map tricks described around the net (like hd(1,0), different /dev/sdX mappings etc).

Problem finally solved by selecting LVM-based install when re-installing from scratch.

It seems that installing Ubuntu in a virtual environment (without xe-guest-utils) is similar to using BIOS RAID - a situation where many people also have GRUB error 2 problems.

Maybe LVM can help RAID users too? It's the magic go/no-go for Xen at least.

---

### Post by dangbinh on 2008-06-10
I don't use RAID, but I receive this error also. The version I'm using is 8.04 Server.

I've tried changing HDD and CD jumper like someone suggested but it seems this tip can not solve the problem.

I've regconized that if I don't choose LAMP server, Mail server, OpenSSH server, Samba (it means choosing nothing in the dialog), this error will not appear.

If I choose, the error appears again.

Looking for solutions.

---

