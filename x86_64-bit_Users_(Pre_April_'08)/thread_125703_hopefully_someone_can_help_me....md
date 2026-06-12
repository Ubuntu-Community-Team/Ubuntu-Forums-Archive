---
title: "hopefully someone can help me..."
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by auke5 on 2006-02-04
So my intro to linux hasn't been great.  ive gotten virtually no support from other linux sites i've checked out and i'm in a bit of a bind, hopefully someone here can help!

i decided it'd be fun to try linux on my 4 month old G4 powerbook.  I initially tried out mandriva (limited ed 2005) and it never ended up installing correctly, each time giving me an error message of some sort.  i tried to reinstall mac OSX, but when i get to selecting a drive to install onto, no drive appears; which i believe to be because i formatted the hard drive during the linux install to Ext2 or 3, rather than standard mac format.

so anyway, it was suggested to me that I try out Ubuntu because there's a live CD available.  So i tried that, and unfortunately it didnt work.  I also downloaded the newest 5.10 release of Ubuntu and popped that CD in and i can't get it to run the installer...and i supposed to press something to get it started or is there something i'm doing wrong?

I know that my last install of mandriva didn't work correctly because all that shows wheni start my laptop is the little "finder" smileyface with a question mark next to it.  Openfirmware is still accessible, and my apple hardware test comes back clean, so i was just wondering where to go from here!  

thanks in advance!

---

### Post by Derek Djons on 2006-02-04
If I'm correct there should be an "advanced" option in Mac OS X which enables you to partition the harddrive to your own wishes.

If that doesn't helps you can always Google for "[COLOR="Red"]Hiren's BootCD[/COLOR]." With this Swiss utility CD you can start up partition tools which enable you to manually erase the whole harddrive and re-partition it with Journal HFS.

---

### Post by stream303 on 2006-02-04
Have you tried rebooting with the ubuntu cd in the drive and holding down the "C" key?

---

### Post by auke5 on 2006-02-04
i will have to try the Hirne's Boot CD, i havent heard of that one yet.

i haven't seen any "advanced options" during install...though maybe i haven't looked hard enough?  i can easily access my disk fixing utility though the computer freezes when i try to.

I have tried holding down the "c" button for the live CD but to no avail, doesn't work. 

i was able to bittorrent a new copy of the 5.10 install for ubuntu and burned that using my PC, and tried to install the new copy but it stopped while installing the base system.  here's the error message:

*"an error was returned while trying to install the initrd-tools package onto the target system.  Check /target/var/log/bootstrap.log for details."*

so yeah that didn't work, and unfortunately i have to head out to my job, but anyone know what that error is about? could my computer be just burning bad CDs?

i seem to be having problems burning images on my PC lately...im going to try a new pack of CDRs and see if that doesn't fix my problems.  I tried to switch over  to roxio ezcdcreator from nero thinking that maybe it was my software, but i guess not.  maybe a new CD drive will be in the works for me tomorrow too :(

---

### Post by auke5 on 2006-02-05
will Hirens Boot CD work on apple computers?  mine doesnt seem to work when i burn it :(

---

### Post by linear on 2006-02-05
[quote=auke5]will Hirens Boot CD work on apple computers?[/quote]

It appears to be a DOS CD, so the answer is no.:cry:

---

### Post by radiojohn on 2006-02-05
I think I am having a similar problem with an old imac (blue and white).  I booted from the live CD and just got a blank screen.  I'd love to wipe the drive and run ubuntu but I don't think it likes the iMac.

---

### Post by N8K99 on 2006-02-06
I had to trick my Powerbook into letting me install. First when I started up, I had to hold command-option-F-O, then on the resultant screen, I chose to re- start, and with the install CD in the drive, I held C which engaged the Installer. I was using a ShipIt CD which may make some difference. I have heard that some CDs burnt off the web do not 'catch' if they were burned too fast.

---

### Post by linear on 2006-02-06
[quote=radiojohn]I think I am having a similar problem with an old imac (blue and white). I booted from the live CD and just got a blank screen. I'd love to wipe the drive and run ubuntu but I don't think it likes the iMac.[/quote]
iMac video problems are a different beast. See suggestions in this post:
 
[http://ubuntuforums.org/showpost.php?p=642271&postcount=2]("http://ubuntuforums.org/showpost.php?p=642271&postcount=2")

---

