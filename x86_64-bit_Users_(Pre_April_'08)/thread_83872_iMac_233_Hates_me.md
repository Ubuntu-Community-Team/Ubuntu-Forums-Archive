---
title: "iMac 233 Hates me"
date: 2005-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigtymer on 2005-10-29
I recently acquired a imac 233 off of a friend, and i would like to install ubuntu on it, but i seem to be encountering some problems. Now, to start off with, it was running fine in OSX until it attempted to do a system update. Halfway through downloading, it froze up, and when i restarted it began to shut down every time i tried to run a program. If i turn it on and leave it go, its ok, but every time i try to run a labor intensive program, it crashes and the screen turns off, and the power button turns orange. If anyone knows what is wrong with my computer, or how to fix it, please let me know... so eventually i can get ubuntu on it.

---

### Post by ssam on 2005-10-30
most likely bad ram. you will need to figure out how to get to the ram slots (cant remember where it is on the tray load imacs.) if there are two ram chips in there try taken each one out and running with just the other. you may find that one works fine, but the other is bad.

another thing you could try is zapping the PRAM. i think you hold down alt-apple-shift-p-r at boot (google would know).

do you have the os x install disk? you can to a verify and repair on the hard drive with that.

i think the tray load imacs may be "old-world", if so the process of booting linux on them is a bit trickier than the "new-world".

---

### Post by bigtymer on 2005-10-30
well... i found the ram, and there is only one chip. It may be a moot point anyways, cause now it wont boot at all. It just goes to firmware, and if i type boot, it says claim failed. I have no idea what im doing with macs, and i dont have an install cd.... ive been looking everywhere for one, but no one i know seems to be at all interested in macs. I really would like to make this run!

---

### Post by jdp on 2005-10-30
It sounds like the PRAM settings got lost (did you try the reset mentioned above?  That'll reset them...)  Are you looking to setup dual boot, or just go Ubuntu only?  If Ubuntu only then try to boot off the CD.  To do that you put the CD in the drive, reboot, and hold 'c' at the chimes until it seems to be going from the CD.

If you get stuck at Open Firmware, try typing **mac-boot** and right after you press return, hold down 'c'.  I had to do that with a 350 iMac because OS X had set things up in OF that prevented it from booting from CD at a cold start or reboot.

---

### Post by bigtymer on 2005-10-30
right... so i zapped the pram, and at least now i can get it to boot. but still cant run any programs in osx, or boot off of the cd. it just unexpectedly quits, or the screen goes blank and the power light turns orange once again.

---

### Post by king_arthur on 2005-10-31
[quote=bigtymer]right... so i zapped the pram, and at least now i can get it to boot. but still cant run any programs in osx, or boot off of the cd. it just unexpectedly quits, or the screen goes blank and the power light turns orange once again.[/quote] 
Big timer, this is a known problem with tray loader macs.

For some reason, in system 9.x they work but in OSX they fall in sleep mode. 
It is a firmware problem.
Did you update your boot rom?

Last year, I have tried everything I could possibly think of to solve this very same problem on the same machine but had to give up after a while because of the firmware issue.
Please note that the upgrade has to be made BEFORE you attempt running OSX.
There is plenty of information in the Apple Users Forum.
Just browse into the old systems section and look for monitor problems for tray loaders as that is the only model affected.

As for Ubuntu, I know that many people will argue about this but believe me, I know what I am talking about, OSX is far better (and also faster) than Ubuntu on a mac, provided you have enough RAM (>256Mbyte) installed.

I have had both running on my PowerBook Wallstreet for a while.
In particular, the X.server, is ways behind what OSX delivers with the Aqua interface as this has been optimized for Apple h/w.

Please note that, generally speaking, I am Linux power-user since a long time and real entusiast about Ubuntu however, having said that, if you just want to play with Ubuntu on a mac, go ahead, if you want to work stay with OSX on your mac and Ubuntu on a PC.


You have been warned... :)

/P

---

### Post by peter_m on 2005-12-04
I know this is an old thread but who knows:

SSAM, all iMACs are "new world". I'm sure of this.

BigTymer, try updating your ROM or Firmware I forget what it is called but you can find the patch at apple.com. It will only run under OS8 or OS9 and it could help but... 

I really think the problem is that your trying to run you monitor at the wrong frequency. iMACs have picky monitors and you OS X could be trying to drive it a the wrong frequency and that ALWAYS blanks the screen and turns the power light to orange. ALWAYS!

Try playing with the screen resolution. It only supports 800x600@95hz and 1024x768@75hz. If you find a panel for monitor settings called SwitchResX, remove it or set it to use standard Apple resolutions. It's a tool to force non-standard resolutions and it might be pushing the iMACs monitor beyong it's specs. I think it can even change the resolution on the go depending on what application you are running. All according to the settings it's loaded with... [http://www.madrau.com/html/SRX/About.html](http://www.madrau.com/html/SRX/About.html)

Good luck!

---

### Post by bigtymer on 2005-12-05
i updated the firmware, and that seems to have fixed the problem.... it runs fine, except now when i put the os x disc in, it says that os x cannot be installed on this system. OS9 runs fine, with no problems. Ubuntu still doesnt want to install. Now it is a perfectly fine iMac with OS9 taking up perfectly fine closet space.

---

### Post by ssam on 2005-12-05
you might want to have a go at installing yellowdog linux on it.

---

### Post by mrivers on 2005-12-05
I just did my first ever Linux install on an iMac 233MHz Rev. A with 96Megs Ram and a 4 Gig hard drive.  I erased the OS9 software, and did a Ubunto 5.10 install off the CD, and it just runs....  Gnome is slow, however, and I will probably look for a different window manager.  I also have to tweak the video settings.  I havent got wireless working yet, as the Belkin USB adaptor I bought must not have the RT2500 chipset. 

After being happy with the stability of OSX on my other machines, I'm glad to be rid of the instability of OS9. I look forward to using this as a web/email station with the ability to begin to use Linux.

---

### Post by pvz on 2005-12-06
[QUOTE=mrivers]I just did my first ever Linux install on an iMac 233MHz Rev. A with 96Megs Ram and a 4 Gig hard drive. 
...
I look forward to using this as a web/email station with the ability to begin to use Linux.[/QUOTE]

I installed debian Sarge on an iMac with the same specs a couple of days ago, also just for webbrowsing and email (actually, it's for my sister). I tried Kubuntu first, but had no luck with that. Debian with a minimal KDE install works just fine. Opera for webbrowsing and Kmail as mailclient. 96MB is minimal, but workable, it's not slow in use. XFCE would be a good window manager too.
I can't imagine OSX performing better on this machine, even if maxed out with RAM..

A working XfreeConfig for it can be found here:
[http://www.petrvz.net/pages/xfree86configs.php](http://www.petrvz.net/pages/xfree86configs.php)

---

