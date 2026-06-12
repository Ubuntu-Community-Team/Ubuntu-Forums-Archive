---
title: "No yaboot? B&amp;W G3"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by outofnicks on 2006-03-04
My first attempt to intstall 5.10 dual-boot with Jaguar on a B&W G3 seemed to go well, all the way to the end where I hear the little drum slap (sweet, is that a djembe or ashiko?) The last bit of text I remember seeing in the output was about Gnome cannot be initiated, or something to that effect. Then a black screen, with just an underscore at the top.
Any keyboard input had no effect, I tried Ctrl-Opt-F1 and all the other Fkeys to try and get to shell, no luck.
So I did the 3-finger salute restart, and it booted back into OS X without the boot screen giving a choice that I thought I should expect. Another restart with just the option key, same thing. Next I zapped the PRAM, 3 times, still no joy.
Booting into Open Firmware, I tried the command boot hd:disk0s9 with the answer of "can't OPEN: hd:disk0s9".
Searching for clues in the forums, It seems that I should have installed the yaboot files before booting the install CD--is that correct? But I distinctly remember during the install seeing Yaboot being configured, it hung on that for something like 5 minutes.
I also found another thread on the black screen with underscore, with the advice given to lower the screen resolution. I believe I'd edit the /etc/X11/xorg.conf file to fix that, right?
Anyway, I can't even get to that point, since it only boots to OS X. 
I tried the live CD but it doesn't even appear on OS X although I can boot back into the install CD. Just not sure what to do next, can someone point me in the right direction please?

---

### Post by outofnicks on 2006-03-05
Progress---
I found the correct command in OF to get to yaboot, it was
 boot hd:9,yaboot 

My original failure to get to a shell from the black screen was due to a faulty keyboard, I found another one and succeeded. Getting to the shell, that is. The Gnome Display Manager still won't start.
So I edited xorg.conf a few times (made a backup of the original first) by deleting the higher resolutions under Monitors, leaving 800x600, and adding 640x480 at the default bit depth which was 24. When that didn't work (using the command /etc/init.d/gdm restart) I repeated the resolution change, moving down to 16 bit depth, then 15, and finally 8 but still no gdm--just the black screen with an underscore.
At least I got into Ubuntu, but how can I get into Gnome?
Thanks for any help in advance.

---

### Post by jdp on 2006-03-05
You can try using the automatic xorg.conf file setup with the commands **sudo dpkg-reconfigure xserver-xorg**.  You should be able to at least start Gnome with **startx** if GDM isn't/won't run.  THat'll let you test your changes to the config file.

---

### Post by outofnicks on 2006-03-05
Well, I followed your advice and went through the reconfigure, probably should have just accepted all the defaults--but no, I had to change the video card type without really knowing what I was doing. I think that was the only one, it was very detailed and took a few minutes so can't remember it all.
Then it was done and saved, so I typed startx and was told the display manager was already running! So I typed sudo /etc/init.d/gdm restart and that brought me back to the black screen. Didn't hear the little drum slap I'd heard before at this point, and Ctrl-Opt F1 didn't work at all. After about a minute, it rebooted on it's own back into OS X.
I'll try booting back into Ubuntu one more time and do the auto xorg setup again, and see if accepting all defaults will help. If not,  then will probably do a reinstall--only takes an hour. It's a learning experience, anyway--thanks for the help!

---

