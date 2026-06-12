---
title: "need help with loading nvidia driver"
date: 2006-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by lexus_is250_awd on 2006-11-18
Hi all,

Kinda new to linux and new with Ubuntu Edgy. I want to install nvidia driver for my gforce fx 5900 ultra card and I'm having problems. I followed the directions on how to add repositories with synaptic then download the nvidia drivers which was successful but when i go to run: 

sudo nvidia-glx-config enable in an x-term window I get this error:

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

I'm almost positive that I've downloaded the correct drivers. If anyone can help me cause I'm going nuts and really don't want to go back to windoze.

Thanks!!

---

### Post by mwthrane on 2006-11-18
in terminal:
gksudo gedit /etc/X11/xorg.conf

replace nv with nvidia

It only says nv one place so should be pretty simple. After that reload xserver or reboot.

---

### Post by lexus_is250_awd on 2006-11-18
I know how to do that but, why am I getting the error above when I run:

sudo nvidia-glx-config enable

Cause just changing nv to nvidia doesn't do it all. I'm still missing options in /etc/X11/xorg.conf for nvidia settings.

---

### Post by JAPrufrock on 2006-11-18
This might work:
First make sure that all the repositories are uptodate.
> sudo apt-get update
Then install the driver
> sudo apt-get install nvidia-glx
Then run the config file to set the parameters
> sudo nvidia-xconfig

---

### Post by mwillems on 2006-11-19
Fantastic! That did it for me.

I am now using an official 64-bit OS for the first time... cool.

---

### Post by Azakus on 2006-11-19
If you're getting that little annoying Nvidia Logo everytime you boot up. You can get rid of it be adding the line Option "NoLogo" in your xorg.conf file under the "Device" Section.
It looks like this:
```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Option		"NoLogo"
EndSection

```

---

