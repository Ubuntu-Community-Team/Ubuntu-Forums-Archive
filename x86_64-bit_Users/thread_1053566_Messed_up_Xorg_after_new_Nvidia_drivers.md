---
title: "Messed up Xorg after new Nvidia drivers"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by .Maleficus. on 2009-01-28
Today in my coffee-deprived internet roaming I ran across a thread mentioning the 180.22 Nvidia drivers.  Remembering I hadn't yet installed them, I decided to download and go for it.  After what I thought was a successful install, Xorg told me that it was still loading the kernel module for the 177 driver and not the 180.  During the install, the driver didn't find any precompiled modules for my system (which I thought was strange) so apparently it built one for me.  I don't know why it isn't being loaded if it's there, but it's not.  I tried to revert to my previous Xorg.conf but I got the same message (loading the same driver I assume).  I wish I could solve this one myself but I'm stumped.  Any ideas?

Thanks guys.

---

### Post by Spr0k3t on 2009-01-28
How did you install the 180.22 drivers?  Link to the thread would help.  Also, if you don't have the right kernel specifics for the binary driver, you won't be able to load the needed drivers for the kernel build.

All this would be a thing of the past if Nvidia would distribution open source drivers.

---

### Post by .Maleficus. on 2009-01-29
I didn't follow any specific guide from a thread, just the mention of the driver reminded me :).

Anyways, I just downloaded the installer from Nvidia's website (NVIDIA-Linux-x86_64-180.22-pkg2.run), logged into vc/1 and ran it as root.  I didn't get any kinds of errors so I figured it worked, but I guess it didn't.


Edit:  Of course, now I find out that the drivers are in the repos.  Downloading and installing now.

---

### Post by williane on 2009-01-29
Any updates on this? I'm having a similar issue. :(

---

### Post by Strid on 2009-01-29
Me too! I tried to install the ubuntuish drivers in the System>Administration>Hardware Drivers. I installed the 177 driver - didn't work, so I deactivated them. That was slightly better. Now I can log in with full resolution, but still crummy without any real Nvidia driver - movement of windows and such isn't smooth.

Sucks!! Wonder what to do now.

---

### Post by .Maleficus. on 2009-01-30
Unfortunately, no.  I thought I may have just fixed it, but I was wrong.  After installing the 180 drivers via Synaptic, I rebooted using the nv driver and got a notification that there were restricted drivers available (and 180 was one of them).  I checked the box to Activate, rebooted and X failed to start once again.  I don't have time now to look further into this but when I get home from school I'll do a little more digging.

---

### Post by PTrenholme on 2009-01-30
Have you rebooted since you did the build? The older kernel module should be removed, but sometimes it isn't.

If you still have the problem after a reboot, boot into rescue mode and select the root prompt option. (You can actually do this from the "low graphics screen if you prefer to work in a GUI environment. Just open a terminal window and enter the commands. If you don't want to type **sudo** before the commands needing **root** access, you can enter the command **sudo su -** to start a sub-shell as **root**.)

First, check to see if you have any of the older 177 driver files around:```
# **locate -r 'nvidia.*177...$'**
```
That command should return the path to any files whose name ends with 177 followed by exactly three characters. Here's what I see on my system for the 180.25 driver I have installed.```
**$ locate -r 'nvidia.*180...$'**
/usr/lib/libnvidia-cfg.so.180.25
/usr/lib/libnvidia-tls.so.180.25
/usr/lib/libvdpau_nvidia.so.180.25
/usr/lib/tls/libnvidia-tls.so.180.25
/usr/lib/xorg/modules/libnvidia-wfb.so.180.25
/usr/lib32/libnvidia-tls.so.180.25
/usr/lib32/libvdpau_nvidia.so.180.25
/usr/lib32/tls/libnvidia-tls.so.180.25
```(Note that I'm running Jaunty 9.04 beta with the 180.25 driver, so my output will, obviously, be different from what you will see.)

If you see any files in the list, you'll need to remove them from your system. (If you don't see any, then I haven't a clue about how you've got a 177 driver loaded.)

Now do a **ls /usr/lib/xorg/modules** and look in the output for either a **nvidia.so** file or a **nvidia/** subdirectory. If you have the **nvidia/** subdirectory, do a **ls -l /usr/lib/xorg/modules/nvidia** to see where the symbolic link in the directory points. (The **nvidia.so** file is the driver that the X-server loads when it is started.) If it's pointing to your new **180** file, you can proceed with deleting the old 177 stuff. If it's still pointing to the 177 stuff, then you'll need to replace the symbolic link with a new one pointing to your newer 180 stuff.

If you feel you can remove everything that was listed by the locate command, you can do so with a **rm -f $(locate -r 'nvidia.*177...$')** ([color=red]**Caution**[/color]: You are running as root, so any typos in that command can have _catastrophic_ consequences. Look _very_ _carefully_ at the output of the preceding **locate** command, because _every_ file listed there will be deleted when you run the **rm** command.)

Now, the final step is to update the module dependency tables to refelct the changes you've made. Issue the command **depmod**, wait 'till it finishes, and reboot with the **reboot** command.

**[color=red]Final Warning[/color]**: If this is not clear, or you have _any_ questions, do _not_ follow these suggestions. As I said above, you'll be running as **root**, and it will be very easy to convert your system into a re-installation training exercise.

---

