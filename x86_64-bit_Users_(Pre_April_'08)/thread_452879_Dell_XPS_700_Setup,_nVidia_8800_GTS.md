---
title: "Dell XPS 700 Setup, nVidia 8800 GTS"
date: 2007-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by pcbroch on 2007-05-23
Just thought I'd create a thread with the various steps for my Feisty installation on a Dell XPS 700.  Hopefully it'll help someone else, but it's mostly to help me remember when I need to reinstall.

[COLOR="Red"]
[SIZE="3"]Clean Install[/SIZE][/COLOR]
I started with a fresh install of Feisty x86_64, after which pretty much everything was recognized and configured properly.

[COLOR="Red"][SIZE="3"]Splash option during boot[/SIZE][/COLOR]
The first issue I had was that my videocard somehow does not like the "splash" kernel boot option.  I just get a blank screen and have no way of getting a console.  So at the first boot, you need to hit 'e' on the grub menu, and get rid of the "splash" option on the boot line.  This should allow a first boot, but it will not be persistent upon reboot.  I simply edited /boot/grub/menu.lst and got rid of the "splash" keywork on the kernel boot line and on the 2 lines it appeared:

```

# defoptions=quiet splash 

```
becomes
```

# defoptions=quiet

```

and 

```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=803447af-8383-45d1-bea2-8e1bc9898baa ro quiet splash

```
becomes
```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=803447af-8383-45d1-bea2-8e1bc9898baa ro quiet

```

[COLOR="Red"][SIZE="3"]Getting latest updates[/SIZE][/COLOR]
I then got the latest updates by editing /etc/apt/sources.list and uncommenting the 'backports' repositories, after which I ran:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

[COLOR="Red"][SIZE="3"]nVidia 8800GTS and nVidia 97.55 driver[/SIZE][/COLOR]
The biggest issue is the video card.  Installing the nvidia-glx-new (97.55) driver included with Feisty does not install the modules properly, resulting in X not working.  A few simple steps are required to get it working again:

```

sudo apt-get install nvidia-glx-new

```

What follows is a shameless rip from [this thead]("http://ubuntuforums.org/showthread.php?t=449105&highlight=libwfb.so&page=2").  Get the driver package from nvidia and extract it:
```

wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sh NVIDIA-Linux-x86-1.0-9755-pkg1 -x

```
or, if using AMD64:
```

wget http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run -x

```

Copy the missing module and link to it:
```

cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
cd /usr/lib/xorg/modules
sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so

```

Finally, activate the driver
```

sudo nvidia-glx-config enable

```

Beryl will likely be missing window borders, the following should fix this problem.:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```

After a reboot, X should be fine.


[COLOR="Red"][SIZE="3"]Installing other apps[/SIZE][/COLOR]
A few apps I use, to save me from finding out I need to install something new before using it:
```

sudo apt-get install beryl beryl-manager ia32-libs build-essential wireshark openssh-server checkgmail vim-gnome

```

I also installed firefox32 following [Killz excellent howto]("http://www.ubuntuforums.org/showthread.php?t=202537"), to get flash plugin and java functionnality.

---

### Post by prostock3 on 2007-06-26
Hi Thanks for the post on driver install.  for some reason my 8800gts still has issues with gnome.  i do the following:


Hi,

I've been trying to get gnome installed for a while but with no success.  I think it has to do with my 8800gts nvidia video card.

First i installed my video card via instruction from another post:
1.  sudo apt-get install nvidia-glx-new
2.  wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)
3.  sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
4.  cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
5.  cd /usr/lib/xorg/modules
6.  sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so
7.  sudo nvidia-glx-config enable

Then I installed gnome with:

apt-get install x-window-system-core xserver-xorg gnome-desktop-environment 


I get error message when trying to run startx:
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to kiad the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining.


Does anyone know how I go about debugging this?

Thanks!

---

### Post by heldal on 2007-06-28
> **prostock3 said:**
> Hi Thanks for the post on driver install.  for some reason my 8800gts still has issues with gnome.  i do the following:


Hi,

I've been trying to get gnome installed for a while but with no success.  I think it has to do with my 8800gts nvidia video card.

First i installed my video card via instruction from another post:
1.  sudo apt-get install nvidia-glx-new
2.  wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)
3.  sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
4.  cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
5.  cd /usr/lib/xorg/modules
6.  sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so
7.  sudo nvidia-glx-config enable

Then I installed gnome with:

apt-get install x-window-system-core xserver-xorg gnome-desktop-environment 

!

To be able to start X you first have to load the module installed in step 1 above. Either reboot or issue the command "sudo modprobe nvidia".

---

### Post by sirius11 on 2007-07-01
which mean that : newbies are better to forget about installing ubuntu on a computer with a 8800 card.

or  as the man said : " First i installed my video card via instruction from another post"=    I wish you would of said where is that other post.

---

### Post by Sockerdrickan on 2007-07-02
> **sirius11 said:**
> which mean that : newbies are better to forget about installing ubuntu on a computer with a 8800 card.

or  as the man said : " First i installed my video card via instruction from another post"=    I wish you would of said where is that other post.
It would work if I had an integrated card first and then install driver 100.14.11 right? I'm getting a 8800 in 2 weeks

---

