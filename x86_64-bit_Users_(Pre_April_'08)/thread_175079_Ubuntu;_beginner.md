---
title: "Ubuntu; beginner"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ericunicast on 2006-05-12
I recently installed the latest available version of ubuntu through microsoft vritual pc. The installation went smoothly until the first boot up of the os. the display is in black and white and the resolution is a screen size that is too large for the monitor to handle. Instead, i have to scroll between virtual pc and the ubuntu desktop in order to use the os. I tried adjusting the virtual pc's display settings for the os to no avail. Is there any type of configuration file that I can use or a line of code to edit in order to get my screen size to possibly 1024x768 or even 1280x1024. I am new to the linux experience so any help is much appreciated.

---

### Post by aysiu on 2006-05-12
So System > Preferences > Screen Resolution doesn't work for you?
If you want a config file to edit, try xorg.
Paste these commands in the terminal: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Ptero-4 on 2006-05-13
AFAIK. It won't work. M$ V$PC detects your partitions at startup and if it detects the linux type partitions found in x86 PC's (swap, root, and possibly home) and one or more linux kernels in one of the partitions, it automatically mess up the emulated hardware to make impossible running linux on it. Your only solutions are or get connectix VPC, or get Qemu/Iemulator or use ubuntu PPC.

---

### Post by ssam on 2006-05-14
if you just want to try out ubuntu you will have more luck with the ubuntu live cd. run x86 ubuntu in virtual PC will be slow (years ago i tried running linux in virtual PC and it was not much fun.)

---

### Post by ericunicast on 2006-05-23
The Microsoft Vpc was a concern of mine. I figured that if run under microsft it would probably have errors. Possibly vmware would be a better solution. Im not ready to fully install ubuntu but am eager to do so. What does anyone know about the file systems? security? etc.?

---

### Post by EuroCity on 2006-05-26
On [http://vpc.visualwin.com](http://vpc.visualwin.com) there are instructions for solving the video problem (also works with VPC for Mac): the default colour depth must be set to 16 instead of 24 (the Ubuntu default, which VPC doesn't support).

Otherwise, Ubuntu works well in VPC, but of course rather slowly: especially the install is very slow, at least with the text-mode CD.

Networking requires the Virtual Switch mode, if I'm not mistaken.

---

### Post by ericunicast on 2006-05-26
from what i have learned, all larger OS's run rather slowly in Vpc. Windows 2003 server is a killer when installing active directory and trying to enforce any type of auditing. I have ordered a set of dapper drake, and i can;t wait to install it on my newly constructed 64 bit machine, thank you ebay,

---

