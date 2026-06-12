---
title: "CPU usage over 100%"
date: 2008-12-24
forum: x86 64-bit Users
---

### Post by kristian_k on 2008-12-24
Hi,
I just installed Ubuntu 8.10, it took about 7hours to finish installing & after boot it is still very slow. I discovered that the reason may be because the CPU is running at over 90% to 100% and I have no apps running, the boot takes about 2min. It is an 64bit Ubuntu. It is like that from the start, very slow performance, please HELP!!

thx!!

My configuration:

[U][COLOR="DarkOrange"]Athlon64 X2 TK-57
4GB RAM
250GB hard disk
ATI X1250[/COLOR][/U]

---

### Post by 2hot6ft2 on 2008-12-24
Believe it or not the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing freezes. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

This may or may not be your particular issue but it's where I would start after reading everything I have.

---

### Post by kristian_k on 2008-12-24
> **2hot6ft2 said:**
> Believe it or not the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing freezes. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

This may or may not be your particular issue but it's where I would start after reading everything I have.

thx, I will follow the instructions & report back.
However I do not have any problems with sound, will check it anyway.

---

### Post by cariboo on 2008-12-24
I would suggest opening a Applcations-->Accessories-->Termianl and type:

```
top
```

and have a look to see what process is using all your cpu cycles. See screenshot

Jim

---

### Post by kristian_k on 2008-12-24
I tried the monitor and here are the screen shots

[[IMG]http://img246.imageshack.us/img246/82/slika2hb1.th.png[/IMG]](http://img246.imageshack.us/my.php?image=slika2hb1.png)[[IMG]http://img246.imageshack.us/img246/6004/slika3jh7.th.png[/IMG]](http://img246.imageshack.us/my.php?image=slika3jh7.png)[[IMG]http://img212.imageshack.us/img212/4469/slika4ps6.th.png[/IMG]](http://img212.imageshack.us/my.php?image=slika4ps6.png)

-They don't make sense to me ... in terminal the CPU is used about 60% and in system monitor 96% & 97%, I was not running any other apps during the screenhost besides the system monitor and terminal .. hardly enough for such usage


also I read 2hot6ft2's link but it seams I do not use Pulse Audio, in the Sound Preferences the sound capture is set to ALSA not Pulse Audio, also if I type 'pavucontrol' in terminal it says that it is not installed so I don't think this is what's causing my problem.

---

### Post by sleepyjon on 2008-12-24
xorg looks like it's eating all the cpu, do you have the correct graphic drivers installed?

---

### Post by kristian_k on 2008-12-24
> **sleepyjon said:**
> xorg looks like it's eating all the cpu, do you have the correct graphic drivers installed?

yeah I just came to that conclusion myself ... Xorg seams to eat it all up. I installed the 64bit version driver for my card ATI X1250 from ATI's official site and nothing changed.

---

### Post by kristian_k on 2008-12-25
ok.. me again.. I'm starting to get desperate ... installed and tried everything possible to fix xorg, installed drivers, updated system... so now the CPU usage for Xorg is down to 15%
but the problem is still here, every process i start uses up over 90% of the CPU rendering any wish to do some work impossible. Also you can hear the processor working very loudly (for a laptop) and this starts exactly as the boot screen for Ubuntu appears.
What should I do? help please...

---

### Post by John Jason Jordan on 2008-12-25
> **kristian_k said:**
> ok.. me again.. I'm starting to get desperate ... installed and tried everything possible to fix xorg, installed drivers, updated system... so now the CPU usage for Xorg is down to 15%
but the problem is still here, every process i start uses up over 90% of the CPU rendering any wish to do some work impossible. Also you can hear the processor working very loudly (for a laptop) and this starts exactly as the boot screen for Ubuntu appears.
What should I do? help please...

The fact that it took seven hours to install tells me that there is something wrong with the initial installation. It should take an hour or less.

I would wipe out the installation and start over. I mean start over by downloading the ISO anew and burning a new install CD. Check the md5sums to be sure it is a good download.

---

### Post by kristian_k on 2008-12-25
> **John Jason Jordan said:**
> The fact that it took seven hours to install tells me that there is something wrong with the initial installation. It should take an hour or less.

I would wipe out the installation and start over. I mean start over by downloading the ISO anew and burning a new install CD. Check the md5sums to be sure it is a good download.


I tried 3 different sources already, 

ubuntu-8.10-desktop-amd64.iso
ubuntu-8.10-desktop-i386.iso
ubuntu-8.10-dvd-amd64.iso

the funny thing is that the iso from ubuntu.com for 64bit version doesn't even want to install. It says error reading boot sector after I press install and the only option is to reboot.
I already thought that a piece of hardware was malfunctioning so I tried ubuntu 8.04 and it works fine but thing is I don't want to use 8.04 because it can't connect to the wireless connection in my college.
Bottom line is .. Ubuntu 8.10 doesn't work ... 
are there any kernel or CPU drivers/updates I can try ... ?

also if someone can give me a link to download a _tested_ copy of Ubuntu 8.10 that would be great.

---

### Post by John Jason Jordan on 2008-12-25
> **kristian_k said:**
> I tried 3 different sources already, 

ubuntu-8.10-desktop-amd64.iso
ubuntu-8.10-desktop-i386.iso
ubuntu-8.10-dvd-amd64.iso

the funny thing is that the iso from ubuntu.com for 64bit version doesn't even want to install. It says error reading boot sector after I press install and the only option is to reboot.
I already thought that a piece of hardware was malfunctioning so I tried ubuntu 8.04 and it works fine but thing is I don't want to use 8.04 because it can't connect to the wireless connection in my college.
Bottom line is .. Ubuntu 8.10 doesn't work ... 
are there any kernel or CPU drivers/updates I can try ... ?

If 8.04 will install then one option would be to go with 8.04 and afterward do a version upgrade to 8.10. That is, once 8.04 is installed, go to System > Administration > Update Manager and there will be a button to click at the top of the window to upgrade to 8.10. Just be sure not to do the upgrade unless you have a stable net connection. If the upgrade is interrupted it will create such a godawful mess that you'd be better off to wipe it out and start over with 8.04 from scratch.

And if there is a problem after the upgrade to 8.10 (like it won't boot or something) there will likely be error messages that can give a clue as to what is wrong.

---

