---
title: "Installing [K]Ubuntu on a Dell SC-1435 server with Opteron processor"
date: 2007-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by techread on 2007-03-08
Hello to all: this is my very first posting in these forums, and I've heard some very positive comments about the helpfullness of all you people here...let's find out :) 

I've been a somewhat intermediate-level user (I'm a regular user, not a sysadmin) of Linux for about 8 years now, and having tried various Linux distros, I can tell you that my current favorite is Kubuntu.

Because of this, in our company we just bought a Dell SC1435 Server, for installing in it either Kubuntu or Ubuntu server.

However, as soon as the machine goes through its POST process and reads the CD-ROM, it shows in text mode:

.
Decompressing Linux
Booting the kernel.


But then it freezes there and my only option is to turn off the server again (you cannot switch to any other screen by using the usual Ctrl+Alt+F[n] key combination.

The main hardware components are:
-1 Dual Core AMD Opteron 2210 processor running at 1.8 GHz
-2 SATA Hard Disks, each of 160 GB and each running at 7200 rpm
-2 GB RAM (667 MHz)
-Video card: ATI ES1000 (16MB)
-1 dual interface Broadcom 5721J Gigabit ethernet adapter

Just for reference, CentOS 4.4 Server x86_64 installs without a problem, but then when you start X11 it shows a message that does not allow to start it: the server very briefly goes in to graphic mode and then returns to text mode, showing:

(WW) RADEON(0): Failed to set up write-combining rnge (0xe0000000, 0x1000000), 

even though when running the installation program X11 starts ok and all the installation was done on graphical mode. Because of this I suspect that my problem may have to do with the video adapter.

Can anyone please help? Thanks in advance.

---

### Post by insom on 2007-03-21
Long time reader; first time poster.

We've just received shipment of a DELL SC-1435, and it hangs on boot, both with 32bit 6.10 (Edgy) and 64bit 6.10 (Edgy). This appears to be an ACPI issue, and Cal Leeming found that booting with:

noacpi acpi=off pci=noacpi

Lets us finish the installation. I hope this helps someone.

---

### Post by ivanperzan on 2007-08-13
Hi

new at this thing... how does this noacpi acpi=off pci=noacpi thing works exactly. Where do I enter this?

Ivan

---

### Post by Kilz on 2007-08-13
While Kubuntu may be your favorite, are you sure you want to install kde on a server? IMHO it is the most resource consuming vs gnome (Ubuntu, second most) or xfce ( Xubuntu, Not bad for servers). You might even consider [icewm and rox]("https://help.ubuntu.com/community/IceWM?highlight=%28icewm%29") for the limited amount of time you will need a desktop on a server.

---

### Post by insom on 2007-08-13
Those go in the boot params when grub loads, press "c" on the loading screen.

---

