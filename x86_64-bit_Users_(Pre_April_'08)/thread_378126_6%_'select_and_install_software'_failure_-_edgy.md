---
title: "6% 'select and install software' failure - edgy"
date: 2007-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ecs_pf5 on 2007-03-06
Trying to install Edgy from the alternate AMD64 CD, as a dual-boot with Windows Vista.

I am installing Vista from the DVD first, using it to create two 40Gb partitions 0 and 1.

I am installing Vista to partition 1.

Then, I am booting from the Edgy CD and taking the top menu option. I am using the partitioner as follows:

1. Manually delete all non-Vista partitions.
2. Automatically partition the remaining free space
- it creates a main, bootable root partition as primary ext3 #1 plus a small swap partition as logical swap #5 

Edgy installation then proceeds fine, up until 6% of 'Select and Install Software'. It lingers on 6% for a long time with plenty of CD activity, before finally reporting an installation step failed. The CD at this point is locked in the drawer.

I've had a close look at the CD & it seems physically free of defects.

I downloaded the Edgy CD using Dapper from the main Ubuntu site and burnt it using the CD-burning app available as default in Dapper's menu. 

I installed Dapper recently using the same procedure & it worked fine.

Any suggestions as to where I'm going wrong?

---

### Post by kleeman on 2007-03-06
Sounds like a dud cd. Use the check cd option on the livecd. Try redownloading and reburning at a slower speed on the burner.

---

### Post by ecs_pf5 on 2007-03-06
Forgot to mention it's a SATA drive if that makes any difference. 

I'll go check the CD.

==

./pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.1.20060513-1_all.deb failed MD5

Apologies for being new & thinking I could get away with skipping checking the MD5 after downloading the .iso - will know for next time ;)

Cheers

---

### Post by irish8890 on 2007-03-12
I have had similar problems last weekend.  My final install crash was around 85% installed.  Some things that might help:
- Make sure that the SATA drive that will have the installed OS is the first SATA drive in the BIOS bootup.
- There are no hardware conflicts with your DVD drive.  I replaced my CompUSA/BenQ drive with a Sony drive & my results were a little better.  I also had the DVD drive as cable select & master on the IDE cable.
- After many retries I managed to get a working system by skipping the rest of the software install.  But I did manage to install GRUB & finish the remaining installation.  After fixing the nVidia graphics I managed to get into the graphical desktop system & installed software I intend to use.

I still have issues.  
- Nautilus does not work very well; I don't see it in the menus & I cannot get a file manager when I click on a drive icon on my desktop.
- I will have a system lockup (compelte lockup, video, keyboard, mouse) occasionally & i have to do a hard-boot.

My system: 
Abit KN8 SLi, AMD 3700+, eVGA eGeForce 6600LE

John

PS:  I had similar install problems with FC6 & openSUSE 10.2.  I have to do a text-based install except for openSUSE 10.2 where the safe graphical install works.

---

### Post by totalnub on 2007-03-17
i had the exact same thing happen when i wanted to install Edgy 64bit. I went ahead and installed the 32bit version with text install. I am dual-booting with xp (where xp is on my 1st partition) I figured since i was new at all of this that i could try the 64bit install again, and after about 10min @6% it went past. so now i am running 64bit edgy. Keep tryin man. GL

---

### Post by terranghost on 2008-04-02
exact same problem here. happens with or without network connection.

since 2005 each year i give linux a try....and EVERYTIME it ends up being nothing but troubles.
:mad::mad::mad::mad::mad::mad:

---

### Post by Roger Mudd on 2008-04-13
I've been having the same problem with an alternate install of Gutsy to a Thinkpad T42. Strange, as I've used the same media to install to this machine on several occasions without issue. I decided to try the Hardy beta and it looks as if it's stalling at the same point. Not sure it matters, but the last package listed below the progress bar before the stall is Xorg. Then the dreaded "Please wait...".

---

### Post by Jouke74 on 2008-04-14
Note that the stop at 6% takes quite a while before it continues. All big important packages (Gnome, Openoffice etc) are installed. See if there is harddisk and CD activity. If there is, please wait, and wait and wait. With Hardy I noticed, it took about 15 to 20 minutes before it continued at about 75%.

---

### Post by Guilden_NL on 2008-04-27
> **Jouke74 said:**
> Note that the stop at 6% takes quite a while before it continues. All big important packages (Gnome, Openoffice etc) are installed. See if there is harddisk and CD activity. If there is, please wait, and wait and wait. With Hardy I noticed, it took about 15 to 20 minutes before it continued at about 75%.

After four hours, still the same problem.  I am seeing a lot of reports about this.

---

