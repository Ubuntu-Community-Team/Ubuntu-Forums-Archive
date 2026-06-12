---
title: "Nvidia PCI-e video cards (6600, 6800) screen corruptions !"
date: 2005-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tichondrius on 2005-02-13
This thread discusses a [horrible bug](https://bugs.freedesktop.org/show_bug.cgi?id=2322) causing weird screen corruptions in X-windows, which affects people using PCI-express video cards on all 64-bit Linux distributions ! Note that most people encountered this when using Nvidia 6600 series pci-e cards, but it should also happen for 6800 pci-e series. It does not affect AGP cards, nor does it affect 32-bit distributions.

This bug has been encountered by many other people and solutions to it exist (a discussion can be found [here](http://www.nvnews.net/vbulletin/showthread.php?t=42597&page=1&pp=15) ), which I will explain below, but first I'll describe the problem in more detail. The problem occurs only on AMD64 linux distributions, as it is a caused by a bug in X-windows 64-bit versions (both XFree86 and Xorg). This bug causes graphics memory corruptions only for pci-express video cards running using the nvidia 64-bit drivers. So the main victims of this bug are the 6600/GT cards, but again - only when running in 64-bit. Also note that the public domain "nv" driver doesn't support the 6600 series cards yet, and the "vesa" driver also doesn't work with these card in 64-bit mode (probably for the same reason), so people who are running a 64-bit distribution can't use X-windows with their pci-e cards !!!

The symptoms of the bug are
(a) A mouse pointer which looks like a large square, or a disappearing mouse pointer.
(b) Text fonts which randomly disappear and/or being displayed garbled in X-terminals and other applications which display text fonts (almost any application).
(c) Text mode terminal (e.g. when pressing ctrl-alt-f1) is completely messed up and illegible.
(d) When X loads, the nvidia logo doesn't display, and instead you see some corrupt image.

As I said, it was diagnosed as a bug in the 64-bit part of the X-windows (xfree86 and xorg) code. A fix does exist and is pretty small, but requires you to recompile X-windows from scratch ([here](http://www.shell.linux.se/xpatrikx/articles/xf86pcibus-bug.html) ). If you don't want to do that, then there is a workaround, which involves adding the following two lines in the "Device" section of the xorg.conf/XFree86-4 configuration file (the section where the "nvidia" driver line is present):

Option "SWCursor"
Option "NoRenderExtension"

This solves most of the problems, except for the consoles being garbled after you exit from X-windows, but that is really a small problem. Also this workaround doesn't cause performance degradation in games or 3d-apps.

**Request to Ubuntu developers: **It would be nice if you could incorporate this fix into the hoary-amd86 xorg binary package. For example, Gentoo has already done so in their xorg package. I encountered some problems when trying to compile xorg (not related to this change), so I'm still using the workaround above.

---

### Post by Tichondrius on 2005-02-13
Given the above bug, here's what you need to do to get a 6600 & 6800 series pci-express to work with the nvidia drivers after installing hoary-amd64. Note that the nvidia 64-bit drivers are not available in Ubuntu's warty repository, so if you're using warty-amd64, you'll have to use the vesa driver (until someone backports the nvidia 64-bit driver packages to warty).

1) Install hoary-amd64 as usuall, which will detect your nvidia cards and choose the "nv" driver by default. At the end of installation it will try to start X-windows and fail, most likely crashing the machine in the process (note that the "nv" driver might work for 6800 series cards, but we still want to install the "nvidia" drivers which much better performance, especially in 3D apps and games).
2) Reboot using "recovery mode" option in the grub menu, which doesn't start X-windows.
3) Edit /etc/apt/sources.list to uncomment all the repositories (lines starting with "deb").
4) Type the following (don't worry if you get warnings about some repositories not being available):

# apt-get update
# apt-get install nvidia-glx
# nvidia-glx-config enable

5) Edit /etc/X11/xorg.conf and find the "Device" section. Make sure the driver line in it says "nvidia", and then also add the following lines in the end of this section:

  Option "SWCursor"
  Option "NoRenderExtension"

6) reboot w default kernel mode (not recovery mode).

---

### Post by mips on 2005-03-05
I did all the above with no luck. My X starts up with the normal "nv" driver but will not start after the above procedure. Running Hoary AMD64-K8

---

### Post by daniels on 2005-03-06
It's already been fixed.

---

### Post by gugin on 2005-03-09
I can't get it to load x86 serve at all. it just fails. nv6600 gt pcie.

---

### Post by pavedissian on 2005-03-10
I'm not so sure this is only an AMD64 thing.  I am running an XP/Ubuntu dual boot on  a Dell 8600 and I seem to be having the same symptoms as was described.  It only happens when the computer is running on battery for a length of time.  I have been looking around for some help as to what it could be but i am either not entering the correct search criteria, or nobody has the same problem I have.  If anyone has any idea on how to fix this, please let me know.

Paul

---

### Post by jmcknight on 2005-03-19
Does this bug only effect these 2 particular cards?  I'm going to be upgrading my motherboard to a PCI-E based board (ASUS A8V-E Deluxe) and an ASUS Geforce 6200 PCI-E card.  Would this bug effect me?

---

### Post by coolmike890 on 2005-05-22
[QUOTE=pavedissian]I'm not so sure this is only an AMD64 thing.  I am running an XP/Ubuntu dual boot on  a Dell 8600 and I seem to be having the same symptoms as was described.  It only happens when the computer is running on battery for a length of time.  I have been looking around for some help as to what it could be but i am either not entering the correct search criteria, or nobody has the same problem I have.  If anyone has any idea on how to fix this, please let me know.

Paul[/QUOTE]
 Yours is a hardware problem. I am 5-9's sure. It's not a related issue.

---

### Post by Jet2k5 on 2005-07-06
:(  Lol I'm building a 64-bit machine with pci-e and this is sad news.  I have to deal with yet another problem on my computer.  I have soo many problems coming up that I don't how all this stuff is going to work.  Thank god it's not just ubuntu but linux in general.

---

### Post by cassidy on 2005-07-11
I envisage to buy a GeForce 6600GT pci-x with AMD64.
Is this bug still present on breezy?

---

### Post by Jet2k5 on 2005-07-11
[QUOTE=daniels]It's already been fixed.[/QUOTE]

Looks like the developer said it was fixed.  So either it's fixed right now for Hoary, or it's fixed in Breezy.  I hope both lol  :-P

---

