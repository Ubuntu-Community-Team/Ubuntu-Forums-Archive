---
title: "dual boot Works! on two drives one SATA and one IDE"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by roboghast on 2006-09-07
This is how I set up my puter to dual boot on the SAME SATA hard drive and have a second IDE hard drive as a second drive (a slave).

Both Windows XP AND Ubuntu are installed and working on my 80 gig SATA Hard drive. It wasn't easy and it took a bit of hit and miss but this is what I did. If I were you don't give up trying different ways it will work! 

number of jumper positions 3
number of ATA cable connectors 2
number of OS 2
number of Drives 2
3 x 2 x 2 x 2 = 24 different combinations at least- ugh  

I'm a noob to Linux, I'm no computer expert - so maybe this will help some other newbie people out there. 

**System: **
I have an Alienware area 51 with Nforce motherboard, it has a 80 gig SATA hard drive. After I got fed up with Windows, I tried Ubuntu and have fell in love with it. BUT I still wanted to run games. If you read my other posts you can see how frustrating this was. 

SO the solution was to have both Windows XP (for games) and Linux for work, browsing, email, etc. 

I had erased Windows (after backing up all my cool Enya music files on a smart drive) and had Ubuntu Installed on the disk, Windows was not on it. 

I bought a second Hard Drive, which used the ATA cable, that's the flat fat cable, Like I said I don't know too much about comptuers, just work on the desktop rarely tear them apart. 

My original Drive is a Baracuda 80 Gig SATA the second drive is a Maxtor 100 gig. 

I wanted Windows and Ubuntu on the 80 gig SATA Hard drive because I think that drive is faster - it seems that way to me anyways. 

**1**. OK, First I unpluged the cable from the Second drive so the 80 gig SATA was the only one working. 

**2.** I installed Windows XP **first reformating** the hard drive with quick format **I also pushed F6** when it asked if I wanted to add RAID - don't know if this had anything to do with helping Ubuntu install but it didn't hurt. (now after you install it **DONT update Windows and add a bunch of drivers and stuff yet** - you want your space on your Hard drive relatively free. I noticed when I did install the nvidia drivers and other things first it wrote stuff to the middle of the hard drive - ugh want to save that space for Ubuntu) 

**3.** As soon as the basic windows was installed **I defragmented it** - YES even after you just install Windows seems like there are fragmented files. (puh Windows!) This helped compact the files better.

**4.** **I restarted with the Ubuntu LiveCD disk** in CD ROM so it booted the Live version.

**5.** I pushed the install icon. It will ask you the basic setup stuff, like name and time. THEN when it goes into the PARTITIONING. The automatic option this didn't work because the Disk is formated by windows because it was formatted with the NTFS format not FAT32. It would stop and say it couldn't do it. DONT BELEIVE IT you can do it manually. 

**YOU DO IT MANUALLY** - sounds scarey? not really - basically you pick about half the drive and reformat it with the **MANUAL PARTITION** option.

**SO..**
Go into the format MANUALLY, don't try the automatic option or the sector 0,0,0, install over everything option - **go to the THIRD option Manually set partitions. **

Click on the BIG chuck of disk space, and click on (I think its the little arrow beside the menu, I forget, BUT its the option that allows you to ADJUST THE SIZE of how much disk space you want to parition). I made a parition about half the size of the disk AND make sure you **click the option on the right that say REFORMAT**. It will reformat that partition for Ubuntu.  I didn't touch the Swap file at all. (at least you know that THIS is what you have to mess with to get two operating sytems on the disk. 
 
IT WILL ASK YOU if you want to make it "/boot" or "/" or "/whatever" **PICK THE "/" OPTION** (I did and it worked, probably could use others but this worked)

and then I clicked partition. It seemed to work fine - it installed - and GRUB (which it the application that switches between Windows and Ubuntu for you) was working fine when I restarted. It gave me the option of windows or Ubuntu, the safe Ubuntu start up and that memory check thingy. 

6. I turned off my comptuer and plugged in the drive but for some reason I got a blank screen! - I realized that I had plugged the BLACK connector on the flat grey ATA cable into the second hard drive - I remember reading that the slave liked the GREY connector for some reason. SO I plugged the grey connector and made sure the jumper on the second hard drive was set to SLAVE. 

It seems to work now.

**SO in summary: **to dual boot MANUALLY PARTITION the master drive with Windows XP in it. I would do a fresh install of Windows, and use the F6 allow RAID thing option, don't know if this has anything to do with it but it worked. 

USE THE MANUAL PARTITION OPTION IN UBUNTU LIVECD INSTALL --SET THE PARTITION TO "/" choose a good chunk of the hard drive to partition. 

AND make sure your hardware is set up right in your BIOS, hard drive jumper options of "select cable" and making the second drive a master DIDNT WORK for me. It may with some smarter people but I'm not. 

Now I am going to try to use the slave drive - Maxtor has a Windows install application for that not sure if Ubuntu will like that or not - going to try or I may find an application that will format the slave into a half FAT32 format and some in NTFS format--maybe Ubuntu can do that? wish me luck! 

:D 
love, 

roboghast

---

### Post by BLTicklemonster on 2006-09-07
Le Eeeek.

How can I get winderz to partition my hard drive as fat32, I wonder? I have yet to get it to do that lately. Used to do give me a choice...

This is pretty swift. I'll give it a go, as I have only reinstalled once since putting ubuntu back on mymachine less than a week ago. God know's I'm gonna blow something up pretty soon and have to redo it all again...

---

### Post by djrobthaman on 2006-12-02
Windows by default won't give you the option to partition a drive as fat32 if it is bigger than 32gigs.  You can however bypass this in linux.  

One thing though.  Even though when I looked on the net and everbody seems to say it's all ok doing it and Windows will be able to see the disk when you do this (thereby having your hard drive read/write compatible with both OS's) I tried it once with suse.  And suse saw it fine.  I even loaded some files on there.  However, when I went over to Windows it couldn't see a thing.  It found the hard drive and recognized it as fat32 but the files were magically invisible (it did register, however, that there was a certain amount of space used on the disk.  Just not what was taking up the space.  Weird)

Hope this helps,
Douglas

---

### Post by hainesr on 2006-12-06
You can avoid all that tedious defragmenting and re-partitioning malarky by not letting WinXP write over the whole disk. When the windows install gets to the bit about installing in the free space, create a partition instead and then install into that. Then when you come to install linux you can safely put it in the free space on that drive instead of having to reduce the size of the WinXP partition first...

Cheers,
Rob

---

