---
title: "X-Server Error on AMD 64 X2"
date: 2006-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Minkl825 on 2006-04-10
I get the following error when I try to run the live or install of Ubuntu 5.10.  I tried using the PC and 64 version.  All versions came from the Ubuntu distributor.  So basically, four strikes and I'm out.  Anyway, here is the error:

"Failed to start the X server (your graphical interface)"

My system:

DFI LANPARTY UT nF4 SLI-DR Socket 939 NVIDIA nForce4 SLI Motherboard
AMD64X2 3800+
CORSAIR XMS 2GB (2 x 1GB) 184-Pin DDR SDRAM Unbuffered DDR 400 
     (PC 3200) Dual Channel Kit System Memory
Dual XFX PV-T73G-UDD3 GeForce 7600 GT XXX (590MHz) 256MB 128-bit 
     GDDR3 PCI Express x16 Video Card in SLI mode
S-ATA Maxtor 200GB HDD
BenQ Black E-IDE/ATAPI 16X DVD±R DVD Burner Model DW1625 BLK

I am able to run two other version of Linux without any problems.

Thanks in advance for the help.

MM

---

### Post by taipan on 2006-04-10
I had the same problem on my laptop, using an ATI card and all :-(, just had to suffice with the generic vid drivers

type
[B]
sudo dpkg-reconfigure xserver-xorg[/B]

when you get to the driver brand selection screen choose 

**vesa**

It may not be the fastest or best looking setup, although it worked for me.
At least it allows you into gnome to attempt installing latest drivers

Hope this helps

---

### Post by Minkl825 on 2006-04-10
Do I type that prior to the install?  As opposed to just hitting 'enter' for the default installation.  

Thanks for the response.

MM

---

### Post by taipan on 2006-04-10
My problem occurred after I had installed ubuntu. It just didn't load the gnome desktop, although I still had the graphical line. That is where I entered the above stated lines; to reconfigure xorg.

If your problem is in the installation process, I am unable to help.

---

### Post by Minkl825 on 2006-04-12
It worked.  Thanks for the help.

---

### Post by Jason_25 on 2006-04-12
You can install the closed source nvidia drivers if you want 3d performance.  I assume you would with such a new card.

---

