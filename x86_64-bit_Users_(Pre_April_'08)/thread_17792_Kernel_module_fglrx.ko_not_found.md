---
title: "Kernel module fglrx.ko not found"
date: 2005-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by beppo on 2005-03-02
I tried to install the ATI 64 drivers following the instructions on [http://www.stanchina.net/~flavio/debian/fglrx-installer.html](http://www.stanchina.net/~flavio/debian/fglrx-installer.html)
using the make-kpkg method. (I have a custom built kernel also built with make-kpkg following the instruktions on the Ubuntu AMD64 CD)

After a number of tries I managed to get the kernel module fglrx.ko.
However, it seems that it was either created at a wrong location or that I miss a symbolic link, because the only way I can load the kernel module is a insmod with the comlete path to the module (/lib/modules/2.6.8.1-1.4/misc/fglrx.ko).

I added fglrx to /etc/modules but due to the problem the module is not loaded at start-up and as I am rather a newb I wonder how I can automate the loading during start-up. Should I create an entry in the /etc/rc?.d directories???

Here are more details.
Kernel source are latest 2.6.8.1. They are unpacked in /usr/local/src/kernel-K8-1.4.
/usr/src/linux points to this directory.
I used 
make-kpkg --append-to-version "-1.4" --added-modules fglrx-kernel-src modules_image
to build the package.

Any help (and also background information) is appreciated.

---

### Post by Tobu on 2005-03-03
I think you need a:
sudo depmod -ae
to register the new module.

Also, you can check if uname -r is 2.6.8.1-1.4 just in case.

---

### Post by beppo on 2005-03-19
Hi Tobu,

thank for your answer. Indeed uname -r was NOT 2.6.8.1-1.4. I did not understand, that there is a difference between the revision and the version. 
Deinstalling the packages rebuilding them with no version but the right revision worked fine.
Thanks for the help.

---

