---
title: "WiFi difference between 32 bit and 64 bit?"
date: 2008-08-10
forum: x86 64-bit Users
---

### Post by pgte3 on 2008-08-10
The following worked on my (Ubuntu 8.04) 32 bit partition but does not work on my 64 bit partition (see below). I think I should be able to use the same driver as long as I compile it on my 64 bit partition. Any ideas?

Within Gnome desktop:
System-->Hardware Drivers--> uncheck (unenable) HAL

From a terminal window:
wget [http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

sudo apt-get install build-essential

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot

---

### Post by Yellow Pasque on 2008-08-10
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by pgte3 on 2008-08-11
Thanks for the link. Looking at the instructions in the link it appears there is a 64 bit driver. I will try these steps and report back.

---

### Post by pgte3 on 2008-08-11
I followed the steps in this link and was able to get my wifi working on my AMD 64.

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Thanks

---

