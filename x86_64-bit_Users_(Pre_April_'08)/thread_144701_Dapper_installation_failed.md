---
title: "Dapper installation failed"
date: 2006-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bonjourmate on 2006-03-14
Alright, followed the instructions on the wiki for burning DATA cds.

Downloaded dapper-install-powerpc.iso and burned it to cd (once at max speed, once at slowest speed.  In case it messed up on the first).  

The first time (with max burn speed) when I chose to boot from cd I got a little folder that flashed a ? 

The second time when I chose to boot from CD it just kept coming back to the "press l to boot linux, press c to boot cd-rom" after pressing 3 about 3 times it just froze.

Can some one tell me what I'm doing wrong in my dapper installation?

---

### Post by andrego on 2006-03-14
Well, this is the Breezy forum (breezy = latest stable release, dapper = development/unstable release), so I'd first recommend you try Breezy.  A Dapper CD image isn't tested much (iirc), and may not even boot no matter what you try.  Breezy is tested...

However, if you're set on using dapper, more info would be good..like what kind of Mac do you have?  Specs like Processor (G3, G4, G5 or Intel?), RAM, HD, Video Card, etc would be good.

Edit: Also including the location to the instructions would help.  It's been a while since I've browsed the PPC wiki :)

---

### Post by Bonjourmate on 2006-03-14
Powerbook G4 1.5 Ghz
2 gig of RAM
80 Gig HD
ATI Radeon 9700 (I believe that is the stock card)

here is the wiki [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by andrego on 2006-03-14
Ok, looks like there are specific instructions for a variety of use-cases.  I'm assuming you burned the image on the Powerbook?  If so, did you use Disk Utility, or Firestarter FX (or something else?).

I'm grabbing the dapper PPC iso as we speak; I'll try to re-create what you're seeing (although, my main PC is a...PC, running Dapper, so I'll test on my iBook G3...)

---

### Post by Bonjourmate on 2006-03-14
No, I didn't use OS X to burn it.

I used the instructions for burning it with Ubuntu...  that's what the wiki link was about.

---

### Post by andrego on 2006-03-14
Alright, I had a nice long post written up for you, but Xgl ate it (stupid shift-backspace!).  The long and short of it was this:

1) The wiki describes burning on MacOS X, WinXP, and Ubuntu, but I don't think that matters anyway.  Once I booted my PPC ubuntu CD, I realized the boot prompt you got will only happen after an install (not while trying to boot the install CD).

2) This means you must have gone through the install.  If the CD was ok, you wouldn't have received any errors like "file missing/corrupt" or "CRC error", "cannot read from source file", etc.  Did the install go through without error?

3) Because we can't enter any boot arguments for linux (boot loader freezes before stage 2, when you select kernel and can pass arguments), we're limited in troubleshooting...If we're stuck on option 3, not much we can do, other than verify how it was installed - likely culprits would be bootloader installation/configuration and kernel install/config.

So, any errors during install would be good to post, also anything you did to customize the install (or did you just select defaults all the way?).  If you can get past the prompt to select OS (I thought it was X for OS X, L for Linux, and M for Mac OS 9?) and on to stage 2 bootloader, you could also try entering "linux video=ofonly" to see if the video driver is an issue (unlikely, but again, dapper isn't release quality...could be a bug there, and initializing video happens early in the boot process).

---

### Post by Bonjourmate on 2006-03-14
What do you mean it'll only happen after an install?  I see it every time I boot up my computer, cd inside or not.

---

### Post by andrego on 2006-03-14
Wierd; I totally don't get that when I boot with the install CD...I just get a yaboot prompt that says "boot:".

One thing you could try is powering on the 'book while holding "option".  It'll bring you to an openfirmware GUI boot selector.  Select the yaboot partition, and then click the arrow pointing right to start booting.  This will force it to boot that partition, instead of whatever nvram might be pointing to.  At least we'll know the mac's trying to boot the right drive then.

Let me know if anything changes, or it's still the same story when you try that.

---

### Post by Bonjourmate on 2006-03-14
by option you mean the open apple type key right?

---

### Post by andrego on 2006-03-14
The key between "ctrl" and the apple key, on the left side of the keyboard (if your powerbook is anything like my ibook...some macs have one on either side of the keyboard)

Edit: on my keyboard, the key is labled "alt" on the top-half of the key, and "option" on the bottom section.

---

### Post by Bonjourmate on 2006-03-14
:D missed that key

---

### Post by Bonjourmate on 2006-03-15
Alright, held down the option key and it brought me to a blue screen with a Linux logo in the middle.  On the left was a reload button and to the right was a button with an arrow.  If I pressed the arrow it brought me to the press l to boot linux, press c to cdrom.  Either way...  no way to install was found.

Any ideas?

---

### Post by jdp on 2006-03-15
If you did that with a CD in the drive, then I'd guess it was a bad burn or you are having CD drive problems.

---

### Post by Bonjourmate on 2006-03-15
Odd.  Didn't have CD drive problems when I installed Ubuntu a week ago.  Burned it at lowest speed too.

---

