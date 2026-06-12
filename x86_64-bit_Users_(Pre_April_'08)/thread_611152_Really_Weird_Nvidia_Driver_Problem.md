---
title: "Really Weird Nvidia Driver Problem"
date: 2007-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by H4x3r on 2007-11-12
hey guys, i am having a really weird issue with my Gutsy(64bit version) install. After having enabled the 100.14.19 nvidia drivers in restricted drivers, i got the big bad freezing problem. So i disabled the restricted drivers, and used Envy to remove any references the the old driver....I use an AMD x2 4200+ with 7300LE graphics card, and i decided to install the 100.14.09 driver. Well i installed that driver all went well, everything ran smoothly installed compiz-fusion and it worked like a dream....then...i restarted my machine (for the first time after the install) and when it comes back up it's in really low resolution, and when i log in it says in the Graphics and Screens menu that it is using the Vesa Generic drivers for it, but here is the weird thing. In xorg.conf the driver is "nvidia" no references to nv or vesa are there, as well the restricted drivers manager still shows it as being enabled. When i run glxinfo it shows nothing and glxgears doesn't work either...i've searched asked searched and asked some more trying to fix this...and after hours of frustration i've almost given up...but i will keep going until i fix this issue....if anyone has this same problem i would be most appreciative if you could help me...thanks many times for the help guys.

---

### Post by kafiend on 2007-11-13
Hi, I had similar issues with my Ati card - this thread might help you. All my drivers were allegedly working but fglrxinfo said mesa.  Anyway after much frustration i found this

[http://ohioloco.ubuntuforums.org/showthread.php?t=569654](http://ohioloco.ubuntuforums.org/showthread.php?t=569654)

 I had to follow the part of the guide titled "If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before."  in order to remove everything and start over.

Of course yours is Nvidia and the guide is for Ati but some of it might help you on your way.

Best of luck

---

### Post by dabl on 2007-11-13
That is weird.

If you run it as user and get logged in, you might try letting the Nvidia driver overwrite the xorg.conf file.

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Then you can run (as root, one time) the nvidia-settings utility to change the default resolution and refresh rates to what you want upon logging in:

```
sudo nvidia-settings
```


By the way, make sure you do NOT have the package xserver-xgl installed -- if it is, remove it.  It will bork up your compiz attempts.  :)

---

### Post by H4x3r on 2007-11-13
thanks for the help, but i have discovered that for some reason the xserver always seems to default back to xorg.conf.failsafe no matter what i do, even when i let the nvidia driver write the xorg.conf....i'm going to try the 32bit version today and see what happens....thanks for the help fellows

---

### Post by dabl on 2007-11-13
No problem.

Hmmmmm -- there's no reason that kind of problem should be related to the architecture of the OS.  But hey, if it works when you install 32-bit, just go with it!  :)

---

### Post by d1ss0nant on 2007-11-13
The same thing happened to me!  I use 64 bit Gutsy Gibbon and I had that happen when using my external monitor.  I did resolve it, but I'm unable to remember how for some reason.  It was definitely through info taken from these forums though - If i can find it again I will post the thread.

---

