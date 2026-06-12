---
title: "Diablo II Problem"
date: 2011-09-03
forum: Wine
---

### Post by GoldenNathan on 2011-09-03
Hello,

I want to run Diablo 2 Windowed but i have no clue how to..
And i can't install it with my discs, it just wont detect the play disc!
So i used the installed one from an USB works fine full screen.
I have Diablo 2 two times and with the program D2NT i should be able to use the second CD key (i have 2 different Diablo 2 folders with the full Diablo 2 installed).
But when i try i get unhandelled exception ...

Please help someone!

---

### Post by disabledaccount on 2011-09-03
Diablo works perfectly under latest wine, without any tricks.
Tips:
- manually (re)mount the cds during installation under /mnt or some other folder of Your choice. This prevents wine confusion, because every cd is mounted automatically under different name in /media folder.
- patch diablo to 1.12+ - this patch removes the need to run game with cd inserted, but You have to copy all video files to hdd.
- However, unless You are using modified version (like Median), patch 1.12 is the last one that allows to run game in 1024x800 and more.
- To run diablo in window You must launch wine configuration (winecfg) and select 'emulate virtual desktop' in graphics tab.

---

### Post by GoldenNathan on 2011-09-03
How can I manually mount? I'm kinda new to Linux so I don't understand what you mean by mnt:confused:

---

### Post by disabledaccount on 2011-09-03
That's very easy :) Insert the CD and when its icon will show on desktop run terminal and type:
> mount 
This will display all mounted volumes and You should see something like: "/dev/sr0 on /media/DIABLO II type iso9660 ...."
important is "sr0" - this is Your cd/dvd drive.
>umount '/media/DIABLO II'
>mount -t iso9660 /dev/sr0 /mnt/iso
Then run winecfg and set D: drive to /mnt/iso (Drives tab)
All CDs used for game installation have to be seen as D:, so in multi-CD instalation You have to mount them under D: - what means /mnt/iso
If installer wants to change cd You need to: umount /dev/iso, change the CD and mount it again uder /mnt/iso
To run installer You just type >wine "D:\\install.exe" (whatever You need to run)

Of course mount location name is an example and f.e. it can be located in Your $HOME dirtectory.

---

### Post by GoldenNathan on 2011-09-03
Wait what? 

I insert the disc and then wine starts everything up I enter my cd key and when I'm at 50% it asks me to insert play disc but when I do that nothing happens. That's my question how to fix this?

---

### Post by disabledaccount on 2011-09-03
You have to disable autoplay: Nautilus(menu: edit->preferences). OR choose "Cancel/No" during installation and then start from "stable" D: drive again.
Additionally, It's clear that Ubuntu is NOT windows and WINE is kind of "workaround" - You should learn/understand the basics before trying it.

---

### Post by GoldenNathan on 2011-09-03
Nono i wanna learn this!

When i typ Mount i don't get the thing you said i get this:

/dev/sr0 on /media/INSTALL type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)

But thats kinda the same :)

But when i typ /media/DIABLO II

it says no such directory

---

### Post by GoldenNathan on 2011-09-03
> **tomazzi said:**
> Diablo works perfectly under latest wine, without any tricks.
Tips:
- manually (re)mount the cds during installation under /mnt or some other folder of Your choice. This prevents wine confusion, because every cd is mounted automatically under different name in /media folder.
- patch diablo to 1.12+ - this patch removes the need to run game with cd inserted, but You have to copy all video files to hdd.
- However, unless You are using modified version (like Median), patch 1.12 is the last one that allows to run game in 1024x800 and more.
- To run diablo in window You must launch wine configuration (winecfg) and select 'emulate virtual desktop' in graphics tab.

I can't get the setup.exe work without using wine. Here's what i do i go to applications then i go to wine and click on wine tricks i select install Diablo II but @ 50 % my problem shows up! But i can't mount 2 disc's at the same time so i don't think manual mounting will work?

---

### Post by disabledaccount on 2011-09-04
In /media/SOME_NAME the <SOME_NAME> is the title of CD - in Your case it's INSTALL

It depends on the install program if it will search all CD drives for second CD. If setup expects next CD to be placed in the same drive, then You have to remount. Most of older games need remounting of cd/iso under the same drive letter.

---

