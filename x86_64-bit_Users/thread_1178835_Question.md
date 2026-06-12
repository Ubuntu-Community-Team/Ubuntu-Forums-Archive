---
title: "Question"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by zenbachry on 2009-06-04
Is there any Virtual Machine software out there that I can play my Windows games on (with installing Windows, of course)?

Reason I ask, is I've got majority of my games to run under WINE or with Cedega, but there are 3 games that I can't get to run. Cabal, 12 Sky 2, and Project Torque. Those are the only reason why I have a hard drive dedicated to Windows. Its actually a pain in the rear to restart to go play those games, and come back to Ubuntu to do everything else. I know, I could just leave Ubuntu and stick to Windows, but I don't trust Windows at all really. I've looked around, I hear of Xen, VirtualBox, and Parallels. Xen did something funky to my computer and I couldn't figure out how to undo it. Parallels doesn't have a 64-bit version, and VirtualBox doesn't have the support for the games.

Catch what I'm askin'?

---

### Post by ZeldeR on 2009-06-05
hey I think you need Vmware Server or Workstation or Virtualbox...but I'm not sure if you can choose a graphic-card in the Virualbox.

Vmware Server and Workstation use a 16 MB graphic card and you have no chance to play something there :(

---

### Post by zenbachry on 2009-06-05
When I try to play my games under VirtualBox, the guest OS locks up. You're right, 16 MB video memory ain't nothin' now.

Thanks for your suggestion.

---

### Post by markharding557 on 2009-06-05
unfortunatly the virtualizers just arn't very good at running 3d yet.
the support is patchy and performance way below running the same 3d app directly

---

### Post by zenbachry on 2009-06-05
Well, I read that Xen and Parallels uses full hardware, and not just virtulize...but, again, thanks for your responses.

---

### Post by ddales on 2009-06-07
> **zenbachry said:**
> When I try to play my games under VirtualBox, the guest OS locks up. You're right, 16 MB video memory ain't nothin' now.

Thanks for your suggestion.

Not exactly accurate.  VirtualBox will allow you to use 128MB for video memory with 3D acceleration.  However, it's added to the base memory and increases the requirements for the Host.  It also doesn't work very well.

---

### Post by cariboo on 2009-06-07
You can purchase Paralells from the [Ubuntu Store.]("http://shop.canonical.com/index.php?cPath=19&osCsid=fbb0b49259f0c174ba71d7030111220e")

---

### Post by zenbachry on 2009-06-07
Ok, would that work with 9.04? How 'bout 64-bit? I tried to download their trial off their website, but they didn't have a 64-bit version, and the 32-bit wouldn't install (obviously).

---

### Post by zenbachry on 2009-06-07
> **ddales said:**
> Not exactly accurate.  VirtualBox will allow you to use 128MB for video memory with 3D acceleration.  However, it's added to the base memory and increases the requirements for the Host.  It also doesn't work very well.I have VirtualBox with it set to 128 MB of video memory as well with 3D accelleration. But the games don't do anything. Even Cabal, which requires a 3D accellerator as a minimum locks up the guest OS.

---

### Post by matheusber on 2009-06-08
> **zenbachry said:**
> Is there any Virtual Machine software out there that I can play my Windows games on (with installing Windows, of course)?

Reason I ask, is I've got majority of my games to run under WINE or with Cedega, but there are 3 games that I can't get to run. Cabal, 12 Sky 2, and Project Torque. Those are the only reason why I have a hard drive dedicated to Windows. Its actually a pain in the rear to restart to go play those games, and come back to Ubuntu to do everything else. I know, I could just leave Ubuntu and stick to Windows, but I don't trust Windows at all really. I've looked around, I hear of Xen, VirtualBox, and Parallels. Xen did something funky to my computer and I couldn't figure out how to undo it. Parallels doesn't have a 64-bit version, and VirtualBox doesn't have the support for the games.

Catch what I'm askin'?

I'm trying to do the very same thing in here, and although it is not super stable it works. [http://www.nabble.com/Successful-PCIe-Graphics-VT-d-Passthrough-to-Win32-DomU,-Q35-chipset-td21671745.html](http://www.nabble.com/Successful-PCIe-Graphics-VT-d-Passthrough-to-Win32-DomU,-Q35-chipset-td21671745.html)

the issue is that I can't even boot the 3.4 xen on ubuntu (I failed to find a guide to say what to do). I got the packages from: [https://launchpad.net/~mikmak/+archive/ppa](https://launchpad.net/~mikmak/+archive/ppa)

my menu.lst is:

title		Ubuntu 9.04, kernel 2.6.28-11-generic-xen
uuid		39c98bd5-757b-4b85-aaf7-5e106ff0c5dd
kernel		/boot/xen-3.4.gz noreboot
module		/boot/vmlinuz-2.6.28-11-generic root=UUID=39c98bd5-757b-4b85-aaf7-5e106ff0c5dd ro quiet splash pciback.hide=(01:00.0) 
module		/boot/initrd.img-2.6.28-11-generic


and I have no idea whatsoever of how to config xen kernel and grub stuff. just got some examples from internet and tried :(

I got a dead box using this above.

If anyone has any hints or places where I can read, I'd be really grateful.

I'm using jaunty on E8400 box and Q35 (VT-d capable hardware) on amd64 kernel.

thanks,

matheus

---

### Post by dagrump on 2009-06-08
If I read your post right you are trying to run Vista Ultimate 64bit & play games requiring 3d. Well the OS needs a couple of GB just for itself & then whatever you can throw at it for video ram. 
You are better off just dual booting, & use the proper tool for the job. Windows for Windows games & ( can't replace) Windows only software & Linux for everything else.
I boot Windows for games, Crysis ain't playing on Linux. 
Doom3, & Quake4 have native installation files. Prey runs under wine & is supposed to get a linux install file.
Let virtualbox, etc, have time to mature.

---

### Post by matheusber on 2009-06-09
> **dagrump said:**
> If I read your post right you are trying to run Vista Ultimate 64bit & play games requiring 3d. Well the OS needs a couple of GB just for itself & then whatever you can throw at it for video ram. 
You are better off just dual booting, & use the proper tool for the job. Windows for Windows games & ( can't replace) Windows only software & Linux for everything else.
I boot Windows for games, Crysis ain't playing on Linux. 
Doom3, & Quake4 have native installation files. Prey runs under wine & is supposed to get a linux install file.
Let virtualbox, etc, have time to mature.

I know what you mean, but I really want to make this and don't have to reboot. Iven if I can't succeed, I'll try :)

matheus

---

### Post by Ramza500 on 2009-06-09
I wanted to run something as simple as QuakeLive.  I installed both VirtualBox and VMWare.  VirtualBox has better OpenGL support (which one would think is what they want for Quake) while VMWare has better support for DirectX.  My machine is an E5450, 10GB RAM, and a GeForce 9600 GSO.

Just to let you know how something simple like QuakeLive worked out in a VM environment--

VirtualBox 2.2.4:
Installed XP-SP3, updated; allocated 128MB vid w/ 3D acceleration, 2GB RAM
Tried QuakeLive w/ Firefox on lowest settings - nothing
Installed Wine3D (runs DX commands through OpenGL)
Tried QL, FFox, lowest settings, one opponent - Very laggy 56k sort of feel, stuttering, etc.

VMWorkstation 6.5:
Same setup as above, no Wine3D
Got farther than VBox initial run but did not run as well as VBox final run.

I have Crossover Pro 7.1 and Crossover Games 7.1.2 that I might try soon, preferably in a VM environment first...I will see how those work.

---

