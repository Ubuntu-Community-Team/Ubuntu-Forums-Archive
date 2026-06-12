---
title: "Building/Installing the new ATI drivers"
date: 2007-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ©TriMoon® on 2007-06-04
Hi all,

Because the ati driver that comes with the restricted-drivers package causes my DIVX/XVid video´s to be rendered incorrectly, the colors are messedup (human skins show blueish real alien kind)

I decided to try the latest drivers from the ATI website, v8.36.5 at that time now there is a v8.37.6.
But i have not quite been able to install it to satisfaction.
3D acceleration stays off, with a notice in Xorg.0.log about the kernel module being incorrect.
Although i had uninstalled the restricted-drivers version before this all and build the kernel-driver using module-assistant.
Im also unable to use the AMDCCC/ATICCC

I have uploaded all relevant files here, click image, for those interested.
[[IMG]http://images.rapidshare.com/img/bannersmall1.jpg[/IMG]]("http://rapidshare.com/users/HP69NK")
And i have tried to write down all steps i took, as far as i could remember, in the file "HowTo_Ubuntu-ATI_driver.txt" for both myself and others who are willing to help out...

Im using an ATI-Radeon 1650 Pro...
Anyone any ideas?

---

### Post by Cappy on 2007-06-05
I got that error (the kernel module problem) when I installed my nvidia drivers.
I had to
```

sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*

```
I then installed my nvidia drivers.
When I rebooted after doing that package-removal, I had to go into the recovery mode and reinstalled the drivers from there. Worked after that.

I'm not sure what the ATI equivalent is but you should remove all ati packages (with --purge) and then delete any ATI files that are left over in /etc/init.d/

You can upload to the forum when you post, btw.

---

### Post by ©TriMoon® on 2007-06-06
Thanks for your idea about uninstalling the nvidea drivers.
I have uninstalled a butt-load of packages including the nvidea drivers and restricted drivers pakages, at the time i got fiddling around with the new ATI-drivers.

Xorg finaly cameup correctly using 3D-acceleration whith the v8.37.6 drivers.
But i think i screwedup somewhere along the uninstall path because now i cant get my Wine-game "Voyage Century Online" to work :(
So i´ll just startover and reformat+reinstall Ubuntu once again :D

Anyway here are the links, click image, for the v8.37.6-64bit pakages i generated for us all (myself incl.):
[[IMG]http://images.rapidshare.com/img/bannersmall1.jpg[/IMG]]("http://rapidshare.com/users/HP69NK")

PS: I don´t like to fill forums with files, thats why i prefer off-forum sites that are designed for free file sharing.

---

