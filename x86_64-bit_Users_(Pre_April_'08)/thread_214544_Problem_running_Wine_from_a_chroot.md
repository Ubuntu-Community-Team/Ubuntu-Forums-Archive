---
title: "Problem running Wine from a chroot"
date: 2006-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by amiga_os on 2006-07-12
Hi all!

I'm running Dapper 64bit with a 32bit chroot.  I have 1Gig RAM, and 100Gig HDD.  I'm using an ATI Mobility Radeon 9700 with the proprietary driver from the Ubuntu repos (fglrx for those who don't know).

GLX runs fine, X runs fine, the fglrx driver was installed from a fresh install of Dapper.  The only thing that doesn't work is XGL / Compiz (v. slow and distorted screen), but I've removed that now.

I'm trying to run Wine in the chroot.  I install it from the repos fine, but when I try running wine I get this error:

> pete@pete-laptop:~$ wine
wine: creating configuration directory '/home/pete/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  133
  Current serial number in output stream:  134
wine: wineprefixcreate failed while creating '/home/pete/.wine'.
pete@pete-laptop:~$ wineserver: could not save registry branch to /home/pete/.wine-I8C5PF/system.reg : No such file or directory
wineserver: could not save registry branch to /home/pete/.wine-I8C5PF/user.reg : No such file or directory

This happens when I try to use wine to run exe's too.

I have two questions:

1) How do I make this go away!  I suspect that possibly my chroot installation might need some more packages adding to it (any idea what packages), all I have are the bare bones packages suggested by the chroot HOWTOs: [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) and [http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575) I've added some others to make the chroot look good (ubuntu-art, english language packs etc.)

2) Why on earth is Wine messing around with GLX at all!?!?!?  All it seems to be doing is setting up things for 1st use.  I could understand if I was trying to run the latest FPS, but I just want wine for Bibleworks and a few other non-OpenGL programs.  I'm totally confused!  Help would be appreciated.

---

### Post by Kilz on 2006-07-12
> **amiga_os said:**
> Hi all!

I'm running Dapper 64bit with a 32bit chroot.  I have 1Gig RAM, and 100Gig HDD.  I'm using an ATI Mobility Radeon 9700 with the proprietary driver from the Ubuntu repos (fglrx for those who don't know).

GLX runs fine, X runs fine, the fglrx driver was installed from a fresh install of Dapper.  The only thing that doesn't work is XGL / Compiz (v. slow and distorted screen), but I've removed that now.

I'm trying to run Wine in the chroot.  I install it from the repos fine, but when I try running wine I get this error:



This happens when I try to use wine to run exe's too.

I have two questions:

1) How do I make this go away!  I suspect that possibly my chroot installation might need some more packages adding to it (any idea what packages), all I have are the bare bones packages suggested by the chroot HOWTOs: [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) and [http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575) I've added some others to make the chroot look good (ubuntu-art, english language packs etc.)

2) Why on earth is Wine messing around with GLX at all!?!?!?  All it seems to be doing is setting up things for 1st use.  I could understand if I was trying to run the latest FPS, but I just want wine for Bibleworks and a few other non-OpenGL programs.  I'm totally confused!  Help would be appreciated.
[You do know that you dont have to have a chroot to install wine right?]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by amiga_os on 2006-07-12
> You do know that you dont have to have a chroot to install wine right?

yeah, but how easy is it to uninstall wine if I get the same problem... I'm cool messing up my chroot, but I rely on my main system...

---

### Post by amiga_os on 2006-07-12
> > You do know that you dont have to have a chroot to install wine right?

> yeah, but how easy is it to uninstall wine if I get the same problem... I'm > cool messing up my chroot, but I rely on my main system...

Ok, I repent, just used your script... wow, wow and more wow!

Thanks!

---

### Post by Kilz on 2006-07-12
> **amiga_os said:**
> > > You do know that you dont have to have a chroot to install wine right?

> yeah, but how easy is it to uninstall wine if I get the same problem... I'm > cool messing up my chroot, but I rely on my main system...

Ok, I repent, just used your script... wow, wow and more wow!

Thanks!

Your welcome :D  
Just to let you know, since you used dpkg to force it in, its removable with dpkg.

---

### Post by amiga_os on 2006-07-13
OK, trying to install IE6, but for some reason things are missing from my Wine installation, e.g. using this howto:

[http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)

which expects there to be a file ~/.wine/config but that file doesn't exist!

Then, when I try to install dcom98 (I have an xp license... don't worry I'm legally above board) I get this error:

```
wine --dll ole32=native dcom98
wine: could not load L"c:\\windows\\system32\\--dll.exe": Module not found
```

any ideas?

---

### Post by Kilz on 2006-07-13
> **amiga_os said:**
> OK, trying to install IE6, but for some reason things are missing from my Wine installation, e.g. using this howto:

[http://patrick.spacesurfer.com/ie_wine_install.html](http://patrick.spacesurfer.com/ie_wine_install.html)

which expects there to be a file ~/.wine/config but that file doesn't exist!

Then, when I try to install dcom98 (I have an xp license... don't worry I'm legally above board) I get this error:

```
wine --dll ole32=native dcom98
wine: could not load L"c:\\windows\\system32\\--dll.exe": Module not found
```

any ideas?

Just courious, reading back to your earlier posts you said script. Im hoping that you didnt use the automated setup script I had posted on the main page. It was only up for a few hours before I took it down because of a problem. If you did you may want to just follow the maunal howto to overwrite some of the files.
If not the howto only installs a base wine install. I am thinking of adding how to install a setup script called [sidenet]("http://sidenet.ddo.jp/winetips/config.html") to the howto. But it also can install IE, only problem is its setup isnt compatible with the newest wine.
But anyway, in either case, the best way to install IE with the newer version of wine is a script called [ies4linux]("http://www.tatanka.com.br/ies4linux/index-en.html"). I recommend it above all others. You will have IE up in no time. 
But now that I have told you how to add IE I feel I must warn you. IE isnt safe. It isnt safe even running under wine. If you need it for one or two sites that wont work with firefox or to see how pages you have created look with IE its ok. But please stay safe, dont use it for everyday surfing.

---

