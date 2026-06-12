---
title: "Fixes for 64 bit Ubuntu on Dell Precision M4300"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bensode on 2008-03-10
I just spent the last couple hours doing a fresh install of Ubuntu 7.10 Gutsy 64 bit on my Dell Precision M4300 laptop and wanted to post the results of the quirks and workarounds that made (so far) everything work.  This is a collection and highlights from other peoples posts -- I just chose to consolidate and comment.

1) First problem was detecting the laptop display.  When booting with the live CD my laptop display was never detected and I was not able to safely configure it manually.

  Workaround : Plug in an external monitor then boot to the LiveCD.  After the Ubuntu splash screen the laptop display went black and the status light on the external lit up.  I let it chew for about 3-4 minutes and it came up nice and clear on the external monitor, however the laptop display remained dead.  I completed the install from the external monitor and rebooted (still using the external monitor).  I enabled the Nvidia binary driver through System - Administration - Restricted Drivers Manager and rebooted once again.  This time, I got my display on the laptop at the right resolution 1920x1200 50Hz and was able to run nvidia-settings to enable a seperate X session for my external monitor.  I use separate X sessions because of the different geometry of my external monitor.

2) No sound after installation.  The Dell Precision M4300 uses the [Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

  Fix : Followed the steps from the wiki link above and found that Method G worked the best.  Enable the backports then sudo aptitude install linux-backports-modules-generic, then reboot.  No need to edit the alsa-base as I have not experienced the ever-increasing-volume bug.

3) Vmware Workstation 6 (64 bit) "Unable to change virtual machine power state: Failed to connect to peer process."

  Fix : sudo aptitude install ia32-libs.  This installed a total of 7 packages for about 90M of files but now I can run the Vmware Workstation 6.0.2 in 64bit environment.

I hope that this helps someone else down the road with a Precision M4300 to get Ubuntu 64 bit rolling much faster than I did!  If I happen to find any other issues down the road I will edit this post.  Good luck!

4) Cisco VPN client : Executing vpnclient connect (profile) File or directory not found

 Fix : Install the ia32-libs package.  If you have Vmware you already needed this but if you don't run Vmware but want 64 bit vpn client, install ia32-libs and the required libs are available and the vpnclient runs.  If you need help on locating and installing the 64 bit Cisco client see this [http://forum.tuxx-home.at/viewforum.php?f=15](http://forum.tuxx-home.at/viewforum.php?f=15)

5) Cisco VPN client + Intel binary wifi driver = still broken.  I haven't found this fix yet but when enabling the Cisco VPN while using the Intel wireless binary driver, I get a hard lockup with the capslock & scrolllock indicators flashing.  Can't recover from it without a hard reboot.

Bensode

---

### Post by dcstar on 2008-03-21
> **bensode said:**
> I just spent the last couple hours doing a fresh install of Ubuntu 7.10 Gutsy 64 bit on my Dell Precision M4300 laptop and wanted to post the results of the quirks and workarounds that made (so far) everything work.  This is a collection and highlights from other peoples posts -- I just chose to consolidate and comment.
.........
4) Cisco VPN client : Executing vpnclient connect (profile) File or directory not found

 Fix : Install the ia32-libs package.  If you have Vmware you already needed this but if you don't run Vmware but want 64 bit vpn client, install is32-libs and the required libs are available and the vpnclient runs.  If you need help on locating and installing the 64 bit Cisco client see this [http://forum.tuxx-home.at/viewforum.php?f=15](http://forum.tuxx-home.at/viewforum.php?f=15)


Thanks for the info on getting the Cisco VPN client working on 64 bit, this was annoying me.....

For anyone else, download the patch file from that other link into the Cisco VPN client software for Linux **vpnclient** directory, and then run these commands to compile to software::

```
patch <*patch
./vpn_install
```

Then the HOWTO here can be used to connect to a VPN:

[http://ubuntuforums.org/showthread.php?t=298181](http://ubuntuforums.org/showthread.php?t=298181)

---

### Post by bensode on 2008-03-21
Good update David.  Now that I think about it I don't remember if I applied that patch on my version of the client or not.

---

### Post by tvtech on 2008-04-20
which video card did you get. I'm thinking of buying this laptop and doing the same thing.  but I'm going for the intel wireless card.

---

### Post by bensode on 2008-04-20
I chose the Nvidia Quadro FX 360M (Mobile).  I had to use the binary driver to get it to work corectly with dual screens.  So far it has been working great, except for the Cisco client not working with my Intel wireless.  When I activate the VPN and connect it works fine but whenever I attempt to connect to anything I get a complete lock-up with the capslock and scrolllock flashing.  I know this means a driver crash but haven't been able to narrow it down.

---

### Post by fsckedagain on 2008-05-18
I have the same video card on my m4300, but I cannot get the drivers to work. I just get a white screen and a black bar. 


I am running Hardy, but which driver are you using?

---

### Post by bensode on 2008-05-18
Very odd Hardy worked for me right from boot and installation.  I'm using the binary nvidia driver for 3d support but the open source nvidia worked through the installation for me.

---

