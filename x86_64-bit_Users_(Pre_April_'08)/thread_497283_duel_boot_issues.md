---
title: "duel boot issues"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bullsmack on 2007-07-10
hello,
i am trying to install fiesty 64 bit as a duel boot with my 86 xp . when i try to use ubuntu to make the partition it gives me an error when i get to the 4th step and it doesnt mater which option i choose(ive tried them all. then i tried partition majic 8.0 to make the partition. i read that linux runs faster when its before xp on the drive. well when i tried that with partition majic it worked until it rebooted to install linux( i choose the install a new operationg system option in partition majic). on all acounts it totally destroyed my xp so it woudnt boot at all . even though with the partition majic it was still going to install linux. i mean both messages werre on teh screen at the same time. the one where it was begining the install of linux and the one where ther was an error loading xp. how is that possible for it to let me knwo that there is an error loading xp while it was trying to install ubuntu?
 

the next question i have is..... can i make linux first on the drive since xp is already there? i know that partition majic warns about older MS operating systems wont work when you try that. but it did not include xp in that list. and i know that this version of partition majic is for xp so wouldnt it have included it if it woudlnt work? also there is a warning in partition majic that says that if you dont instal the ubuntu imediately then it would make my existing one inoperable. so WHEN do i put the disc in to install linux? before in restarts or after? or should i just put it in before i click to run the tasks i picked?  also . partition majic wants to make the linux a ext2 file primary. and the instal option in ubuntu tries to make it a ntfs by default. so which is right? partition seems to NOT even give the option for a ntfs . IM LOST NOW FOR SURE.

is the main issue here that since i already have xp loaded first i cannot make ubuntu first on the drive and move xp that far over on the drive?  and i did check the integrity of the disc before i even tried to install it

---

### Post by OldAlgis on 2007-07-10
re: dual boot.
Hi,
Basically, the requirement of WinXP to be on the first partition is not a Linux, but a Windows issue.  Partition Magic (PM) basically will do the partitioning in the way you tell it to do.

I suggest that if you want to have WinXP on your PC, do the following:

part 1. WinXP OS with programs (XX GB; XX depends on your needs, say 15 GB)
NTFS ("New Technology" File System)

part 2. Fat 32 data for WinXP and for Linux (YY GB.  say 15 GB)

part3 - say 15 GB for your Ubuntu or kUbuntu OS and programs.

part 4, has to be extended partition that you will not see.

Now, logical partitions:

part 5. Linux swap partition - for a modern PC perhaps 2 GB

part 6. Linux data partition.  When you install Ubuntu, suggest you create a "Documents" directory on this partition and make a symbolic link to it in your /home/user directory.  This way, if you reinstall Ubuntu later, you need not lose any data!

HTH a bit.

OldAl.

---

### Post by Xyphus on 2007-07-10
Starting with Windows 2000, the OS really doesn't care which partition you install it on.  However, I would install the Windows OS first before installing Ubuntu (or any other version of Linux). I would suggest at least partitioning your drive into two separate partitions. Put Windows on the second partition (it will still call the partition "C:" most likely, even if it is the second partition on the drive).  Then, install Ubuntu on the other partition.  Once you install the various OSes, it should then offer the option of booting into either OS at startup.

---

### Post by bullsmack on 2007-07-10
im getting very frustrated trying to install ths operating system.

every time i get to step 4 it tells ,me that i need to set up a root file system at the partition screen. WELL IM AT THE PARTITION SCREEN!!!!!  THAT IS STEP FOUR!!!! and i even tried making a ext2 file system partiton before even trying to install and then tried to choose it to install on. this  is frustrating because no mater which partition i select it says this , but there is NO PLACE TO MAKE THE SWAP FILE WHICH IT SAYS I NEED!!!. no matter which partition i choose it tries to say that i need to make this partititon. can someone please give me a DETAILED INSTRUCTION FOR STEP 4? i cannot believe that i need somone to type out steps for a step!!! what do i select,/boot, or there are like 7 or 8 other"/options" but i have the feeling thqat if i did get one of them right it would still tell me to make this file system. see i dont understand it because thats what partition majic MADE me do to make the partition in the first place! i had to make it the ext2 file system to even set up the parttion.   all i want to do is install the dagone thing and keep windows as well till i know what im doing. but why im obviously overlooking somethign is beyond me. there isnt but a couple things you can possibly do. 

sorry for the frustration. but this is driving me nuts. then im thinking that maybe my 10,000rpm hard drive isnt supported by linux. so again im lost

---

### Post by mopey on 2007-07-10
> **bullsmack said:**
> every time i get to step 4 it tells ,me that i need to set up a root file system at the partition screen. WELL IM AT THE PARTITION SCREEN!!!!!  THAT IS STEP FOUR!!!! and i even tried making a ext2 file system partiton before even trying to install and then tried to choose it to install on.

Don't make an ext2 partition before hand.  It'd be better to make it free space, but you can always do that on the install.


>  this  is frustrating because no mater which partition i select it says this , but there is NO PLACE TO MAKE THE SWAP FILE WHICH IT SAYS I NEED!!!. no matter which partition i choose it tries to say that i need to make this partititon. can someone please give me a DETAILED INSTRUCTION FOR STEP 4? i cannot believe that i need somone to type out steps for a step!!! 

You're confusing making a partition with formatting a partition.  

So you should have something like x gb of free space.  If not, then create free space.

Create a swap partition in this free space.  It should be around 2 times the amount of memory you have.

Create a root filesystem.  ext3 is a good choice.  Be sure to select a mount point of /.

It's easier for beginners to automatically partition, but that only really works well in my experience if you aren't trying to dual boot.

> what do i select,/boot, or there are like 7 or 8 other"/options" but i have the feeling thqat if i did get one of them right it would still tell me to make this file system. see i dont understand it because thats what partition majic MADE me do to make the partition in the first place! i had to make it the ext2 file system to even set up the parttion.   all i want to do is install the dagone thing and keep windows as well till i know what im doing. but why im obviously overlooking somethign is beyond me. there isnt but a couple things you can possibly do. 

sorry for the frustration. but this is driving me nuts. then im thinking that maybe my 10,000rpm hard drive isnt supported by linux. so again im lost

It's supported.  Linux will run on nearly anything.

---

### Post by dabl on 2007-07-10
Couple of pointers that may help:

1. Download and burn the GParted Live CD ISO and boot that CD to do the partitioning part of the job, including setting the "boot" flag for the partition where you want to install Win XP.  Get it here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

You can leave the formatting for Win XP and Ubuntu, respectively, just set up the partitions with GParted.

2. Install Win XP first if you don't want to spend the rest of the summer twiddling your Grub file placement and boot menu.

3. Use the Ubuntu Feisty Alternate Install CD, not the Live CD -- you'll get better control and visibility of the installation process.

4. I'm running a pair of WD-1500s (10,000 rpm SATA drives) -- I don't think your hard drive is an issue.

I hope these help you along. :)

BTW, if there is an IDE drive on that motherboard, there's a major problem if it already has an OS on it.  There are workarounds, but that is a complicating factor to installing Ubuntu on the SATA drive.

---

### Post by bullsmack on 2007-07-10
all  is well. i am typing to you from installed feisty.   YAY !!!!!!!!   thanks peeps.

---

