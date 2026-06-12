---
title: "[SOLVED] RTL8187 hell again at 8.10 64-bit"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by chessboxing on 2008-10-30
hello
[COLOR="DarkGreen"][SIZE="4"]UPDATED WITH SOLUTION:[/SIZE][/COLOR]

wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/

wget [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)

tar xzf drv.tar.gz
tar xzf stack.tar.gz

sudo gedit ./beta-8187/r8187.h
**and find the line:**

#include <asm/semaphore.h>

**and change it to:**

#include <linux/semaphore.h>

sudo patch -Np1 -i rtl8187_2.6.27.patch

**Then I put rtl8187 to the blacklist:**

sudo gedit /etc/modprobe.d/blacklist and add “blacklist rtl8187” as a new line.
**Then remove the present driver:**

sudo ifconfig wlan0 down
sudo rmmod rtl8187

make
sudo make install

reboot & enjoy

-------------------------------------------------------------------------
7.04 was a pain in the ***, but I managed to get it working with the instructions at aircrack, see beneath.
Deleting old driverfiles:
```
 rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
 rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
 rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
 rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
 rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
 rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
 rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
```
then
Install the new drivers and patching
```
ifconfig wlan0 down	 
rmmod r8187 rtl8187 2>/dev/null
wget http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.24v3.patch
make
make install
```
I used rtl8187_2.6.27.patch instead of cours, which it also located on the aircrack website. Since 8.10 uses 2.6.27 kernel.

The original installation problem is that my internet is just not working. It shows connected, but it's like a photoshoped desktop, just like with 7.04-7.10-8.04.
Any suggestion?
my dmesg when I just installed 8.10 and modinfo rtl8187:
```
suntzu@suntzu-desktop:~$ dmesg
[   11.477611] phy0: hwaddr 00:15:af:51:e9:eb, RTL8187vB (default) V1 + rtl8225z2
[   11.477633] usbcore: registered new interface driver rtl8187


suntzu@suntzu-desktop:~$ modinfo rtl8187
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     AD409A15F56FDE2BEB94FA5
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*
depends:        mac80211,eeprom_93cx6,cfg80211,usbcore
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
```

---

### Post by nss0000 on 2008-10-30
Don't suffer. Buy a PCI-card. They cost $20.00

---

### Post by chessboxing on 2008-10-30
> **nss0000 said:**
> Don't suffer. Buy a PCI-card. They cost $20.00

Wrong reasoning, because Than you also can say, delete ubuntu and continue using windows which is a better solution. Because I already have it, and it cost me €0. No suffering as well. Maybe I should because it's actually irrelevant to deal with a problem like this. 
Next

---

### Post by chessboxing on 2008-10-31
Brothers and sisters, I guess the best solution is to go back to LTS 8.04, the bird.
Technically it is solved:lolflag:

---

### Post by rashwan on 2008-11-03
Nah , i see that your previous solution (back to windows) is the best

---

### Post by chessboxing on 2008-11-06
> **rashwan said:**
> Nah , i see that your previous solution (back to windows) is the best

SOLVED!!!!! H4ter

---

### Post by Lukian on 2008-11-13
After following the instructions wifi-radar no longer functions.

$ sudo wifi-radar
No wifi-device found. Exiting.

---

### Post by dse.37 on 2008-11-18
Will this only work with the 64bit version of Intrepid?

I used these drivers for a long time in Gutsy without issue, but I've just tried this with 8.10 and get nothing but "undefined!" errors after I run make and when it's trying to build modules.

Am I missing something?

---

### Post by chessboxing on 2008-11-20
> **dse.37 said:**
> Will this only work with the 64bit version of Intrepid?

I used these drivers for a long time in Gutsy without issue, but I've just tried this with 8.10 and get nothing but "undefined!" errors after I run make and when it's trying to build modules.

Am I missing something?

I tested it only with the 64-bit (8.04.1 - 8.10) version. You'd better stick with ubuntu 8.04.1 LTS, since I didn't get a good range with 8.10, still worked though. It's working like a charm in 8.04.1 64-bit.

---

