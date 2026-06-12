---
title: "AMD athlon 64 X2 Dual core processor 5200+"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by GnomeFoot on 2007-09-15
Just got my new computer with, the processor above and NVIDA GeForece 8500GT. Is it compatible with linux? Had ubuntu before on my old computer and want it on this one to.

---

### Post by John.Michael.Kane on 2007-09-15
The NVIDA GeForece 8500GT is supported under ubuntu. You need to install the nvidia drivers.

The nvidia-glx-new driver in the repos should work. to use them 
```
gksudo aptitude install nvidia-glx-new
```

Followed by
```
sudo nvidia-xconfig
```

Then reboot.

Should those drives not fit the bill.This is how one member installed the newest drivers.
[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

---

### Post by GnomeFoot on 2007-09-15
How about the processor?

---

### Post by John.Michael.Kane on 2007-09-15
> **GnomeFoot said:**
> How about the processor?

Kernel should see the processor without issue. Your main concern will be with the main board your use.

---

### Post by GnomeFoot on 2007-09-15
motherboard: Asus M2N NF430 AM2

---

### Post by John.Michael.Kane on 2007-09-15
> **GnomeFoot said:**
> motherboard: Asus M2N NF430 AM2

The kernel included with feisty 'might' have problems with the ASUS M2N eth0/net and sound chip, If this is still the case, Which you won't know until you test the hardware. you will have to compile a current kernel or test the kernel in gutsy 7.10.

---

### Post by GnomeFoot on 2007-09-15
but if I test the livecd then I should get a good picture if it works or not? is there any livecd for gutsy?

---

### Post by John.Michael.Kane on 2007-09-15
> **GnomeFoot said:**
> but if I test the livecd then I should get a good picture if it works or not? is there any livecd for gutsy?

Yes you can gage the hardware's support through the use of the live cd.

Heres a link for 7.04.
[Feisty Fawn 7.04 Desktop Live CD]("http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-amd64.iso")

Here's a link for gutsy.
[Ubuntu 7.10 (Gutsy Gibbon)livecd]("http://cdimage.ubuntu.com/daily-live/current/gutsy-desktop-amd64.iso")

Here are some boot command you might need, however they should only be used if the live cd will not boot on its own.

With the ubuntu cd in the drive. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line.Just add the above commands to it. This should allow the machine to install, and boot as normal.

The above should get you going.

---

### Post by GnomeFoot on 2007-09-20
I try to run the way you said, by pressing F6 and write that. But my screen turns black, any problem with the screen compat maby?

---

### Post by GnomeFoot on 2007-09-22
Got it working, but when I installed the nvidia drivers my xorg wont start and I cant log on. how do I fix that?

---

### Post by Sockerdrickan on 2007-09-23
Did you really do sudo nvidia-xconfig

---

### Post by WhistlerUK on 2007-09-23
I too have just build a new PC everything works but I can't get the nvidia drivers to install
its a 8500GT (Zotac Geforce 8500 GT) 
[IMG]http://www.zotac.com/Products/W-LRB-8500GT-N28.jpg[/IMG]

---

### Post by WhistlerUK on 2007-09-23
> (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(EE) No drivers available.

Fatal server error:
no screens found

I tried following this guide too with no luck: [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

---

### Post by John.Michael.Kane on 2007-09-23
> **GnomeFoot said:**
> Got it working, but when I installed the nvidia drivers my xorg wont start and I cant log on. how do I fix that?

What if any error msg are output to the screen during the boot process?
How did you install the drivers?

To reset your xorg, and try enabling the driver sans composite
Step one
1)sudo dpkg-reconfigure -phigh xserver-xorg
Step two
2)sudo nvidia-xconfig --no-composite

> **WhistlerUK said:**
> I too have just build a new PC everything works but I can't get the nvidia drivers to install
its a 8500GT (Zotac Geforce 8500 GT) 
[IMG]http://www.zotac.com/Products/W-LRB-8500GT-N28.jpg[/IMG]

Same questions

What if any error msg are output to the screen during the boot process?
How did you install the drivers?

To reset your xorg, and try enabling the driver sans composite
Step one
1)sudo dpkg-reconfigure -phigh xserver-xorg
Step two
2)sudo nvidia-xconfig --no-composite

Also if the above doesn't work for some reason.Your options are.

1) Use the method outlined by Six
[How I got the latest NVIDIA 100.14.11 drivers installed]("http://ubuntuforums.org/showthread.php?t=514161")
2) Use the envy script 
[Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by John.Michael.Kane on 2007-09-23
> **WhistlerUK said:**
> I tried following this guide too with no luck: [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

Then the issue is with that guide, and not the drivers. 

Have any of you tried the driver in the repo before using that guide? The standard nvidia-glx-new driver should support your cards.

---

### Post by WhistlerUK on 2007-09-23
Many thanks, using Envy I was able to get the card installed thank you :)

---

### Post by ac1964 on 2007-10-18
Hi,

I'm new to Linux and Ubuntu, so bear with me.

I have an MSI MEGA PC MP51c with an AMD 4600+ CPU.
I have Ubuntu 7.04 running smoothly on it at the minute.

I want to install 7.10.

Should I install the 64 bit or the standard version of 7.10?
What difference will it make?
Will I need different versions of software to run on 64 bit Ubuntu.

Can anyone recommend a good book on Ubuntu, as I have moved over from Windozzzzzzzzzzzz and don't want to go back.

Regards,
Adrian

---

### Post by Kilz on 2007-10-18
> **ac1964 said:**
> Hi,

I'm new to Linux and Ubuntu, so bear with me.

I have an MSI MEGA PC MP51c with an AMD 4600+ CPU.
I have Ubuntu 7.04 running smoothly on it at the minute.

I want to install 7.10.

Should I install the 64 bit or the standard version of 7.10?
What difference will it make?
Will I need different versions of software to run on 64 bit Ubuntu.

Can anyone recommend a good book on Ubuntu, as I have moved over from Windozzzzzzzzzzzz and don't want to go back.

Regards,
Adrian

You question is a common one. But there is no standard version of Ubuntu. All versions are standard for the hardware they are designed to install to. If you have a 32bit (i386) install you will need to do a complete install to move to 64bit (amd64). Since its new release time its a great time to do it. 
You will get some performance boost, how much will depend on what you use the computer for. But common tasks like backing up dvd's , ripping cd's , 3d modeling, and others can get up to a 30% increase in performance.
[You might also want to read this post for more info.]("http://ubuntuforums.org/showthread.php?t=368607")

---

