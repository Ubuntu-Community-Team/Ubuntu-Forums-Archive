---
title: "Problems editing xorg.conf"
date: 2009-04-12
forum: x86 64-bit Users
---

### Post by DJDarknez on 2009-04-12
Sorry to post this here, but the kubuntuforums.net website is broken in a weird way.  Something with cookies.

I'm trying to edit xorg.conf to get a higher screen resolution than 800x600 (which looks pretty small on a 22" screen running 1680 x 1050).  Only problem is that the xorg.conf file looks very different from what I've seen (as screencaps) on the forums.

I've got more problems to take care of after that (I'm running Kubuntu in Sun xVM VirtualBox and it won't update anything at all) but that's after I can get this to a usable screen res.

I've used Kubuntu lightly in the past, but I'm still pretty much a noob when it comes to this stuff.

---

### Post by sanderj on 2009-04-13
1) Editing xorg.conf is so last-millenium. I wouldn't do that at all.

2) you're using Kubuntu in a VirtualBox VM, right? If so, and you want a higher resolution, the VM first has to provide that to the guest OS (=kubuntu). To achieve that, you need to install the Guest Additions. See [http://www.dreamincode.net/forums/showtopic76340.htm](http://www.dreamincode.net/forums/showtopic76340.htm) . "Now start the Ubuntu virtual machine. When the Ubuntu OS is completely loaded, make sure the mouse is not being captured by the guest environment (if it is, press the right Ctrl button to release capture). Navigate through the Devices menu (in the top bar of the VM windows, sanderj) to reach the Install Guest Additions option."

---

