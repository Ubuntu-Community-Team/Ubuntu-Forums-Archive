---
title: "No root password"
date: 2005-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by speedbird on 2005-03-11
Having finaly sorted out that the ASUS A8V motherboard doesn't work with Ubuntu until you disable the onboard LAN in BIOS ( Marvell Yukon Gigabit Ethernet ) I now boot up and the login screen is just a jumble of colours. The first time I logged onto the system fine but on the second occassion this happened. To get around this I try to boot in recovery mode but this requires one to be logged on as root. This option appears to be specifically denied in this distro. Anyone any ideas how to get around this problem or what the default root password is?

---

### Post by eternity on 2005-03-11
[QUOTE=speedbird]Having finaly sorted out that the ASUS A8V motherboard doesn't work with Ubuntu until you disable the onboard LAN in BIOS ( Marvell Yukon Gigabit Ethernet ) I now boot up and the login screen is just a jumble of colours. The first time I logged onto the system fine but on the second occassion this happened. To get around this I try to boot in recovery mode but this requires one to be logged on as root. This option appears to be specifically denied in this distro. Anyone any ideas how to get around this problem or what the default root password is?[/QUOTE]

You have to log in as a normal user and run:
sudo passwd

If you are unable to log in as a normal user you can boot up the livecd and mount the partition you have ubuntu on and from there chroot to your ubuntu partition. If you aren't familiar with linux this is a rather complicated task.

---

### Post by bored2k on 2005-03-11
Deja Vu
[http://www.ubuntuforums.org/showthread.php?t=19264](http://www.ubuntuforums.org/showthread.php?t=19264)

---

### Post by speedbird on 2005-03-11
Thank you both I will try those suggestions.

---

### Post by bored2k on 2005-03-11
[QUOTE=speedbird]Thank you both I will try those suggestions.[/QUOTE]
 Welcome to the Forums.

---

### Post by speedbird on 2005-03-11
Yes that worked. I am now at root after using the install disk (the sudo thing didn't work for some reason ) I am now at a bit of a loss to know how to correct the video settings that are obviously corrupting my startup. Is there a how to page on this somewhere?

---

### Post by kubla on 2005-03-11
[QUOTE=speedbird]Yes that worked. I am now at root after using the install disk (the sudo thing didn't work for some reason ) I am now at a bit of a loss to know how to correct the video settings that are obviously corrupting my startup. Is there a how to page on this somewhere?[/QUOTE]
 There should be info on this around; however, you can probably also try running, as root:

/usr/X11R6/bin/xorgconfig

That should step you through a configuration for your graphical card.

You should take note of a few important pieces of information first though:

1) which graphics card you have
2) what your monitor's display capibilties are.

You can find out 2 by running:

ddcprobe and noting the output.

Lots of useful information on configuring X can be found here:

[http://www.oreilly.com/catalog/runux3/chapter/ch10.html](http://www.oreilly.com/catalog/runux3/chapter/ch10.html)

---

### Post by speedbird on 2005-03-11
Thanks for the advice. I have an ATI sapphire 9200 graphics card and the monitor is a Viewsonic VX910 LCD screen which has a preferred mode of 1280x1024. I have tried /usr/X11R6/bin/xorgconfig but that doesn't exist. I tried the xf86config and xf86cfg which were there but the BASH shell just reported command not found. Do I have to use an editor to edit these files?
Thanks.

---

### Post by mips on 2005-03-11
> Do I have to use an editor to edit these files? 

Yes.

sudo nano <filename>

cheers
mips

---

