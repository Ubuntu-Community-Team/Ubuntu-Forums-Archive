---
title: "Intel 3100 Graphics Problem"
date: 2008-05-24
forum: x86 64-bit Users
---

### Post by Brian96 on 2008-05-24
I have a Dell Inspiron 530 using the Intel 3100 onboard GMA and I'm running Hardy 64 bit. Compiz works, but my screen has a black bar around the sides and bottom. I've tried running "sudo dpkg-reconfigure xserver-xorg" to be sure the proper driver ("intel" right?) is in use, but the program quit after the keyboard configuration (no error messages, just quit).

Any ideas?

---

### Post by Sockerdrickan on 2008-05-25
Ummm... disable compiz?

---

### Post by Yellow Pasque on 2008-05-25
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mspaul on 2008-05-25
running dell 530 core 2 duo 1 gig ram latest bios 

I'm a Linux newb...  I can't get this card to work at all...  it slows down the system with compiz, when I try to adjust it, I have found that it isn't detected and the vesa driver is being used.

I went ahead and purchased a geforce pcie 8400.  hopefully that solves the problem.

I have found various bugs with dell 530 and ubuntu (linux in general... sata bios settings don't cooperate with the hardy kernel)

so I would like to reinstall hardy is there a way to update the kernal (for a newb)????  I have found post stating that the newer linux kernel has solved a few of the problems with the dell 530/intel situation.

---

### Post by Brian96 on 2008-05-25
> **Temüjin said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I've tried that, too.

Anybody know why the dpkg-reconfigure utility would close (possibly crash?) before it gets to the graphics part?

---

### Post by Brian96 on 2008-05-25
> **Tux0r said:**
> Ummm... disable compiz?

That kind of defeats the purpose, but just for the sake of understanding, how should that help?

---

### Post by Yellow Pasque on 2008-05-25
> so I would like to reinstall hardy is there a way to update the kernal (for a newb)???? I have found post stating that the newer linux kernel has solved a few of the problems with the dell 530/intel situation.

Why do you need to reinstall? Do you remember what you did when your issue began (e.g. programs you installed) or has it always been a problem? I mean, if you just recently installed and haven't done a lot of work customizing, you could try it.

To get the latest available Ubuntu kernel, just keep your system up to date with Update Manager or apt-get update/upgrade.
If you want the latest "vanilla" kernel from kernel.org, it's not too difficult, but it can be tedious to configure the kernel.

Here's how I do it (based on the "Old-Fashioned Debian Way" in this guide: [https://help.ubuntu.com/community/Kernel/Compile ](https://help.ubuntu.com/community/Kernel/Compile ))
1. Get the necessary packages:
```
sudo apt-get install linux-kernel-devel fakeroot build-essential libncurses5 libncurses5-dev
```
2. Download the kernel source to your Desktop: [Here](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.25.4.tar.bz2)
3. Unpack and move the kernel source:
```
sudo mv ~/Desktop/linux-2.6.25.4.tar.bz2 /usr/src
sudo tar -xvjf linux-2.6.25.4.tar.bz2
cd linux-2.6.25.4/
```
4. This is the fun part. (At least I find it fun. You may not be so nerdy, err, patient.) You get to configure your kernel. There are a few interfaces available, so that part shouldn't trip you up. I prefer the text/keyboard interface, but if you want a GUI, you can try *make gconfig* or *make xconfig*
```
make menuconfig
```

You'll need some packages for xconfig:
```
sudo apt-get install qt3-dev-tools libqt3-mt-dev
```
And for gconfig:
```
sudo apt-get install libgtk2.0-dev libglade2-dev
```

After the kernel is configured, we'll make .deb packages for easy install/uninstalling:
```
fakeroot make-kpkg --initrd kernel-image kernel-headers
```

To make sure you get the Ubuntu splash screen:
```
echo vesafb | sudo tee -a /etc/initramfs-tools/modules
echo fbcon | sudo tee -a /etc/initramfs-tools/modules
```

Now, we install the new kernel:
```
sudo dpkg -i linux-image-2.6.25.4_2.6.25.4-10.00.Custom_amd64.deb linux-headers-2.6.25.4_2.6.25.4-10.00.Custom_amd64.deb
```

And we need to configure GRUB and add the new kernel:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Brian96 on 2008-05-26
> **Brian96 said:**
> I've tried that, too.

Anybody know why the dpkg-reconfigure utility would close (possibly crash?) before it gets to the graphics part?

Bump.

I've now tried disabling compiz and also running dpkg-reconfigure from the "failsafe terminal" session, and get the same results. I don't even know how to tell which xserver video driver I am using because dpkg-reconfigure doesn't go past the keyboard settings.

---

### Post by Brian96 on 2008-05-26
I've decided to post my xorg.conf file contents to see if that gives anybody any ideas.

[quote=xorg.conf]
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
[/quote]

It almost looks like the video devices have not been configured at all (or are configured elsewhere?).

---

### Post by Brian96 on 2008-05-26
Well, I determined through the "Screens and Graphics" tool that I am using the VESA driver, but I still don't know how to change it (changing it there failed).

---

### Post by Yellow Pasque on 2008-05-26
> **Brian96 said:**
> Well, I determined through the "Screens and Graphics" tool that I am using the VESA driver, but I still don't know how to change it (changing it there failed).
Again:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can also change the driver by manually editing your /etc/X11/xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```
A search for intel xorg.conf should give you plenty of resources.

---

### Post by Brian96 on 2008-05-26
> **Temüjin said:**
> Again:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You can also change the driver by manually editing your /etc/X11/xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```
A search for intel xorg.conf should give you plenty of resources.

I have TRIED <sudo dpkg-reconfigure -phigh xserver-xorg> multitudinous times, both before and after starting this thread. The utility shuts down (without an error message) after the the keyboard configuration. This is one of the main things I am trying to get feedback on.

I also posted my xorg.conf in the hopes that clues may be found there. From the looks of it, the video card is not being properly detected at all. I know this is a very common system, so I am trying to figure out why I am having so much trouble with it.

---

### Post by Yellow Pasque on 2008-05-26
```
Section "Device"
Identifier "Configured Video Device"
EndSection
```
----->
```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection
```

---

