---
title: "Can't boot from LiveCD, or after install"
date: 2008-06-02
forum: x86 64-bit Users
---

### Post by apedeaux on 2008-06-02
Okay here is my situation.

Downloaded DVD version of Hardy for AMD64.  Burned to DVD.  When I boot from the CD, I get to the splash menu where I can load Ubuntu, check the CD, install, etc.  If I select the first option, "Install or Run Ubuntu" it starts to load, and the text starts scrolling line by line from the top of the screen.  When it gets to the 4th line, which is something about initializing boot script, involving /etc/boot, it hangs up (at work now, will post the exact message when I get home).  If I ctrl-alt-del from here, I will get all the shutdown messages then it reboots.

From the splash screen, if I instead select the text install, I can go through the installation just fine, everything seems to be okay, but when I try to boot after the install, my bios POSTS, then I get a blank screen with the cursor blinking at the top left, and nothing else.

My machine is:

AMD Athlon64X2 6400
Nvidia 8800GT
Soundblaster XFI Extreme
Windows XP64 running on 2 striped SATAs.
I have a 3rd solo SATA where I am installing Ubuntu.

I tried re-burning the DVD, same problem. Then I DLed the smaller CD version, burned it, and have the exact same problem, so I don't think it's a bad burn or download.  Running the CD-check from the splash menu, my monitors go off, the drive spins for maybe 5 minutes, then stops spinning and I am left with my monitors both still off and nothing happens.

My next step will be to get Gutsy and see if I have the same problem. Any advice?

Thanks

---

### Post by linux4me on 2008-06-02
What is the boot order for devices in your BIOS? I'm wondering how your system knows which of the drives to attempt to boot from?

---

### Post by apedeaux on 2008-06-02
I just hit f8 at POST to get to the screen that lets me pick what drive/disc to boot from.  If I pick the XP drive, it boots into windows just fine, but if I pick the linux drive, I just get the blinking cursor.

---

### Post by linux4me on 2008-06-02
Have you tried changing the boot order in your BIOS to boot the Ubuntu drive first, put the install CD in the drive, and then do the install without the requirement of the F8 to see if it works?

---

### Post by apedeaux on 2008-06-02
I did not, I will try that tonight.

---

### Post by linux4me on 2008-06-02
I'm not at all sure that will help; I'm just trying to think of things about your system that vary from the run-of-the-mill installation that you can eliminate to try to identify the cause. That makes it easier to identify a solution. The two I noticed were the separate non-RAID drive and the dual monitors.

The other thing I wonder about is whether your CD is bad. Did you download the CD in binary mode? I believe that there have been some issues with using the "auto" mode in some FTP programs. If you don't have a decent CD, all bets are off.

---

### Post by ilrudie on 2008-06-02
The blinking cursor sounds like you may have gone through the text installer but declined to install a bootloader like grub or lilo.  Even if you do not wish to duel boot you need a bootloader.

---

### Post by apedeaux on 2008-06-02
> **ilrudie said:**
> The blinking cursor sounds like you may have gone through the text installer but declined to install a bootloader like grub or lilo.  Even if you do not wish to duel boot you need a bootloader.

I'm fairly sure the installer never asked anything about a bootloader... I certainly would not have told it not to install it.  Is that something I have to do seperate from the regular installation?

---

### Post by ilrudie on 2008-06-02
The default bootloader is called GRUB.  Most likely it is one of the last steps on the installer.  I do not recall the alternate installer well because I have not used it in some time.  

It is possible that grub was installed on a different device.  You can watch closely when you select the windows drive from the bios and see if grub is there but auto booting into windows quickly.  When my pc was setup to autoboot it would display a message for about 3 seconds to the effect of "press escape for more options".  If there is anything like that press escape and see if Ubuntu is an option in that menu.  Now it is possible to install grub outside of the installer from a liveCD but it is a fairly advanced procedure and if you don't have anything of value on your ubuntu drive (which I'm assuming you don't because you can't boot it) its probably easier to just reinstall the whole OS from scratch.  I suggest using the alternate install cd since you seem to be having problems with the liveCD installer.

---

### Post by apedeaux on 2008-06-02
Okay here are my further developments...

I have tried installing Hardy and Gutsy both, using Live and alternate CDs, and reburning everything, and I still can't boot.  I am starting to think it may have to do with my RAID.

I have been running WinXP64 on a 2 SATA striped RAID.  I just got a new hard drive, and the plan was to plug it in and install Ubuntu on it, leaving the Windows RAID completely seperate and uninvolved.

The RAID is the one that come with my ASUS m2e mobo, I think it is nvidia Mediashield.  When I try to boot to the Linux drive, I POST like usual, it detects my IDE drives and I can see the new drive on the list, then it goes to the MediaShield RAID health check, then it goes to the endless blinking cursor.  Is it possible that the RAID is somehow rendering the unRAIDed drive unbootable somehow?

When I install Ubuntu it definately tells me near the end that it is installing and setting up GRUB... but I certainly never see anything GRUB-like when booting.

Any ideas?


edit: The more I think about it the more I think it is definately GRUB-related... but I can't figure out how or why.  I've been looking on the web at ways to put GRUB on a floppy, but it seems really involved and I'd rather save that as a last resort ;)

---

### Post by apedeaux on 2008-06-02
Okay someone tell me if I'm on the right track here... GRUB needs to get installed to the master drive, which I guess is my RAID/XP drive... and I assume that Ubuntu is like XP in that it can't understand a RAID array w/o drivers or something, so the installer doesn't know to put GRUB on that master drive, so it goes on the Ubuntu drive which can't address the MBR.

---

### Post by apedeaux on 2008-06-03
Now that I've figured out that my problem is with GRUB and my RAID, I opened a new thread in the Installation and Upgrades forum, since that seemed a big more appropriate. (I would have just moved the thread, but I couldn't figure out how ;))

[http://ubuntuforums.org/showthread.php?p=5105839#post5105839](http://ubuntuforums.org/showthread.php?p=5105839#post5105839)

---

