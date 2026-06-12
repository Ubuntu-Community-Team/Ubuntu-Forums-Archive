---
title: "wine on amd64"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by bluppfisk on 2006-07-11
Any ideas how to run windows programs (StarCraft !!) in Ubuntu for amd64? winE is apparently incompatible with my architecture. fiddlesticks.

---

### Post by RAOF on 2006-07-11
I'm too lazy to link to a howto, so I'll just give the edited highlights :)

1) Manually download an i386 .deb from the wine site.
2) **sudo dpkg --install --force-architecture *wine_filename.deb***
3) Manually download i386 deb from packages.ubuntu.org for libXxf86vm
4) Extract the .so file from this deb (using file-roller, or whatever) and copy it to /usr/lib32

If you've any problems with the above, post back.  Hopefully Kilz will link to his howto :)

---

### Post by bluppfisk on 2006-07-11
Hi mate! I found the HOWTO yet there's trouble there. APparently I have no OpenGL enabled on my SiS 760 video adapter and there's where Wine crumbles. Any ideas on how to do this? Or should I just use VMWare and install win 98 or XP. Will hardware acceleration work in Windows XP with VMWare if it doesn't in the parent OS, Linux?

---

### Post by RAOF on 2006-07-11
> **bluppfisk said:**
> ...
Will hardware acceleration work in Windows XP with VMWare if it doesn't in the parent OS, Linux?
No, definitely not.

What sort of capabilities does that SiS card have, anyway?  Ok, it seems fairly recent, so it should have **some** sort of GL capabilities :).  Check out the SiS website, check if they have some linux drivers.  If they don't, then by the look of the [Xorg driver wiki page]("http://xorg.freedesktop.org/wiki/sis?highlight=%28sis%29") you're out of 3D acceleration luck.

I'm surprised that wine dies without GL, though.  Perhaps you could install the mesa software GL library, although I have no idea whether that would work or not.

---

### Post by bluppfisk on 2006-07-11
Afaik, the card is compatible with DirectX8 cards so I figured it has GL support, and drivers are included with Ubuntu (I mean, it recognised it, and it says SiS in my xorg.conf file and some package with sis drivers has been downloaded and installed during installation) but I just don't seem to have hardware acceleration.

(are DRI and GLX incompatible with each other mayhap?)

tell me more about mesa software GL library, perhaps that's the issue. I don't suppose StarCraft needs 3D Acceleration anyway.

---

### Post by RAOF on 2006-07-11
It looks like the SiS driver does not support the 3D capabilities of your card.  The driver can work with the 2D part, just not the 3D stuff.

You might want to try installing the **libgl1-mesa-swrast** package.  It seems to provide a software-rendered OpenGL library.  Maybe that will work for you.

---

### Post by Kilz on 2006-07-11
> **RAOF said:**
> I'm too lazy to link to a howto, so I'll just give the edited highlights :)

1) Manually download an i386 .deb from the wine site.
2) **sudo dpkg --install --force-architecture *wine_filename.deb***
3) Manually download i386 deb from packages.ubuntu.org for libXxf86vm
4) Extract the .so file from this deb (using file-roller, or whatever) and copy it to /usr/lib32

If you've any problems with the above, post back.  Hopefully Kilz will link to his howto :)

[I sure will :D]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by bluppfisk on 2006-07-11
> **RAOF said:**
> It looks like the SiS driver does not support the 3D capabilities of your card.  The driver can work with the 2D part, just not the 3D stuff.

You might want to try installing the **libgl1-mesa-swrast** package.  It seems to provide a software-rendered OpenGL library.  Maybe that will work for you.

I've done so now. Quite a bit of stuff appeared on my screen because I had to remove the original libgl1 (dependency trouble mostly: like hey, tuxracer depends on libgl1-mesa, so I will probably have trouble installing new stuff that needs libgl1).

Anyway, let's see how the cookie crumbles. Should this work right outofthebox, or what should I do next to make things work?

CHeers
Sandr

---

### Post by bluppfisk on 2006-07-11
Update: 
great gods yes. I can run Glxgears (at an enormously low speed but hey). winecfg won't work though. :/

this is what it looks like:
> wine: creating configuration directory '/home/sandr/.wine'...
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  3318
  Current serial number in output stream:  3319
wine: wineprefixcreate failed while creating '/home/sandr/.wine'.
sandr@loki:~/Desktop$ wineserver: could not save registry branch to /home/sandr/.wine-rXQGKY/system.reg : No such file or directory
wineserver: could not save registry branch to /home/sandr/.wine-rXQGKY/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/sandr/.wine-rXQGKY/user.reg : No such file or directory


---

### Post by RAOF on 2006-07-11
Ok, I'm out of options.  Perhaps you could ask the wine guys (winehq.com) why it won't work without opengl.  I can't really see any reason it shouldn't.

---

### Post by Kilz on 2006-07-13
While trying to find a solution to another problem I may have found one for this post. [Sidenet]("http://sidenet.ddo.jp/winetips/config.html") is a wine setup script. It sets up almost everything including cdroms, and a virtual c drive in your home folder. I was testing it out on a virtual machine without a graphics setup. It had the 
"fixme:wgl:X11DRV_setup_opengl_visual Failed to find a suitable visual"
error, and winecfg wouldnt start. But when I installed sidenet the error is still there but winecfg starts up.

---

