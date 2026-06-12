---
title: "AMD64 SMP and NVIDIA GTX 7800 system hangs"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by plg on 2006-01-09
I experience system hangs and lockups in SMP-mode, hard reset required.

The problem is not present when running in single CPU-mode. I'd be happy to know if anyone is running a similar config and how it is working. I can not really determine if it is a graphics driver issue or more general SMP issue.

Hardware:

* AMD64X2 (Dual Core) 4400+, 4 GB mem
* Asus A8N-SLI motherboard
* NVIDIA NForce4 SLI chipset
* NVIDIA GeForce 7800 GTX PCI-express

OS:

* Ubuntu 5.10: 2.6.12-10-amd64-k8[-smp]
* NVIDIA Graphics Driver Version 81.78 (dec 22, 2005) (also tried 81.74)

Running with the non-smp version seems to be working fine.
Booting (and reinstalling nvidia drivers) in SMP, the system hangs after a couple of minutes - moving mouse, clicking, or maybe nothing.

Problems have also been present in SMP-kernel without graphics. I got system messages like "Many lost ticks" and finally the machine hung.
The thread 'Re: ups....problems "many lost ticks"' may be reporting about the same problem, but with a different description. I therefore provide more details about the hardware config.

$ lspci
00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2)
00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f3)
00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f3)
00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0091 (rev a1)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

$ lspci -n
00:00.0 0580: 10de:005e (rev a3)
00:01.0 0601: 10de:0050 (rev a3)
00:01.1 0c05: 10de:0052 (rev a2)
00:02.0 0c03: 10de:005a (rev a2)
00:02.1 0c03: 10de:005b (rev a3)
00:04.0 0401: 10de:0059 (rev a2)
00:06.0 0101: 10de:0053 (rev f2)
00:07.0 0101: 10de:0054 (rev f3)
00:08.0 0101: 10de:0055 (rev f3)
00:09.0 0604: 10de:005c (rev a2)
00:0a.0 0680: 10de:0057 (rev a3)
00:0b.0 0604: 10de:005d (rev a3)
00:0c.0 0604: 10de:005d (rev a3)
00:0d.0 0604: 10de:005d (rev a3)
00:0e.0 0604: 10de:005d (rev a3)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 10de:0091 (rev a1)
05:0b.0 0c00: 104c:8023


cheers / Patric

---

### Post by Fregster on 2006-01-09
I can't even get ubuntu to install with my 7800 :(

---

### Post by J-B on 2006-01-09
I have an AMD X2 3800+, and a XFX 7800GT.   I haven't had any problems running the 64-bit edition of Ubuntu.    Although After reading this thread I looked in my device manager and every single thing is listed as "unknown", so for all I know it may not even recognize both cores.   But it seems to be running well so i can't complain.

---

### Post by plg on 2006-01-10
Although I'm not certain what you mean by "not installing". I'd guess the problem is with the Ubuntu NVIDIA drivers - you don't get X up and running without recent NVIDIA drivers from NVIDIA.

You should not install the Ubuntu NVIDIA support, it doesn't support the 7800 yet (from what I read 1 month ago). Also, I had problems running OpenGL apps (they all seg. faulted) if I installed the 32-bit libraries from the NVIDIA installer. So don't install that unless you know want to solve it - or know how to do it.

---

### Post by plg on 2006-01-10
Are you running a -smp kernel?

Unless you use an SMP kernel the OS will only use one CPU. How many CPU's do you see in "more /proc/cpuinfo"?

What 64-bit kernel are you running?
I'm running 2.6.12-10-amd64-k8, but the -smp version don't work.

---

### Post by Chris Cromer on 2006-01-10
I have the AMD 64 X2 4200+ and the BFG 7800GTX. Both worked out the box on a fresh install, no tweaking necessary.

I am using 2.6.12-10-amd64-k8-smp, and it works just fine for me. I use Ubuntu 5.10.

---

### Post by plg on 2006-01-11
If I'm not mistaken, the 7800 is not recognized, could it be you're running a generic VGA driver for X? What does glxinfo say?

Otherwise, which NVIDIA driver do you use?

There are some interesting posts in "Re: ups... lost ticks..." thread that might be connected to this problem. From that it sounds like the type of chipset/motherboard may play some part. 

/ Patric

---

### Post by al108 on 2006-01-24
I have similar problem with AMD 64x2 4400 and 7800GTX. Ubuntu drivers won't load with the smp kernel. (By that I mean that xorg.conf retains nv driver instead of nvidia and if you edit it X won't load). Tried to install nVidia drivers from their website but couldn't get to compile it. I'll try again today. As far as "unknown" in the device manager it doesn't stop it from working. I've installed Ubuntu on 5 or 6 different boxes mostly AMD64 and every one of them have everything "unknown". Still works just fine.
Alex

---

### Post by al108 on 2006-01-24
OK. It looks like those nVidia drivers from Ubuntu were never compiled for use with smp kernels. I installed drivers from nVidia web site and it works just fine even with twinview. I did follow this HOWTO "method 2" [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) 
I couldn't shutdown X using "sudo /etc/init.d/gdm stop (OR "kdm stop" if you use KDE)" from the howto, but rebooting with "recover" option worked. Also new nvidia  run package will make a backup of xorg.conf for you and install graphical interface for nvidia-settings if you want. I used readme from nvidia for more options and to enble twinview. Works great!
Alex

---

