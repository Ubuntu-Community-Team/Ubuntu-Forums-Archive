---
title: "nVidia driver install"
date: 2008-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by jomasecu on 2008-02-01
Very new to Linux, trying to get the drivers for my graphics card on here.

I used ctrl+alt+F1 to get the terminal, then quit the x server with "/etc/init.d/gmd stop". Found that stuff out on this forum. After that I cd to my Desktop where the .run file I got from nVidia's site was saved, and type "sh NVI...pkg2.run" I get this:

"No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site (ftp://download.nvidia.com)?" [Yes/No]

I select Yes and...

"No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel." [OK]

"ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package." [OK]

So... I have no idea what to do now.

---

### Post by astoltz on 2008-02-01
I think the package you need is libc6-dev;```
sudo apt-get install lib6c-dev
```But being new, I'd suggest sticking to the Nvidia driver available through the restricted drivers manager.

---

### Post by jomasecu on 2008-02-01
That driver won't let me go above 640x480x50Hz, and the default driver (before I enabled the restricted one) caused the computer to freeze after a couple minutes.

Tried that command:
"E: couldn't find package lib6c-dev"

---

### Post by astoltz on 2008-02-01
Well the driver from the Nvidia site works fine on my system, but then again so did the others.  Good luck...

---

### Post by astoltz on 2008-02-01
> **jomasecu said:**
> Tried that command:
"E: couldn't find package lib6c-dev"

Hmmm, that's strange.  I'm on a 64-bit system, maybe the package is named slightly differently on 32-bit.  Try searching for libc.  The "dev" part is what supplies the needed header files.

---

### Post by RRS on 2008-02-01
> **jomasecu said:**
> 
Tried that command:
"E: couldn't find package lib6c-dev"
I think lib6c-dev is part of the  build-essential
Try:
```
sudo apt-get install build-essential
```

---

### Post by eewujian on 2008-02-01
I'm a newbie too. It took me nearly a month to figure out how to install the NVIDIA driver on my system. It works perfectly in my system now. I summarized the steps to install the driver here. Good luck!
Jian

NVIDIA Linux Display Driver - x86 Installation Guide for ubuntu 7.10 Users

1) Download NVIDIA display driver from [www.nvidia.com](www.nvidia.com)
NVIDIA-Linux-x86-169.09.pkg1.run

2) Install packages:
linux-kernel-devel
pkg-config
xserver-xorg-dev

3) Uninstall packages:
nvidia-glx
linux-restricted-modules
linux-restricted-modules-common

4) Delete files (if exist):
/etc/init.d/nvidia-glx
/etc/init.d/nvidia-kernel
/lib/linux-restricted-modules/.nvidia_new_installed

5) Exit X
sudo /etc/init.d/gdm stop
Press "Ctrl+Alt+F1"
log in

6) Install NVIDIA display driver
sudo sh NVIDIA-Linux-x86-169.09.pkg1.run
(Follow instructions to compile the NVIDIA kernal interface)

7) Restart X
sudo /etc/init.d/gdm restart

8) Create customized X server configuration file (optional)
a) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
b) Go to "Applications->System Tools->NVIDIA X Server Settings->X Server Display Configuration" and customize settings (to anything you want).
c) Click "Save to X Configuration"
d) Uncheck "Merge with existing file."
e) Click "Show preview..."
f) Open another terminal and type "sudo gedit /etc/X11/xorg.conf"
g) Replace the content in the opened file by the content in the window that h) opened by clicking "Show preview...".
i) Save the file.
j) Exit X
k) Restart X

---

### Post by astoltz on 2008-02-01
I can see both packages in Synaptic.  In fact, build-essential depends on libc6-dev.  But like I mentioned, that is on a 64-bit system.  Try libc-dev.  I don't think you need the whole build-essential package.

---

### Post by jomasecu on 2008-02-01
Can anyone confirm what eewujian posted? That's insanely complicated to install some graphics drivers.

---

### Post by jomasecu on 2008-02-02
> **astoltz said:**
> I can see both packages in Synaptic.  In fact, build-essential depends on libc6-dev.  But like I mentioned, that is on a 64-bit system.  Try libc-dev.  I don't think you need the whole build-essential package.

E: Package libc-dev has no installation candidate

Would build-essential be harmful somehow? 
I am on 64-bit as well.

---

### Post by soxs on 2008-02-02
> **jomasecu said:**
> 
Would build-essential be harmful somehow? 
I am on 64-bit as well.
No, it's a package required to compile code.

---

### Post by astoltz on 2008-02-02
> **jomasecu said:**
> E: Package libc-dev has no installation candidate
Would build-essential be harmful somehow? 
I am on 64-bit as well.
It certainly wouldn't hurt but I'm guessing that it won't install either.  Build-essential is just a meta-package that installs several other packages via dependencies - libc6-dev is one of them.  I'm more curious why you can't see the libc6-dev package - it's in the main gutsy repository.  Would you mind posting the results of ```
cat /etc/apt/sources.lst | grep deb
```

---

### Post by jomasecu on 2008-02-02
No such file or directory

Edit: found sources.list
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by PmDematagoda on 2008-02-02
The code is actually:-
```
cat /etc/apt/sources.list | grep deb
```

Edit:- Just install the build-essential package using:-
```
sudo apt-get install build-essential
```
That will clean up the required dependencies for the Nvidia driver installer.

---

### Post by jomasecu on 2008-02-02
That worked, but after installing the drivers I got this:

"WARNING: Unable to perform the runtime configuration check for library 'libGL.so.1' ('usr/lib32/libGL.so.169.09'); assuming successful installation."

When I restarted I got the message "Ubuntu is running in low-graphics mode" and I can now get to 800x600x85Hz. (at least I can see the bottom of most dialogs now. :-P )

I tried to go into the configuration and select the driver type but I couldn't get it to test successfully. If it's helpful, the card is a Leadtek Winfast GeForce 6800 256MB.

---

### Post by PmDematagoda on 2008-02-02
Kill the GUI again as given previously, and reinstall the driver, after that is done, reconfigure the X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```

After that is done, execute:-
```
sudo /etc/init.d/gdm start
```

---

### Post by jomasecu on 2008-02-02
Same results.

---

### Post by jomasecu on 2008-02-02
> **eewujian said:**
> I'm a newbie too. It took me nearly a month to figure out how to install the NVIDIA driver on my system. It works perfectly in my system now. I summarized the steps to install the driver here. Good luck!
Jian

NVIDIA Linux Display Driver - x86 Installation Guide for ubuntu 7.10 Users

1) Download NVIDIA display driver from [www.nvidia.com](www.nvidia.com)
NVIDIA-Linux-x86-169.09.pkg1.run

2) Install packages:
linux-kernel-devel
pkg-config
xserver-xorg-dev

3) Uninstall packages:
nvidia-glx
linux-restricted-modules
linux-restricted-modules-common

4) Delete files (if exist):
/etc/init.d/nvidia-glx
/etc/init.d/nvidia-kernel
/lib/linux-restricted-modules/.nvidia_new_installed

5) Exit X
sudo /etc/init.d/gdm stop
Press "Ctrl+Alt+F1"
log in

6) Install NVIDIA display driver
sudo sh NVIDIA-Linux-x86-169.09.pkg1.run
(Follow instructions to compile the NVIDIA kernal interface)

7) Restart X
sudo /etc/init.d/gdm restart

8) Create customized X server configuration file (optional)
a) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
b) Go to "Applications->System Tools->NVIDIA X Server Settings->X Server Display Configuration" and customize settings (to anything you want).
c) Click "Save to X Configuration"
d) Uncheck "Merge with existing file."
e) Click "Show preview..."
f) Open another terminal and type "sudo gedit /etc/X11/xorg.conf"
g) Replace the content in the opened file by the content in the window that h) opened by clicking "Show preview...".
i) Save the file.
j) Exit X
k) Restart X

Tried this, and got some error messages...

"ERROR: Unable to create '/usr/lib/nvidia/libGL.so.1.2.xlibmesa' for copying (no such file or directory)"
"WARNING: Unable to restore file '/usr/lib/nvidia/libGL.so.1.2.xlibmesa'."
And the same two messages for these files:
usr/lib32/tls/libnvidia-tls.so.100.14.19
/lib/modules/2.6.22-14-generic/volatile/nvidia.ko

When I restarted X, I was still stuck in low-graphics mode.

---

### Post by damoisture on 2008-02-02
> **jomasecu said:**
> Can anyone confirm what eewujian posted? That's insanely complicated to install some graphics drivers.

I just ran those settings and so far, it looks totally sweet. I have a Gigabyte 7300LE and was having problems with the system locking up every 1-3 days. So we'll see if these new drivers fix it.\

eewujian, thank you so much for the instructions.

---

