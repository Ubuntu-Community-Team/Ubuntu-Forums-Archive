---
title: "Crash/freeze during anything really"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2006-11-22
Ok well I installed Ubuntu on my computer and now I'm having a little bit of a problem, at different times during use of the OS it locks up or freezes and I have to restart.  The screen seems to shift a little and if there were words on the screen you can't make out what they say.  I'd really like to be able to use Ubuntu (BTW I have dual boot with windows Xp Pro)

---

### Post by glenn45 on 2006-11-22
maybe its your X windows. search the forum about how to fix it. do you have nvidia or ati graphics card?

---

### Post by DaGGer on 2006-11-22
I have Nvidia, I have a EVGA 7800GT.  Here are my system specs:

Mobo: MSI K8N Neo4 Platinum
Processor: AMD 4200+ X2
Ram: Crucial (2gigs 4x512 sticks) value select
HD: Western Digital 160gig W/ 16mb buffer
Video card: EVGA 7800Gt

And I don't know a whole lot about linux but I do know quite a bit about computers and I don't know what X is.

---

### Post by DaGGer on 2006-11-23
well I tried to use this program Automatix and it didn't work at all.

---

### Post by DaGGer on 2006-11-23
no one can help me out with this, I forgot to add that i can move my mouse when it freezes/crashes

---

### Post by John Jason Jordan on 2006-11-23
> **DaGGer said:**
> no one can help me out with this, I forgot to add that i can move my mouse when it freezes/crashes
I'm betting it's the graphics driver. I have NVidia chipset also, and at least once every couple of weeks the whole display locks up. I'm using the "nv" (open source) NVidida driver. In the past I have used the proprietary driver from NVidia for a brief time. I think I am going to switch to the NVidia driver and see if it works better.

---

### Post by DaGGer on 2006-11-24
alright well can you please tell me how to install these drivers please.

---

### Post by RAOF on 2006-11-24
From a terminal:
```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```

The first line installs the nVidia drivers from the repository.  The second modifies xorg.conf to use the new drivers, the third restarts the GUI so the new drivers get loaded.

Be aware, the third line will restart the GUI.  You will be logged off.  Any unsaved work you have open will **not** be saved.

---

### Post by DaGGer on 2006-11-24
alright well I tried to follow those directions but after i put the first line of code in I get this error

"Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted nvidia-glx 1.0.8762+2.6.12.11-3

Temporary failure resolving 'security.ubuntu.com'

---

### Post by DaGGer on 2006-11-24
come on, after this I'll actually be able to use linux instead of Windows almost full time.

---

### Post by incubus on 2006-11-24
That's weird.  Is your Internet working?  Can you update and install other packages normally?  Can you:

```

$ ping security.ubuntu.com

```

incubus

---

### Post by incubus on 2006-11-24
EDIT:
You will need other packages as well.  If aptitude or apt-get are still not working, you have to download the packages pointed by Sukarn in the next post and follow the same procedure for installing them.

=============================

If you can't figure that out, you can also download the nvidia package from packages.ubuntu.com.

Here's the link:
[http://packages.ubuntu.com/dapper/x11/nvidia-glx](http://packages.ubuntu.com/dapper/x11/nvidia-glx)

I'm assuming you're running Dapper.  To download, you just have to click on the platform at the bottom of the page.  When you have the package in hand, you can issue:
```

$ sudo dpkg -i nvidia-glx*.deb

```

Then follow the rest of RAOF's instructions.

incubus

---

### Post by Sukarn on 2006-11-25
Dont you think he needs the linux-restricted-modules-*[kernel-version]* package for his specific kernel as well as the nvidia-glx package if he gets them directly from the packages.ubuntu.com site?

To me **sudo aptitude install nvidia-glx** gives the output that its installing the following packages -
* binutils-static
* linux-restricted-modules-2.6.17-10-generic
* linux-restricted-modules-common
* nvidia-glx
* nvidia-kernel-common

---

### Post by incubus on 2006-11-25
Good point, I didn't think about that. I'll change my post to avoid confusion.

incubus

---

### Post by DaGGer on 2006-11-26
alright well I downloaded the AMD64 nvidia-glx package but I couldn't extract it.  It said there was an error.  I don't get whats going on with this stuff, and yes my internet does work.

---

### Post by RAOF on 2006-11-26
You should be able to just try again the apt-get way.  The "Temporary failure resolving 'security.ubuntu.com'" error should be temporary :).

---

