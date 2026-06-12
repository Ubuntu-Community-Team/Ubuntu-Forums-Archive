---
title: "X gnome login crash"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by yilez on 2005-11-29
Hi, I searched for the solution for this, but couldn't find the correct thread, so I apologise if this has been answered already.

Basically, I installed Ubuntu fine and rebooted my system. After boot, I get the Gnome login screen. Anything I do here, crashes the system.

i.e. I put in my details, and it starts to initialise the window manager, and it locks up the computer, including the keyboard, meaning I cannot switch session to the console.


Also, if I click session-type, this too locks my system up in the same way.

My system looks like this:

Asus A8N-E
Athlon 64 x2 4400
2 GB RAM
NVidia 7800GT (BFG, if that makes any difference)
Western Digital 200 GB SATA drive with Windows XP in the first primary partition.
Netgear WG111 (USB wireless adapter)

Thanks.

---

### Post by bonzodog on 2005-11-29
do you have the nvidia accelerated drivers installed?
There is a known bug with the basic X drivers and the very latest cards. The very latest version of the nvidia drivers off nvidias site (you will need to compile and build them yourself), fixes the problem. DO NOT get the nvidia-glx apt-get package as it is 7667 - you need 7676. To install the drivers you will also have to install the kernel headers and development files by doing:

```
sudo apt-get install build-essential

sudo apt-get install linux-headers <your kernel version>

```

---

### Post by yilez on 2005-11-29
[QUOTE=bonzodog]do you have the nvidia accelerated drivers installed?
There is a known bug with the basic X drivers and the very latest cards. The very latest version of the nvidia drivers off nvidias site (you will need to compile and build them yourself), fixes the problem. DO NOT get the nvidia-glx apt-get package as it is 7667 - you need 7676. To install the drivers you will also have to install the kernel headers and development files by doing:

```
sudo apt-get install build-essential

sudo apt-get install linux-headers <your kernel version>

```[/QUOTE]

That makes sense. I've always found the standard nvidia drivers shipped with all distros to be rubbish, and I'll only have the standard nvidia drivers installed at the mo.

One more thing, to prevent me from booting from Linux, to Windows and back more than necessary: does Ubuntu ship with ndis support? My wireless adapter is 802.11g. If it doesn't I'll download that as I get the nvidia driver.

---

### Post by bonzodog on 2005-11-29
you will need ndiswrapper to use the modem with the windows drivers.

---

### Post by yilez on 2005-11-29
[QUOTE=bonzodog]you will need ndiswrapper to use the modem with the windows drivers.[/QUOTE]
Yes. I will. Does Ubuntu ship with it, is what I'm asking.

I'm finding not very many distros do, there only really seems to be Mandriva that does.

---

