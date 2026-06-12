---
title: "How To: ATI Drivers OpenSUSE 11.1"
date: 2008-12-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Vince4Amy on 2008-12-23
[FONT="Arial Black"][SIZE="6"]This Guide Is No Longer Maintained, For The New Guide [Click Here](http://grubbn.org/otheros/showthread.php?tid=53)[/SIZE][/FONT]

There have been some problems getting the official fglrx drivers to work on OpenSUSE 11.1, I have made this (rather basic) walk through on how to get them to work correctly. **This Works For 32 & 64-bit Releases**

```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-9-1-x86.x86_64.run
``` - Download The Driver

Run these as Root:

```
zypper in kernel-source gcc make patch
``` - These are the dependencies of the driver, the packages are approximately 70-75MB overall.

```
sh ati-driver-installer-9-1-x86.x86_64.run
``` - Run through the installer choosing the automatic steps

```
aticonfig --initial -f
``` Configure Xorg.

```
sax2 -r -m 0=fglrx
``` Configure Sax2 with the fglrx driver.

Reboot your system and everything should work, you can verify this with (run as normal user):

```
fglrxinfo
```

Updated for 9.1, 64-bit users no longer have to link the 32-bit DRI either 64-bit now works and FPS in 32-bit applications should be working as expected.

---

### Post by Tamjay on 2008-12-24
Thanks!  Worked like a top =).

---

### Post by gjluong on 2008-12-25
Thanks a lot. I wasn't aware about having to configure SaX2 as this isn't required with Ubuntu.

---

### Post by spiritofreason on 2008-12-28
> **Vince4Amy said:**
> ```
rm /usr/lib/dri/fglrx_dri.so && ln -s /usr/lib64/dri/fglrx_dri.so /usr/lib/dri/fglrx_dri.so
``` **- This is for 64-bit users as the Driver will fail to work as it will try to use the 32-bit DRI.**

That will get the 64-bit drivers to work, but emulation for 32-bit will be gone (e.g. for Windows games in WINE).  So far, I only know of this hack, too, though; X won't even load the proper extensions for 3D support if it sees the wrong binary.

If you want 32-bit emulation to work, you'll have to swap back in the 32-bit binary before you start the program (and swap back out when you're done--this is probably going to be nasty if you're using Compiz or something else using the 64-bit driver).

I'm not sure yet whether this is a build script issue or a bug in AMD's code.  I'm probably too lazy to look into it, too... ;-)

---

### Post by gjluong on 2008-12-29
Would this explain why I keep getting 'Segmentation fault' errors when attempting to load a game of Enemy Territory: Quake Wars?

---

### Post by faithfulsoft on 2009-01-01
> **Vince4Amy said:**
> ```
sax2 -r -m 0=fglrx
``` Configure Sax2 with the fglrx driver.

Reboot your system and everything should work, you can verify this with (run as normal user):

```
fglrxinfo
```

When I run sax2 command, I receive this output

```

sax2 -r -m 0=fglrx
SaX: initializing please wait...
SaX: your current configuration will not be read in

SaX: access to your display has been granted
SPP: prepare device [0] profile: FireGL
SPP: prepare device [0] profile: AIGLX
SPP: prepare device [0] profile: Composite
SPP: prepare device [3] profile: synaptics
SPP: including prepared profile(s)...
SPP: prepare device [0] profile: nobus
SPP: including prepared profile(s)...

SaX: startup
SaX: X-Server: :0.0 -> grant

```

And the system hangs there... is this normal?

Thank you

---

### Post by havok1977 on 2009-01-02
Does anyone know what could be the reason why im getting this:

```

# aticonfig --initial -f
Uninitialised file found, configuring.
Segmentation fault

```

The Ati install procedure finished properly, the driver was compled successfully when the RPM was installed; so whats wrong?

---

### Post by spiritofreason on 2009-01-03
> **gjluong said:**
> Would this explain why I keep getting 'Segmentation fault' errors when attempting to load a game of Enemy Territory: Quake Wars?

If you're running 64-bit, then it's certainly a candidate.  There are a number of ways to find out... does fgl_glxgears run?

---

### Post by gjluong on 2009-01-03
> **spiritofreason said:**
> If you're running 64-bit, then it's certainly a candidate.  There are a number of ways to find out... does fgl_glxgears run?

Thanks for replaying. Yes, fgl_glxgears runs at ~4000 fps.

---

### Post by spiritofreason on 2009-01-03
> **gjluong said:**
> Thanks for replaying. Yes, fgl_glxgears runs at ~4000 fps.

If you're using a 64-bit binary for ET:QW, then the bug giving you trouble is different.  The library loading problem prevents hardware 3D support.

You might try searching the forums for quake wars problems and if you don't find anything, creating a thread for your issue (with console output to start things off).  I'd only be stabbing in the dark from here, so hopefully someone else will be able to help. ;-)

---

### Post by fitlad on 2009-01-06
Thanks Vince for the quick howto, it worked like charm with opensuse 11.1 but I had another problem to resolve; getting my webcam configured. As you know, opensuse comunity didn't release gspca binary package due to the fact that gspca is now built in the main stream of the kernel (the same kernel used in fedora core 9), however cheese doesn't recognise my usb webcam. Thus I decided to downgrade my os to opensuse 11. It's more stable though.

By the way, I already posted a thread regarding mplayer error, I wish you could read it and help me if you can. Cheers :-)
[http://ubuntuforums.org/showthread.php?t=1031887](http://ubuntuforums.org/showthread.php?t=1031887)

---

### Post by Vince4Amy on 2009-01-06
> **fitlad said:**
> Thanks Vince for the quick howto, it worked like charm with opensuse 11.1 but I had another problem to resolve; getting my webcam configured. As you know, opensuse comunity didn't release gspca binary package due to the fact that gspca is now built in the main stream of the kernel (the same kernel used in fedora core 9), however cheese doesn't recognise my usb webcam. Thus I decided to downgrade my os to opensuse 11. It's more stable though.

By the way, I already posted a thread regarding mplayer error, I wish you could read it and help me if you can. Cheers :-)
[http://ubuntuforums.org/showthread.php?t=1031887](http://ubuntuforums.org/showthread.php?t=1031887)

Fair enough, it's supported with Security updates until 2010 anyway so you'll be fine using it. I'm still using it on Production systems.

---

### Post by billytex on 2009-01-14
Hey There,

Got openSUSE 11.1 the other day and also have ATI All in Wonder 9600.  Used the 32 bit version of these instructions and am posting from installed version now :)  Thanks much those of you who know Linux!

---

### Post by Vince4Amy on 2009-02-06
Updated for the new ATI Drivers release.

> 
That will get the 64-bit drivers to work, but emulation for 32-bit will be gone (e.g. for Windows games in WINE). So far, I only know of this hack, too, though; X won't even load the proper extensions for 3D support if it sees the wrong binary.

If you want 32-bit emulation to work, you'll have to swap back in the 32-bit binary before you start the program (and swap back out when you're done--this is probably going to be nasty if you're using Compiz or something else using the 64-bit driver).

I'm not sure yet whether this is a build script issue or a bug in AMD's code. I'm probably too lazy to look into it, too...

This is fixed now.

---

### Post by Vince4Amy on 2009-02-08
Update, I've also tried this on the 32-bit version and it works.

---

### Post by vonzipper27 on 2009-02-11
i hate to sound very....new, but i am. I have the 3400 card, and am running 64 bit. The instructions in the first post I am sure are correct, but I do not know how to follow them. Can someone help?

---

### Post by Vince4Amy on 2009-02-12
> **vonzipper27 said:**
> i hate to sound very....new, but i am. I have the 3400 card, and am running 64 bit. The instructions in the first post I am sure are correct, but I do not know how to follow them. Can someone help?

That's fine we all learnt from something after all:). What seems to be the problem?

---

