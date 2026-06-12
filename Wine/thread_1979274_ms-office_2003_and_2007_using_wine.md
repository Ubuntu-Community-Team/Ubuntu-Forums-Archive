---
title: "ms-office 2003 and 2007 using wine"
date: 2012-05-13
forum: Wine
---

### Post by fahd on 2012-05-13
Hi folks ...

In the past prior to ubuntu 12.04 (ubuntu 11.10 for instance), i could install both ms-office 2003 and ms-office 2007 using wine 1.2. This solution appealed to those colleagues especially who still stick to ms-windows systems. Now in ubuntu 12.04 (shiped with wine 1.4 and of course wine 1.3 and wine 1.2), when i install wine 1.2 as i did in the past the installer (synaptic) tags wine 1.4 package (very weird), thus i do not get it working (ms-office 200x products). Inspite that the wine dev.team had made a great job, unfortunately they did not strive to make it (wine 1.4) downward compatible with the previous versions of wine. Any clue. Thanks a lot.

Fahd
120513

---

### Post by zombifier25 on 2012-05-13
Wine 1.4 is supposed to have *better* compability with MS products (this is even stated in its changelog)

When upgrading between Wine versions, the config tends to be messed up (because of incompability)
Try deleting the .wine folder and try again.

---

### Post by irishetalon007 on 2012-05-15
I, too, cannot install Office Professional 2003 on Ubuntu 12.04. I've tried on both my amd64 and i386 machines.

I've tried both wine1.4 and wine1.5

Here's some info:

Command line output of WINEARCH=win32 winecfg


jordan2@jordan2-HP-12:~$ WINEARCH=win32 winecfg
wine: created the configuration directory '/home/jordan2/.wine'
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0x100e8ec, overlapped 0x100e8d0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: configuration in '/home/jordan2/.wine' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory




and now here's the output (see file attachment) of trying to run SETUP.EXE from the [CD Root]/OFFICE/ directory:
(NOTE: The file is a TEXT file, just change the file extension from SVG to TXT)


Any help with this is greatly appreciated, Thanks!!

---

### Post by fahd on 2012-05-25
Thank you all.

Fahd

---

### Post by howefield on 2012-05-25
Thread moved to the "*Wine*" forum.

---

### Post by LewisTM on 2012-05-25
Install PlayOnLinux and launch it.
Click the Install button and find Office 2003 or 2007.
PoL will guide your through and download the appropriate Wine version for it (there are dozens, many patched for games). It will then download any missing helper libraries and proceed with the installation, prompting you for a setup.exe
This works great. It downloaded 1.2-rc1 x86 for Office 2007 32 bit.
I subsequently set it to use my system Wine (1.4) and it still runs fine so I think the key is in the other details.

Cheers!

---

### Post by forrestcupp on 2012-05-27
> **LewisTM said:**
> Install PlayOnLinux and launch it.

I agree with this. Since 12.04, it's much easier to just use PlayOnLinux to install Office. It won't give you a desktop launcher to open Word and Excel from the Dash, and it won't let you associate filetypes, but I have a [HowTo right here](http://ubuntuforums.org/showthread.php?t=1940522) that tells you how you can do that manually.

---

