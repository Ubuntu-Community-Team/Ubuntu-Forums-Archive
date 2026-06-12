---
title: "Dual Booting Xp Pro 64bit with ubuntu 8.04 64bit"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by TRDownShift on 2008-06-23
Hi, i've ben trying to setup dual partitions for the last two days and can't seem to pull it off T.T no matter what distro i try all the partitioning programs seem to fail in resizing my windows partition. I found this nice easy tut to help me dual boot ubuntu but it's not working out how it does in the tut and frankly.... the pissing the living F*^&ing S*^! out of me :P

You see in this ([http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)) tut it makes dualing boot look very easy.... but it isn't working out like that AT ALL.... >.> the biggest prob im having is this step > [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm) that top option to resize my partition isn't showing up and it stops me dead every time.

Any help would kick ***... i used to run linux and LOVED it but being a gamer i need winblows as much as it sucks, so i wanna dual boot. Though that seems as though it's going to be quite a B*%&!.... ah, im runing an AMD 64 dual core 4000+ live with a gig of ram and a Geforce 8400GS video card... oh... and my HDD is a 250GB Samsung if that helps at all.

---

### Post by uidb4056 on 2008-06-23
> **TRDownShift said:**
> Hi, i've ben trying to setup dual partitions for the last two days and can't seem to pull it off T.T no matter what distro i try all the partitioning programs seem to fail in resizing my windows partition. I found this nice easy tut to help me dual boot ubuntu but it's not working out how it does in the tut and frankly.... the pissing the living F*^&ing S*^! out of me :P

You see in this ([http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)) tut it makes dualing boot look very easy.... but it isn't working out like that AT ALL.... >.> the biggest prob im having is this step > [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm) that top option to resize my partition isn't showing up and it stops me dead every time.

Any help would kick ***... i used to run linux and LOVED it but being a gamer i need winblows as much as it sucks, so i wanna dual boot. Though that seems as though it's going to be quite a B*%&!.... ah, im runing an AMD 64 dual core 4000+ live with a gig of ram and a Geforce 8400GS video card... oh... and my HDD is a 250GB Samsung if that helps at all.

First of all it's important to know how many partitions are on your HD because there is a limit of 4 primary partition or 3 primary and 1 extended.

Second instead to choose install from liveCD as showed in your link (second menu option) you have to choose the first one "Try ubuntu without any change to your computer", this will let you first check your hardware compatibility and second you can start GPARTED under menu System->Administration (Partition Editor), with it you can verify how and what type of partitons you have resize them as needed, ...

A good link for dual boot you can read is [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by kuja on 2008-06-23
Also, be sure you're not using any sort of compression/encryption options on the NTFS filesystem or it won't work.

---

### Post by TRDownShift on 2008-06-23
ah, i tryed Gparted.... though i think it's messed up :P as i just got the computer last month and theres no way my HDD is messed up >.> im going to try what it told me to do and see if it works. -.- *sigh*

---

### Post by TRDownShift on 2008-06-23
I'm back :P


yeah..... it didn't work.... i have new screen shot too -.-

This blows.... it seems winsh!t will fight to the bitter end on this >.> 

Oh, and theres nothing wrong with my hard drive, the windows scan didn't show any probs >.>

If it comes down to it i WILL kill winSh1t.... i'll back up my 100+GB's of data and format this b1tch.... then we'll see what windodo can do >.> F*^&en B$%#@#$ bill should burn in hell >.>

---

### Post by old_geekster on 2008-06-23
You know, I have two $50, Hitachi Deskstar 80GB HDD's in my rig.  On one I have XP Pro 32-bit and the other Hardy Heron 8.04 64-bit.  I have no problem with booting from either one.  This is how I recommend that you do a dual-boot.  You should install Windows first, then Hardy will setup accordingly.

---

### Post by TRDownShift on 2008-06-24
thats how mine is setup, im on windows right now :P have ben sense i got the computer. iut's just not working for some reason i cant comprehend.... T.T

I don't know, i don't want to reformat this drive because it would take time to get all my settings back so what im thinking is i might just wait till i have some extra cash and buy a second HDD.

Thanks guys, but somehow i think if i don't reformat this will end up over my head to fix, so im just going to wait and buy a second hard drive >.>

---

### Post by retiree on 2008-06-24
I am running Xp Pro 64 bit and Hardy 8.04 64 bit with almost the same setup you have and I had little problems setting it up.Did you defrag your harddrive  before you installed Hardy? If you have had this computer a long time it probably needs to be defragmented. That might be a help to you.
Cheers

---

### Post by cariboo on 2008-06-25
If I have to install XP and dual boot I usually let Windows have less than half of the hard dirve. Once you get to the windows patitioning softwarte, delete all the partitions and then let the software create a partition that takes up half of the hard drive space, and leave the rest unpartitioned. When I install ubuntu I have this area on the hard drive that is ready to be partitioned the way I want it, and no need to fool around with different partitioning software.

Jim

---

### Post by phlembob on 2008-06-25
Hi, My machine is loaded with XP Pro x64 and Ubuntu 8.04 64 bit on the same SATA HDD.  I don't remember any problems other than deciding the size of partitions so I installed using the Ubuntu default partition size.  Ubuntu calculated the needed size left for the XP and it is less than 20gig. I remember answering Ubuntu's questions only.  Don't be discouraged, take your time --- read each alternative.  You may need to only investigate before moving forward.  Good Luck and keep jamming :guitar:

You have 2 HDDs.  I previously installed on separate HDDs, which worked fine, but I had one SATA HDD w/ Ubuntu and one IDE HDD w/ XP Pro x64. I may have found a programming bug between SATA and IDE both as Masters, but by placing the jumper on the IDE to slave eliminated IDE identification problem.  After you get your dual boot up (grub installed through Ubuntu automatically), you will want to write on either HDD.  Ubuntu 8.04 LTS can be updated with ntfs-3g program to use both NTFS and sda/hda formats to store your info.  You can do it!  Stick with it.

---

### Post by Kevbert on 2008-06-25
You may have problems partitioning due to the Windows paging file towards the end of the disk.  If you run up the default defrag program you should be able to see this block of data.  To turn this off you need to go into Settings - Control-Panel - System - Advanced tab.  Now click on Performance Settings and then the Advanced tab.  Click on Change under Virtual Memory and set No paging file.  Click on Set and OK.  Close all windows boxes.
Now when you go to Programs - Accessories - System Tools and select the Disk Defragmenter and run it at least once.  The old paging file data block will go and the end of the disk will be empty (ready for repartitioning).  Once you have installed your new OS you can re-enable the paging file.

---

