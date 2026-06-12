---
title: "Blank screen after install from live cd"
date: 2007-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Alfusious on 2007-11-30
I created the live cd, booted from it and then hit install for the demo but just get a dark screen after the kernel loads? WHAT GIVES? I should add some specs to help out in the diagnosis. I have amd 64 X2 6000 With nvidia 8600gts and 2 gb of ram. I am currently running vista.

---

### Post by SpaceFarm on 2007-12-01
Well I've got a 7600GT and amd x2 and after I installed Ubuntu the screen was blank too...It's probably not that much help but I was frustrated by it too but my solution was so simple. The screen turned itself off after booting! So I had to button mash and move mouse to turn the screen on again. 

Again, you've probably already tried this but if not...

---

### Post by derby007 on 2007-12-01
Could be a graphics problem. it hung for me aswell, try the Alternate CD.

---

### Post by picopir8 on 2007-12-01
This is a known problem in the 64 bit version. There is a problem with the splash screen and sometimes it seems like it might be hanging (ie if checking the hard drive integrity at boot).  It affects both the livecd and boots after being installed.  If you experience the problem on the CD, just boot with safe graphics option or hit f9 or whatever to edit the boot line.  If editing the boot line on the live CD or in grub after it is installed, then remove "splash" from the line and boot and you should be okay.

This is quite frustrating because it should be a very easy bug to fix and it makes a lot of people think something is wrong with their computer.  The bug has been around long before the final Gutsy was released and now, over a month and a half after release it is still not resolved.  I understand that there may be bigger fish to fry but I think there should at least be an temporary solution such as removing "splash" from the boot command automatically so newbies dont have to go digging for it themselves.

---

### Post by Alfusious on 2007-12-01
Thanks for the bit with the splash! Now it loads but hangs at the swooshes backgroung and the hourglass just keeps whirling with no progress.

---

