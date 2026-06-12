---
title: "Problem after installing.."
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bowdwin on 2005-12-17
I am installing the amd 64 ubuntu version.  I have a AMD 64 bit +3200 proc.  I also have a BFG geforce 7800 GT 256 graphics card.  I picked the max resolotion when it prompts me to (1600 x 1200).  After the install it reboots and then I enter my User name and password.  After I hit enter I see nothing but a brown background and a center with a bunch of colors mushes together in a rectangle.  I have tried to install it twice and I get the same problem.  I can move the mouse around but thats it.  There is nothing on the screen but that.  Is there an easy fix for this? Or is this a graphics card driver issue? 
Thanks
Keith

---

### Post by FluffyElmo on 2005-12-17
It sounds like a driver issue. Try hitting Ctrl-Alt-F2 to get to a command prompt and follow the instructions here to install a current driver for your card. 

[http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")

You may also want to specify a lower resolution for the card to make sure everything works then increase it after drivers are installed.

---

### Post by Bowdwin on 2005-12-17
I tried a lower resolution and that did not work.  How do I open synaptic / kynaptic ? to follow the link..

---

### Post by Bowdwin on 2005-12-17
I went to bfg tech and downloaded the nvdia-linux-x86_65-1.0-8174-pkg2.run but how do I run that? Is there a way to run it in the command line?  Because I cant get past the login screen it just freezes with glitches on the screen.

---

### Post by FluffyElmo on 2005-12-17
You should be able to do the same things using the command line and apt-get. Rough command line equivalents to method one get you started:

```
sudo nano /etc/apt/sources.list
```

Uncomment the lines for the Universe repository (remove the leading #). *Ctrl-O* to save and then *Ctrl-X* to exit. Be careful that lines don't wrap, if they do go down a line and backspace until it's back on one line.
```

sudo apt-get update
sudo apt-get install nvidia-glx nvidia-settings
```
The preceding will update the package list with Universe enabled and install the 2 packages from the guide.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo nvidia-glx-config enable 
sudo nano /usr/share/applications/NVIDIA-Settings.desktop
```
This is the same as the guide, but it uses nano instead of gedit which requires a gui. Again, *Ctrl-O* to save and *Ctrl-X* to exit the editor.

Insert the following lines into the new file:
```
[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA Settings
Exec=nvidia-settings 
Icon= 
Terminal=false 
Type=Application Categories=Application;System;
```

Finally, after saving the modified file, restart your machine:
```
sudo shutdown -r now
```

Hopefully you can figure out what is going on by comparing to the original. If you're unfamiliar with the command line it'll be a bit of a crash course;)

For future, *nano* is a decent little text editor and *apt-get* can do everything Synaptic does, though Synaptic is much prettier. Here are a few basic commands:
```

//will search for all packages with 'nvidia' in them ("| more" shows the results a screen at a time)
apt-cache search nvidia | more 
//will install the package called 'package-name'
sudo apt-get install package-name 
//Un-Installs the package 'package-name'
sudo apt-get remove package-name 

```

Good luck!

---

### Post by FluffyElmo on 2005-12-17
You can try *Ctrl-Alt-2* at the login screen to get to a command line. Alternately when the grub boot text comes up hit the escape key and choose Recovery Mode at the menu.

To run the Nvidia Installer, you have to make it executable and then you can run it. from the directory you've downloaded it to:
```

sudo chmod 777 nvdia-linux-x86_65-1.0-8174-pkg2.run
sudo ./nvdia-linux-x86_65-1.0-8174-pkg2.run

```

You will have to install the *build-essentials* etc using the command line but the guide tells you what you need. I might try the driver version in Universe (Method 1) first to see if that works. The Nvidia installer is a little more difficult.

---

### Post by Bowdwin on 2005-12-17
Ok SO IT WORKS! THanks a lot.  I just gottta figure out how to install the BFG one so I can display the higher resolution.  I have another problem tho.  I tried to install it on my other computer a Dell pent 4 1.7 gh.  After the insall it says Grub loading stage 1.5  
Grub loading,
Please wait

Error 18

How do I remove grub from my system?

---

### Post by Bowdwin on 2005-12-17
Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. 

How can i just uninstall grub?

---

### Post by FluffyElmo on 2005-12-17
Great, glad it's working.

You may be able to make your other machine work by making sure your BIOS is set to use large disks (LBA usually?). I don't really know how to remove grub though, you may have to search around.

Unless it is a dual Ubuntu/Windows boot? If so I think you can remove grub from the recovery console or usinga  boot disk and *fdisk /mbr* but I would search on that first, it's been a long while since I've done anything with that.

---

### Post by Bowdwin on 2005-12-17
Yeah I went into the console for xp and type fixmdr which installed the windows boot loader over grub.  Thanks for all your help.  I am gonna go see if I can get the BFG graphics driver to work so i can increase my resolution.  Do i just change the end ext of that file to an .exe?

---

### Post by Bowdwin on 2005-12-17
So there no way to install it like windows? You have to install things through command promps?

---

### Post by FluffyElmo on 2005-12-18
I have a BFG 6600GT and they just refer you to the standard Nvidia drivers page...but maybe you need the latest driver to support your card. Just download the latest Linux driver from Nvidia and try installing it using Method 2 from the how-to thread and you should be ok.

---

### Post by Bowdwin on 2005-12-18
well fluffy thanks for all your help!

---

### Post by scunc_dvl on 2005-12-22
Once the NVidia thing is running, and finds some kernel stuff it needs, try saying 'no' when it asks about 32-bit compatibility libraries, since they currently seem to break OpenGL in X-windows. Took me a while to figure that one out.

(But don't worry, you can run the nvidia installer again and try those options, before you start messing around with X11 settings like I ended up doing... )

---

