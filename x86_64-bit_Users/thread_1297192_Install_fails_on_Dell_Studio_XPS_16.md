---
title: "Install fails on Dell Studio XPS 16"
date: 2009-10-21
forum: x86 64-bit Users
---

### Post by Max Neptune on 2009-10-21
I have a new (2 months old) Dell Studio XPS 16, with Windows Vista Premium. I am having many problems installing ubuntu x86 64-bit on this system.

I have ubuntu on two other computers and have used it on many others. I have never had these issues before. 

I first downloaded the ISO from the links on ubuntu.com. I then burned this to a dvd on the Dell and tried an install but the Dell would not even boot from the DVD. Yes I know how to change the boot options in the bios but this did nothing for me. I then tried burning another DVD on my desktop and again this failed to boot on the Dell. I even tried downloading ubuntu 9.04 again and burning it to a DVD this did not work. 

I then tried using an ubuntu 8.10 DVD that I purchased on Amazon and has worked on other systems. This did boot, sort of. It would run through the ubuntu loading screen then go to a black and white text only screen and go no further. This screen stated that ubuntu comes with no warranty and some other useless information but this was it. 

Next I tried using unetbootin to create a bootable USB drive. This also worked a little longer. I was able to go into a live session. I then chose install and made it all the way through partitioning and continued to install. Eventually the install fails and tells me to check that the CD/DVD is clean or not scratched, which of course I am not using with a bootable USB stick. 

I tried switching the SATA mode from AHCI to ATA in bios but this also led to a failure.

I have tried all of these options many times and nothing seems to get anywhere. 

Does anyone know what is wrong?

Has anyone else had a similar experience?

Is there a setting in bios that could be causing a problem?

Thank you,
Max Neptune

---

### Post by staticextasy on 2009-10-21
I had a similar problem with trying to actually install Ubuntu on a seperate partition trying to dual boot with Vista 64.

I was trying to use an 8.04 disc that i had got with an Ubuntu book. it didn't really work out to well with me so i downloaded 9.04 and the livecd installer didn't want to work to well so i installed through windows and it worked fine, after that i said to hell with windows

I installed 9.04 using my entire HD scrapping windows in the process ( backed up my windows stuff though :P )

Installed fine that way, i'm on an XPS M1530. 

If you're trying to dual boot i would say you're having the same problem i had.

Try installing through windows using WUBI, if you want to save your windows partition.

---

### Post by Max Neptune on 2009-10-23
Using WUBI works but does not allow me choose the size of the Swap file or the size of any of the partitions for that matter. It also does not allow the creation of a Home partition or anything of the sort. Also I am limited to a maximum size of 30Gb for the entire install. 

Does anyone know how to properly make ubuntu 9.04 on this computer and dual boot with Vista?

Unfortunately I cannot abandon windows, as I must use programs such as Autodesk Inventor and Solidworks for my work. But I also need to use Linux for programs such as XFOIL and OpenFOAM.

Thank you,
Max Neptune

---

