---
title: "Ubuntu 9.04 modules.dep"
date: 2009-08-07
forum: x86 64-bit Users
---

### Post by @echo off on 2009-08-07
I am attempting to run 9.04 persistently from an 8gb usb drive. when it boots up I am given 2 softreset failures and a /lib/modules/2.6.28-11-generic/modiles.dep file not found error. Is there any wayto fix this? If not, this entire situation could be avoided if I coud just findout how to make atheros ar5007 wireless card work with 8.10. 8.10 works just fine of of my usb. 9.40 gets the same failures with the i386 and the mad64 versions. So i need to  either:

1) fix the errors and pray that 9.04 supports my wireless card

                                                                    or
2) Fix up 8.10, only solve one problem, and still have the same out come

Can anyone help me fix one of these situations, preferably the easiest one? 


As a side note, in 8.10 I did get the package from Canonical for the ath5k chips and it did register that I had a "ar5***" chip but I could not find any wireless networks.

---

### Post by warp99 on 2009-08-08
At the command line run the following:

```
sudo depmod -a
```

That will update the module dependency list. If that doesn't work just reinstall the kernel with modules:

```
sudo apt-get install --reinstall linux-image-$(uname -r)
```

As for your wireless card you can install the backports modules which has better support for some atheros cards if the standard kernel modules do not work or use the madwifi modules that are located in the restricted modules package. Here are the names of the packages:

linux-backports-modules-jaunty
linux-restricted-modules

The restricted modules should be the last resort after backports. If you use the restricted modules you have to blacklist the ath5k modules by adding the module to '/etc/modprobe.d/blacklist.conf' and un-blacklist the ath_pci module by commenting out the module in the file '/etc/modprobe.d/blacklist-ath_pci.conf'.

---

### Post by @echo off on 2009-08-08
I tried the depmod -a, sudo is not a command in busybox, and it didnt appear to do any thing so I rebooted and it definitely did nothing. I tried reinstalling, apt-get and install are not commands. Im going to go back to 8.10 and try the wireless thing. I just have to put it on my flash drive.

edit: solved my wireless problem with 8.10 by--
Hit "alt+f2" to run a command and type: [FONT=monospace]
[/FONT]gksudo nautilusAnd navigate to 
/etc/modprobe.d
Now check each and every file for a line that looks like: 
blacklist ath5k
And just add a "#" character at the beginning of the line.

I never got 9.04 to work

---

