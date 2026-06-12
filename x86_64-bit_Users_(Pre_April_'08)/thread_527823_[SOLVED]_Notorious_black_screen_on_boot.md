---
title: "[SOLVED] Notorious black screen on boot"
date: 2007-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Don Giovanni on 2007-08-17
Installed 64bit Ubuntu Fiesty via alternate text install.  Everything seemed to go fine until first boot.

On boot I see "Kernel Alive" "Kernel direct mapping tables up to 100000000@8000-d000" and then get the notorious black screen.
The PC does not respond to ALT-F1 nor CTRL-ALT-F1.   I've tried hitting F6 during boot as well to try the "nosplash noapic nolapic" suggestion I have seen, but unfortunately there is no response to F6.  The only thing I can do is reset from the tower. 

I am able to select recovery mode from GRUB and then startx.   From there I used Envy to install the Nvidia drivers and I manually edited xorg.conf to specify the 1920x1200 native res for my monitor.

Still no change.  Just to see I removed the DVI connection to my monitor and tried using Svideo instead (since it has the input).  Instead of a black screen I get a grey screen boot.

Previously from recovery mode I had also tired sudo dpkg-reconfigure xserver-xorg and went with the VESA driver.  No luck.

I'll attach my current xorg.conf so you guys can take a look. 
Thanks in advance for any help!

System specs
Intel Core 2 Quad Q6600
Mushkin XP2 PC2-8500 2GB 2X1GB DDR2-1066 CL5-5-4-12
ASUS P5K ATX LGA775 P35
EVGA E-GEFORCE 8800GTS 500MHZ 640MB
BenQ FP241W 24IN 1920X1200

---

### Post by happy-and-lost on 2007-08-17
> **Don Giovanni said:**
>  I've tried hitting F6 during boot as well to try the "nosplash noapic nolapic" suggestion I have seen, but unfortunately there is no response to F6.  The only thing I can do is reset from the tower. 


The F6 only works to change boot parameters on the Live CD. To modify it from grub, press "e" to edit your boot parameters, and add delete the "quiet splash" options on the kernel line. Now you should be able to identify the problem, as you'll see the dmesg output.

---

### Post by nowhere.elysium on 2007-08-17
Ah. I had this problem, when I was running a 6300LE in my machine.
I'm afraid that it's something that's interrupting the xorg startup, insofar as I could tell.
I think that there's something in the current range on nVidia drivers that's causing this specific problem. Either 1) wait for a new driver, 2) try out nouveau, or 3) (ironically) get an ATi card. I know that 3) won't be a popular option on this board, but it worked out ok for me: I'm now using an x600 Radeon, without fail. I do a lot of realtime 3D stuff: specifically, I work with Fluxus a lot [http://www.pawfal.org/fluxus](http://www.pawfal.org/fluxus) - as such, I need decent rendering speeds.
Sorry to not have a more positive answer for you, but that's the same brick wall that I ran up against.
the only way that I worked it out was by waiting for about 10 minutes for x to start (which it did, eventually) , and then install bootchart. from there i was able to pont the finger conclusively at x.

here you go: the initial thread showing my progress: [http://ubuntuforums.org/showthread.php?t=484455](http://ubuntuforums.org/showthread.php?t=484455)

---

### Post by jerrylamos on 2007-08-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/132593](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/132593) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I get black screen failure on IBM Thinkpad R31 laptop.  Xwindow support is screwed up on Gutsy Tribe 4.  On Gutsy Tribe 2, correctly uses i810 driver, 1024x768 resolution, depth 24, runs fine.  As Tribe 4 boots it selects VESA driver in either normal live CD boot, or in "safe" graphics mode.  Xorg.conf shows VESA in both cases, resolution none at all!  I was able to use dpkg-reconfigure xserver-xorg once however every time after that the system freezes after the "X" is displayed.  I don't think that's good for the hardware so I won't try again until Tribe 5.

Cheers, Jerry

---

### Post by Don Giovanni on 2007-08-19
> **happy-and-lost said:**
>  To modify it from grub, press "e" to edit your boot parameters, and add delete the "quiet splash" options on the kernel line. Now you should be able to identify the problem, as you'll see the dmesg output.

Thanks for that bit of info.  I was able to log in to a fully functional Gnome environment after deleting quiet splash.  I went and downloaded all available updates, including the newer kernel.  After this I tried rebooting and this time got a no screens found error with the new kernel.  Using sudo dpkg-reconfigure xserver-xorg I was able to install the NV drivers (different than the ones Envy installed I guess), but got the black screen again when i tried rebooting.

Deleting quiet splash again allows the system to boot just fine, and I am able to run everything as I would expect.  I didn't see any error messages.  I looked at dmesg and dmesg.0 in /var/log and couldn't see anything noting major error events.

[   43.952724] lp: driver loaded but no devices found
[   35.018917] ATA: abnormal status 0x7F on port 0x000000000001a887
[   35.303687] PM: Resume from disk failed.

Those  lines are the only ones that sort of jumped out at me here.  I'm not really sure what to look for.  I'll attach both dmesg and dmesg.0. 
[http://www.mts.net/~oggi/dmesg.0.txt](http://www.mts.net/~oggi/dmesg.0.txt)
[http://www.mts.net/~oggi/dmesg.txt](http://www.mts.net/~oggi/dmesg.txt)

I edited grub to permanently have "no splash" removed and I seem to be booting and running fine.  Is everything actually okay or does this just let me bypass some errors that are still there?

---

### Post by Seth on 2007-08-19
The error is in the usplash package (a bug is already filed), so by deleting "splash" you are bypassing the bug. No ill effects, just less pretty.

---

### Post by Don Giovanni on 2007-08-19
> **Seth said:**
> The error is in the usplash package (a bug is already filed), so by deleting "splash" you are bypassing the bug. No ill effects, just less pretty.

That's kind of what I was thinking. Thanks for the help guys, good to have ubuntu up and running on the new machine :D

---

