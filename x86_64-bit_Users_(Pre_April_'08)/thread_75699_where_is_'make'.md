---
title: "where is 'make'?"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by slamdunk on 2005-10-14
Hi,

I must compile ndiswrapper 1.4 (it seems not present in ubuntu-cd) and so I have launched classic 'make'. But make is not installed, and so I have searched it on cd and I have not found it. Possible? Or I have searched wrong 'package-name'?

Thanks,
Giulio

---

### Post by RAOF on 2005-10-14
The package you are after is "build-essential"

Just
```
sudo apt-get install build-essential
```
and you're done :)

---

### Post by slamdunk on 2005-10-14
thanks, now 'make' is installed but there are new problems when I try to compile 'ndiswrapper' (after installed kernel-headers too), because I got error because gcc-3.4 is not present. In synaptics I have found just gcc-4.0 but I suppose that kernel is compiled by gcc-3.4 and so it's not possible make linkable modules for kernel.

---

### Post by RAOF on 2005-10-14
It is possible, you just need to install gcc-3.4.  It's parallel installable with 4.

```
sudo apt-get install gcc-3.4
```

Then, you need to tell make to use the new gcc.  To do this, I belive you want:
```
CC = gcc-3.4
export CC
```
and then do your make-ing.

---

### Post by slamdunk on 2005-10-14
gcc-3.4 is not present in cd. I have tried with synaptics and apt-get via console, but both return gcc-3.4 not present.

---

### Post by estel on 2005-10-14
Have you added the universe repos etc. to sources and updated?

---

### Post by slamdunk on 2005-10-14
For using repos I must connect to internet.
For connecting me, I must compile ndiswrapper-modules.
For compiling ndiswrapper modules I must install gcc-3.4.
For installing gcc-3.4 I must connect to internet.

---

### Post by Pablo_Escobar on 2005-10-14
[QUOTE=slamdunk]For using repos I must connect to internet.
For connecting me, I must compile ndiswrapper-modules.
For compiling ndiswrapper modules I must install gcc-3.4.
For installing gcc-3.4 I must connect to internet.[/QUOTE]

A bit tricky isn't it ??
You need to use some other machine to get deb You want :(

---

### Post by slamdunk on 2005-10-14
Yes, but it's a real wrong choice do not include that package. It's not ndiswrapper problem only, but it's for people that must compile modules for modem 56k or usb-adsl for internet connection (or vmware too). You can connect only with pre-compiled binaries or pppoe?

Ok, I can download it from other os right packages for ubuntu...

For me it's wrong don't include 'ndiswrapper' package too, it's few kb and important...

Can anybody tell me dependencies for gcc-3.4?

---

### Post by medication on 2005-10-14
[QUOTE=slamdunk]Can anybody tell me dependencies for gcc-3.4?[/QUOTE]

I'm running Hoary 64bit... but this is what the package manager tells me:
Depends:
gcc-3.4-base (>=3.4.3-9ubuntu4)
libgcc1 (>=1:3.4.3-9ubuntu4)
libc6 (>=2.3.2.ds1-4)
cpp-3.4(<3.45)
binutils(>=3.4.3-9ubuntu4)
Suggested:
gcc-3.4-doc(>=3.4.3-9ubuntu4)
lib32gcc1
Recommended:
libc6-dev(>=2.3.2.ds1-16)

---

### Post by xthaparian on 2005-10-14
Well go to another machine and in the synaptics just download the Gcc3.4 and gcc 3.4 base.

Now there is an option fo installing or just downloading. Just download them.

That should work.

Apart from that I dont know what to do...:cool:

---

### Post by slamdunk on 2005-10-14
thanks medication, I'll download them... with windows xp:(

---

### Post by tHub on 2005-10-14
hm i had to do the same thing, are you trying to install an Encore ethernet card driver or similar(sundance_main.c)?
here are the dependencies [http://packages.ubuntu.com/breezy/devel/gcc-3.4](http://packages.ubuntu.com/breezy/devel/gcc-3.4)
you're gonna need those cpp's at least i needed

---

### Post by slamdunk on 2005-10-15
thx tHub, effectively 'c++' is needed.

However do not include gcc-3.4 it's a real stupid thing... every distro include it!

---

### Post by slamdunk on 2005-10-15
Thanks for help guys,

but manually downloaded packages are too updated and I cannot install them.

I'm going to remove this unusable distro and install opensuse... too lost time!

goodbye and thanks for all

---

### Post by tHub on 2005-10-15
sudo dpkg -i didnt work?

---

