---
title: "Custom Kernel and new applications"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pouleterie on 2007-06-12
First post on a support forum, but I can't say I didn't try googling for the topic.

Alright, so I have a two weeks old experience on Ubuntu, I've managed to install the 2.6.21 kernel, and applied ck2's performance patch. Did the symlinks to use restricted modules, everything's running smoothly. The only problem is, once I try to install some applications, using .deb packages, it notices it, and doesn't install anything. For instance, I'm trying to install wine, and I get this, if I look at what it does as it installs the .deb:

The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9853kB of archives.
After unpacking, 45.8MB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 
dpkg: serious warning: files list file for package `linux-restricted-modules-2.6.21-ck2-poulet' missing, assuming package has no files currently installed.
128101 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.37~winehq0~ubuntu~7.04-1_amd64.deb) ...
Setting up wine (0.9.37~winehq0~ubuntu~7.04-1) ...

Problem is, after that, wine is "installed", but there's no .wine folder, at all. I tried to install kiba-dock from a .deb, also, and I got the same kind of problems. Does it install anything, past that error, or what? Everything I used so far, or almost, was compiled from source, due to that.

Thanks for your help. I hope this was at the right place.
(Using amd64 deb package for wine, and amd64 kernel.)

---

### Post by Crypto-138 on 2007-06-12
Please forgive me if you've already tried this, or if I'm explaining anything you already know...

I'm not sure if this is your problem, but the .wine directory is only created after you run WINE at least once...
Open up a terminal-
[INDENT]Press Alt + F2
if you use Ubuntu, enter 'Gnome Terminal'
If you use Kubuntu, enter 'Konsole'.[/INDENT]

Type "winecfg" in the terminal. It should say something about configuration, and then you will have your .wine folders.
.deb packages usually install to /usr/bin/, rather than your home directory.

If this fixes it, then I don't believe this has to do with your Kernel and Packages being for AMD64, though.

Also, this looks a bit weird:
> dpkg: serious warning: files list file for package `linux-restricted-modules-2.6.21-ck2-poulet' missing, assuming package has no files currently installed.
I'm not sure if that package is necesary for your architecture (x86_84), but the fact that its file list is missing isn't very comforting either....

---

### Post by Pouleterie on 2007-06-12
poulet@pouleterie:~$ winecfg
wine: creating configuration directory '/home/poulet/.wine'...
Segmentation fault
wine: wineprefixcreate failed while creating '/home/poulet/.wine'.
wineserver: could not save registry branch to /home/poulet/.wine-RBY3ca/system.reg : No such file or directory
wineserver: could not save registry branch to /home/poulet/.wine-RBY3ca/user.reg : No such file or directory

And if I help him up, creating .wine for him, evidently, more errors:

poulet@pouleterie:~$ mkdir .wine
poulet@pouleterie:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/poulet', starting in the Windows directory.
Segmentation fault

So, I don't know. When I installed:

poulet@pouleterie:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9853kB of archives.
After unpacking, 45.8MB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 
dpkg: serious warning: files list file for package `linux-restricted-modules-2.6.21-ck2-poulet' missing, assuming package has no files currently installed.
128775 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.37~winehq0~ubuntu~7.04-1_amd64.deb) ...
Setting up wine (0.9.37~winehq0~ubuntu~7.04-1) ...

---

### Post by Pouleterie on 2007-06-14
I can't get anything to work, mostly. In the case of wine, yet again, I tried compiling from source, and that error still pops up, along with some others. Wouldn't it just be more simple for me to install a standard 32 bits Ubuntu and not touch the kernel? I really wanted to tweak to maximize performance, and make it as smooth as possible. What would you recommend me?

---

### Post by Cappy on 2007-06-16
I would use the kernel that Ubuntu has by-default. I've never compiled my own kernel so I don't know how to fix this stuff =(

---

