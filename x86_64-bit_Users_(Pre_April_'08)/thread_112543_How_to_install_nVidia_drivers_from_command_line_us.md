---
title: "How to install nVidia drivers from command line using cdrom."
date: 2006-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by skillzdatkillzholmes on 2006-01-04
Hi!

I've got a weird problem, I also sent this to the Debian Bug Reporter email server:

Package: Debian-31r0a-amd64-binary
Version: 2.6.11.6

My problem is that when I boot Debian 64 from GRUB, after it's done loading everything, an error message saying "I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I select yes and the following comes up:

XFree86 Version 4.3.0.1 (Debian 4.3.0.dfsg.1-14sarge1 20050915192417
[email]root@bester.farm.ftbfs.de[/email])
Release Date: 15 August 2003
X Protocol Version II, Revision 0, Release 6.6
Build Operating System: Linux 2.6.11.6-vs195-farm1.0 x86_64 [ELF]
Build Date: 15 September 2005

My system contains the following hardware:
Motherboard: Asus A8N-E nForce 4 Ultra
CPU: AMD Athlon 64 3000+ 1998MHz
RAM: OCZ Premium-Series 1gb (2x512mb) 2 DIMMS Dual Channel PC3200 DDR400
Video: Asus Extreme N6600 Silencer (nVidia GeForce 6600 256mb)
HDD: Maxtor 250gb IDE HDD (6Y250P0)
Optical: Pioneer DVR-110D DVD-RW
Monitor: NEC MultiSync 75

What led to this was a Debian "Sarge" AMD64 installation from DVD. I had mostly defaults, with an nForce 2 Ethernet Driver instead of an nForce 4 since I didn't have a floppy and it was the only nForce driver there. (It worked though, it downloaded everything it needed and setup the Network Config successfully) I chose all of the packages available (except for the manually select packages) and when it came to it, I select non-LCD mode, with an "nv" display driver and 1280x1024x60hz resolution/refresh rate. Finally the installation finished and the above problem came to be, it also turns out that my video card is known to have problems with Debian's X Server, so they made a driver that contains a work-around. It is called NVIDIA-Linux-x86_64-1.0-8178-pkg2.run now I only have one problem, installing it. I have no idea how Linux command works, I've only worked with DOS Command *slaps self* so if someone could help me out that would be great, thanks once again in advance.

         Skillz

P.S. I know I'm asking about Debian but the users on the Debainforums havn't replied to this at all and I posted it a while ago, I've been here before and I know that users here are a great help and answer questions quickly.

---

