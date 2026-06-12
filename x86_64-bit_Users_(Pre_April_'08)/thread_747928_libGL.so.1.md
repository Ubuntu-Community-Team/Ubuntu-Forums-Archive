---
title: "libGL.so.1"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by talsemgeest on 2008-04-07
When I was trying out 64bit, I wanted to install the ati driver, using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).

All was good, up until the part where it tells me to do the following: > If using 64bit make sure to collect package "ia32-libs" and " libGL.so.1" before proceeding! ia32-libs was fine, it was in the repos. The more problematic part was the libGL.so.1. It wasn't in the repos and I couldnt find how to get it. I got libgl1-mesa-swx11 but that didnt do the trick as the installation still complained about libGL.so.1.

Any ideas about what I can/should do? All help is appreciated.

Thanks in advance,

talsemgeest

---

### Post by Cappy on 2008-04-07
I'm 90% sure that is bad advice because libGL.so.1 is generated when you install video drivers. It doesn't make any sense to *need* what you are trying to *do*.

The only relevant package for you with libGL.so.1 is what is in "Method 1: Install the Driver the Ubuntu Way" in that wiki.

That wiki is REALLY REALLY badly written for Method 2. 

More info:
[http://packages.ubuntu.com/gutsy/xorg-driver-fglrx](http://packages.ubuntu.com/gutsy/xorg-driver-fglrx)

---

### Post by talsemgeest on 2008-04-07
But the driver itself asks for it as well, which is why you really need it

---

### Post by Cappy on 2008-04-07
Looks like I was 100% wrong then. Hah. I'm funny. Hah. Hah. /end laughter

Just guessing here but try
```
sudo apt-get install libgl1-mesa-glx
```

and see if there is a libGL.so.1 (exactly that name) in /usr/lib with
```
ls /usr/lib/libGL.*
```

If not, create a link with
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```

Make sure of the same thing in /usr/lib32 also
```
ls /usr/lib32/libGL.*
```

---

### Post by Jouke74 on 2008-04-07
I did this:

> sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs

> sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy

> gksu gedit /etc/default/linux-restricted-modules-common
Type: DISABLED_MODULES="fglrx"
save
close

> sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb
This will produce errors for amdcccle.

> sudo apt-get install -f
This forces the dependencies to be installed 
(It installs the restricted Ubuntu FGLRX driver as far as I can tell including the required library).

> sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
Can only be done after previous step.

> sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb
All of them need to be redone.

> Then type "Y" when asked to overwritre the compiz files.

> sudo aticonfig --initial
Needs to be done for cccle to work.

On a X1600 and a clean Gutsy install.
Beware on a unclean Xubuntu Gutsy install this failed to work, everything was very slow.

Don't use the Mesa lib, you will have more trouble getting rid of it later....

---

### Post by talsemgeest on 2008-04-07
Cool, thanks guys, I'll try it out when I get a chance.

---

