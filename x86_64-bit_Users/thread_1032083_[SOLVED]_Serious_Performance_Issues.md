---
title: "[SOLVED] Serious Performance Issues"
date: 2009-01-06
forum: x86 64-bit Users
---

### Post by dragonwolf on 2009-01-06
Hey Guys,

Here is my issue-

Just built this box last month to run vista( I know I know spare the slamms and rederict please) then I got the idea to once again try linux and actually learn this time and do it. Well that much I am doing enogh said on that suffice to say so far I am loving Xubuntu 8.10 64 bit with the exception of one very large problem performance under load absolutly sucks.

give ya a run down on my hardware-

XFX nvidia 750a SLI Mobo
AMD Phenom 8650 triple core
4 GB PC6400 800Mhz Ram
80 GB SATA HD (this is the one I actually run the OS on for now)
750 GB Sata HD (Windows HD, also mounted it for use as slave in xubuntu)
nvidia 9800 GT video card ( downloaded installed proprietary drivers form package manager)


here's my issue- in Vista I can put the same load that I do here on ubuntu on this box and it won't even break a sweat however when I try this on xubuntu it comes to a crawl I know I have either comletly overlooked some tweaks or just didn't know about them so any help would be greatly appriciated.

oh also jsut a little more back ground

Vista is 32bit ultimate edition

the load I speak of is playing a movie while copying a few gig of data from one drive to another and surfing the net at the same time

according to the system monitor even when my CPU is at 100% load it's still only using a mak of 724 mb of an avail 3.9gb of ram also the paging swap doesn't seem to adjust as needed like it did in windows is this right? its set at 3.1 gb

The one thing I have noticed though is a but load of processes like 161 as of this moment none of them seem to be using much memory but is this normal this is over twice the active processes in my windows installation at any given time.

---

### Post by cariboo on 2009-01-06
You can't compare Linux to Windows as the operating systems work totally diferently. The System Monitor app adds quite a bit of overhead, so you are not getting a true reading of cpu usage. THere are two tools that will help diagnose what is using all your cpu cycles. THe first is **Top** which is installed by default, to run it open a Applications-->Accessories-->Terminal and type:

```
top
```

The second is **htop**, it is in the repositories. The easiest way to to explain how to install it is the command line way. In a terminal type:

```
sudo apt-get install htop
```

Htop gives you a visual representation of cpu usage, as well as a list of applications that are using the largest amount of resources. Once installed you can start htop from Applications-->System tools.

Linux does not have a pagefile system like windows, the swap partition your created will only get used if you have so much running that you run out of ram.

To get a true representation of how your ram and swap space are being used, in a terminal type:

```
free -m
```

These utilities should help you get a handle on which applications are using up your cpu cycles.

Jim

---

### Post by dragonwolf on 2009-01-12
> **cariboo907 said:**
> You can't compare Linux to Windows as the operating systems work totally diferently. The System Monitor app adds quite a bit of overhead, so you are not getting a true reading of cpu usage. THere are two tools that will help diagnose what is using all your cpu cycles. THe first is **Top** which is installed by default, to run it open a Applications-->Accessories-->Terminal and type:

```
top
```

The second is **htop**, it is in the repositories. The easiest way to to explain how to install it is the command line way. In a terminal type:

```
sudo apt-get install htop
```

Htop gives you a visual representation of cpu usage, as well as a list of applications that are using the largest amount of resources. Once installed you can start htop from Applications-->System tools.

Linux does not have a pagefile system like windows, the swap partition your created will only get used if you have so much running that you run out of ram.

To get a true representation of how your ram and swap space are being used, in a terminal type:

```
free -m
```

These utilities should help you get a handle on which applications are using up your cpu cycles.

Jim

TYTY but it seems all was due to a corrupt install I reformatted and all is working fine now with no issues(well other than waiting on codeweavers to update crossfire to run the new Adobe CS, lol)

---

