---
title: "Live CD doesn't work"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ibu on 2006-04-08
Both my own and one that got shipped here would not boot.
Tiger 10.4.6
iMac G5 1.8GHz

Both times I tried the same thing happens:

Boots
Black Screen
press enter
White Screen that tells me to release a key to continue. I press Enter and many other keys and all that happens is my fan goes on loud... nothing else

what's wrong?

---

### Post by TeKoverride on 2006-04-08
I had this problem last night with the LiveCD as well. 
I had to change some settings in the BIOS

On my computer I   
-Enabled USB function support
-Enabled USB Function for DOS
-Enabled Thumbdrive Support for DOS

After I did that the LiveCD worked perfectly.

---

### Post by ibu on 2006-04-08
TeKoverride,
thanks, but can you please explain how to do this? I have no idea.. sorry!](*,)

---

### Post by jdp on 2006-04-08
He's talking about a PC.  Your iMac won't have any of this as it's a completely different type of computer.  I don't have an answer for you, but there are several threads here about running Ubuntu on G5 iMacs.  Try searching or browsing threads to find some info.  I do remember reading about G5 iMac issues.

---

### Post by seatea on 2006-04-08
Have you double checked to see if they are the ppc versions? Can you boot from your  Mac Install CD?

---

### Post by ibu on 2006-04-08
Okay:
what the problem was was that I had to type 
live-powerpc64
to make it boot.

my other problem:
after all that other booting stuff (like the bar and it had to get to 100%) i get a screen with a brown background and a cursor for half hour and the fan is really loud. After that I've waited a LONG time .. the screen was just black..

I don't get it.. what's it doing?
I'm using my 5.10 PPC live-cd that got shipped to me.

---

### Post by ibu on 2006-04-08
seatea:
yes..they'rePPC

---

### Post by jdp on 2006-04-08
In the search box at the top of every page here you can put in **g5 imac** and **g5 ppc64** and other key words and get many threads on this subject.  It seems that the problem you have is related to sound on the G5 systems, and some people can overcome it after installing Ubuntu.  It seems the LiveCDs may not work, as you don't have a way to disable sound so that it can boot.

---

### Post by ibu on 2006-04-09
Thanks jdp. So you're saying I can't boot it because of sound and installing Ubuntu will fix my problem??:( 

another thread with the same exact problem I got (same computer too) is:
[http://ubuntuforums.org/showthread.php?t=143627&highlight=iMac+G5](http://ubuntuforums.org/showthread.php?t=143627&highlight=iMac+G5)

Thanks.
off-topic: if I install Ubuntu on my Mac on a seperate partition will I have to reinstall my Mac to do this? Also, if I don't like Ubuntu for some reason can I uninstall it?

---

### Post by jdp on 2006-04-09
Try [this thread](http://www.ubuntuforums.org/showthread.php?t=89960) to repartition your HDD without having to wipe and reinstall everything.  You'll only need about 5-6GB for Ubuntu.

---

### Post by ibu on 2006-04-09
Will I be able to uninstall Ubuntu by deleting the partition?

---

### Post by 3rdalbum on 2006-04-11
To uninstall Ubuntu, you will need to:

1. Delete the Ubuntu partition
2. Delete the Swap partition
3. Boot up from a Mac OS CD and reset your Startup Disk control panel to your Mac partition.
4. (you can leave the Yaboot bootstrap partition on there, it won't cause problems)
5. Resize the now-empty partitions to form one big HFS+ partition (you might be able to merge them with the Mac one if the Yaboot partition is at the very start or end of the disk). Please note that I don't know how to resize the HFS partition, I've never done it :-) But I'm sure it can be done.

---

### Post by 3space on 2006-04-13
[QUOTE=ibu]Both my own and one that got shipped here would not boot.
Tiger 10.4.6
iMac G5 1.8GHz

Both times I tried the same thing happens:

Boots
Black Screen
press enter
White Screen that tells me to release a key to continue. I press Enter and many other keys and all that happens is my fan goes on loud... nothing else

what's wrong?[/QUOTE]

Hey,
I had the same problem yesterday installing on P3 500MHz system.  A friend said to press "RESET" and let it run again.  It worked!  Reason was that the BIOS was probably set for some Plug and Play devices, and there might have been an IRQ conflict.  When you reboot, it clears these parameters, so on second boot it works.  Hope that helps...

---

### Post by megabenman on 2006-04-23
[QUOTE=jdp]Try [this thread](http://www.ubuntuforums.org/showthread.php?t=89960) to repartition your HDD without having to wipe and reinstall everything.  You'll only need about 5-6GB for Ubuntu.[/QUOTE]
Do you think the installation CD will go far enough to use parted?

---

### Post by jdp on 2006-04-24
The install CD shouldn't try to use sound, so I think it should.  Otherwise, all those people who've installed Ubuntu to G5s wouldn't be able to go in and edit out sound functions.

---

