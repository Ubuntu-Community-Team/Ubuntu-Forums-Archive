---
title: "NVIDIA driver problems"
date: 2005-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Compwiz on 2005-03-12
since this question has something to do with both hardware (videocard) and AMD64 problems (drivers), i decided to post it in the AMD section ... please understand my reasoning ... Now onto the problem at hand: I recently got my nvidia geforce 6600GT AGP card  working with the "vesa" drivers. However, i would now like to download the driver (that i got from the website and is now on my USB flash drive) from my flash drive and make my graphics experience complete. The problem is, I dont know how to access the file when not in X ... please guide me in the right direction as to where i should save the " NVIDIA-Linux-x86_64-1.0-7167-pkg2.run" file so it is accessable when i type ```
sh  NVIDIA-Linux-x86_64-1.0-7167-pkg2.run
``` ... all help ia appreciated!

---

### Post by kubla on 2005-03-12
[QUOTE=Compwiz]since this question has something to do with both hardware (videocard) and AMD64 problems (drivers), i decided to post it in the AMD section ... please understand my reasoning ... Now onto the problem at hand: I recently got my nvidia geforce 6600GT AGP card  working with the "vesa" drivers. However, i would now like to download the driver (that i got from the website and is now on my USB flash drive) from my flash drive and make my graphics experience complete. The problem is, I dont know how to access the file when not in X ... please guide me in the right direction as to where i should save the " NVIDIA-Linux-x86_64-1.0-7167-pkg2.run" file so it is accessable when i type ```
sh  NVIDIA-Linux-x86_64-1.0-7167-pkg2.run
``` ... all help ia appreciated![/QUOTE]
 
Your usb drive should still be mountable and hotplug will even probably automagically mount it for you. It'll like be a device like sda1 and mounted in /media. For example, my usb key drive turns up like this (result of df):

/dev/sda1               128228     20280    107948  16% /media/usbdisk

At this point, from your shell you'll need to do the following:

cd /media/usbdisk

chmod +x NVIDIA-Linux-x86_64-1.0-7167-pkg2.run

and then type your command

Good luck!

Ian

---

### Post by Compwiz on 2005-03-16
Absolutely worked 100% fine! i just havent gotten a chance to post ... thanks!!! i now have 3D grafix!!! booya!! its soo awsome!!! (all i need now is a connection to the internet :roll: )

---

### Post by Joshua on 2005-03-17
Along the lines of Nvidia drivers - why wouldn't you aptitude install nvidia-glx?  Is there a difference between nvidia-glx and the drivers from the website?  Should I be using the drivers from the website instead of nvidia-glx for my GeForce MX 400?

---

### Post by tpoindex on 2005-03-17
I had some problem with the nvidia-glx drivers running Enemy Territory on my 6800 card, lots of bad texture maps, etc.  I upgraded to the recently released 7167 driver from Nvidia.  I had a little trouble getting the right debain package for the kernel headers/source before it would compile (my fault, I'm a long-time Linux user but newbie /w Debian).  The 7167 driver fixed all of the texture map issues.

Getting the 32bit OpenGL libs installed correctly was also somewhat problematic, but I finally satisfied the Nvidia installer with some soft links for /emul/ia-32/usr/lib -> /usr/lib32. I installed the newer drivers on top of the nvidia-glz, I probably should have removed the nvidia-glx package first.

---

### Post by rykel on 2005-06-25
[QUOTE=Joshua]Along the lines of Nvidia drivers - why wouldn't you aptitude install nvidia-glx?  Is there a difference between nvidia-glx and the drivers from the website?  Should I be using the drivers from the website instead of nvidia-glx for my GeForce MX 400?[/QUOTE]

Guys,

I know that I am late to this thread, but anyway, the reason why I use the official NVIDIA driver for my GeForce FX 5700LE, is that it has *Direct Rendering*.

btw, installing the official driver on top of nvidia-glx will cause "glxgears" to crash (segmentation fault).

To get great 3D, simply use Synaptic to *_COMPLETELY REMOVE_* (including configuration files) the nvidia-glx and then install the official driver as per instruction below:

[B]Ctrl-Alt-F1
sudo killall gdm
cd (to the folder where you downloaded the nvidia*.run file)
sudo ./NVIDIA*run
sudo gdm start[/B]

I wish that there is an [**official NVIDIA driver autopackage**](http://www.autopackage.org) so that we can all install it easily but that might still be some time away in the future.

Hope that helps!


Rykel
MSN/Skype/eBay/Yahoo: **rykel98**

---

