---
title: "Can't get ATI driver to work"
date: 2006-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ernstblaauw on 2006-12-12
Hi,

On my Edgy Eft installation, I wanted to install ATI drivers for a ATI Radeon 9250 card on my AMD64 computer. So, I used [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Installing_Edgy.27s_Included_Driver_.288.28.8.29"). However, when I restart my computer, my graphical card stops to output a signal when the log in window should have come up. So, I used the recovery mode to restoremy xorg.conf, and then Ubuntu can start in normal mode. However, of course, the driver is not loaded.
Does someone know a solution?

---

### Post by renzokuken on 2006-12-12
could you post the xorg.conf you were using with the ATI driver, if you still have it

---

### Post by juah on 2006-12-12
Check this howto also

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I got the same video card. I've already upgraded once since first installation, but originally I used the packages from ubuntu restricted repos.

Maybe all those fancy actions described in nowadays' howto are needed, but way back then the howto was much easier if I remember right. All I did was

sudo apt-get install xorg-driver-fglrx
echo fglrx|sudo tee -a /etc/modules
sudo dpkg-reconfigure xserver-xorg

and booted with new xdriver (yes, I know they say it's not necessary, but It's not an Issue for me)

The crucial thing here is to give right parameters according to panel's manual. Check fglrx as xserver driver and give proper horiz sync rate and vert. refresh rate. You can get those from your original xorg.conf

Better rely on up to date howtos of course...

---

### Post by ernstblaauw on 2006-12-12
I attached to files: the current xorg.conf and the one which crashed my computer.

I also tried the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
but also then, the graphical user interface will not come up. 

I have to add that my computer does not really crash: there is no GUI, but if I enter my user name and password, I can hear I logged on (but without an interface it is kind of useless)


edit:
I also tried
> sudo apt-get install xorg-driver-fglrx
echo fglrx|sudo tee -a /etc/modules
sudo dpkg-reconfigure xserver-xorg
but then, after pressing ctrl-alt-backspace, if I look with 'fglrxinfo', I see this:
> display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)


I assume the driver is not installed?

---

### Post by renzokuken on 2006-12-13
well its recognised it as a mesa driver, and not fglrx. this is actually a fairly commen problem and there is a solution on one of the guides, i'll see if i can find it for you.

also, interesting that its outputting AGP 1x, that radeon card is capable of AGP 8x. not sure how to fix that though, although it might be solved when the fglrx driver is sorted.

i'll go find that howto for the mesa

EDIT: heres one [http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

---

### Post by ernstblaauw on 2006-12-13
> **renzokuken said:**
> well its recognised it as a mesa driver, and not fglrx. this is actually a fairly commen problem and there is a solution on one of the guides, i'll see if i can find it for you.

also, interesting that its outputting AGP 1x, that radeon card is capable of AGP 8x. not sure how to fix that though, although it might be solved when the fglrx driver is sorted.

i'll go find that howto for the mesa

EDIT: heres one [http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

That guide is not updated for Edgy Eft, which I'm running... It points to another guide, but that's the guide I already followed (see the first post).
However, I'm thinking about reinstalling Ubuntu, but this time  32-bit. That's because I'm just beginning with Ubuntu, and a lot of packages are built for 32-bit. Could it be, that my problem will disappear with a new, 32 bit, installation?

---

### Post by renzokuken on 2006-12-14
possibly but not guranteed.

32 bit is certainly a lot easier to use than 64-bit

---

