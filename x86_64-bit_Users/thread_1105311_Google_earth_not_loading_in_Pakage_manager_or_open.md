---
title: "Google earth not loading in Pakage manager or opening in BIN"
date: 2009-03-24
forum: x86 64-bit Users
---

### Post by Tony_photoplus on 2009-03-24
I am struggling to get things going with this new 64 bit machine.  I am trying to load Google earth and tried with the package manager, no success.  It told m edit was loaded and I couldn't find it anywhere. I downloaded from the Debs package website and made it executive as I think I was suppose to.  Not sure how to get it open though but I am hoping you might help here.  

I Have given up on Wine and Adobe7 I was hoping for some good luck here.

Thanks

Tony

---

### Post by oldos2er on 2009-03-24
If you downloaded a *.deb file, just double-click on it to install.

 To install the *.bin file, enter these commands one at a time in a terminal (assuming GoogleEarthLinux.bin is on your desktop):
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```
 This will install GoogleEarth to /opt/google-earth . Exit the installer before running the program.

---

### Post by Tony_photoplus on 2009-03-25
Thanks for that it did start loading then it couldn't load properly. 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

It loaded in the menu and when opened it stated this...
Could not create directory:

/root/.googleearth/Cache

Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:
My Places Path: "/home/tony/.googleearth"
Cache Path: "/home/tony/.googleearth/Cache"

I had the feeling that it would do this as it didn't load properly in the first place.  

Looking forward to the correction of this if there is one?

Thanks

Tony

---

### Post by dcstar on 2009-03-25
[https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package](https://help.ubuntu.com/community/GoogleEarth#make-googleearth-package)

Do you have the ia32-libs package installed?

---

### Post by oldos2er on 2009-03-25
Try running these commands one at a time:
```
sudo mv libcrypto.so.0.9.8  libcrypto.so.0.9.8.old
sudo ln -s /usr/lib/libcrypto.so libcrypto.so.0.9.8
```
 Let me know if this works.

---

### Post by Slim Odds on 2009-03-25
> **oldos2er said:**
> Try running these commands one at a time:
```
sudo mv libcrypto.so.0.9.8  libcrypto.so.0.9.8.old
sudo ln -s /usr/lib/libcrypto.so libcrypto.so.0.9.8
``` Let me know if this works.

This will definitely not work on the x86_64 version of Ubuntu.

The google version of  libcrypto.so.0.9.8 is 32 bit and the one in /usr/lib is 64 bit

I've recently built an Ubuntu 64 bit machine and installed google earth 5. Had no issues. It works fine.

That issue is only for the 32 bit Ubuntu.

---

### Post by Reeman on 2009-03-26
> **Slim Odds said:**
> This will definitely not work on the x86_64 version of Ubuntu.

The google version of  libcrypto.so.0.9.8 is 32 bit and the one in /usr/lib is 64 bit

I've recently built an Ubuntu 64 bit machine and installed google earth 5. Had no issues. It works fine.

That issue is only for the 32 bit Ubuntu.
I have GoogleEarth5 working just fine with 86_64. Found it easier to just install wine to get all the lib32 stuff necessary. You do need to use the system 32 crypto libs instead of the directory library calls that GoogleEarth libcrypto.so.0.9.8 uses. 

However if the packaged library that GoogleEarth install is not available it will search the tree for what system crypto uses for a 32 bit communication app and use what the system has. Unfortunately unless you have an internet active 32bit subsystem installed GoogleEarth will choke on the 64 bit cryptography calls!

Do this by just renaming libcrypto in /opt/googleearth. The reason is that the ssl libs in a 64bit Ubuntu install default to use only 64bit encryption calls.  

The install error that you are showing tells me that you are missing the standard 32 bit crypto...when you install wine, wine must do 32 bit ssl thus the 32bit system crypto libs are made visible in the directory tree by default.

Complicated and annoying situation.

---

### Post by Slim Odds on 2009-03-26
> **Reeman said:**
> I have GoogleEarth5 working just fine with 86_64. Found it easier to just install wine to get all the lib32 stuff necessary. You do need to use the system 32 crypto libs instead of the directory library calls that GoogleEarth libcrypto.so.0.9.8 uses. 

However if the packaged library that GoogleEarth install is not available it will search the tree for what system crypto uses for a 32 bit communication app and use what the system has. Unfortunately unless you have an internet active 32bit subsystem installed GoogleEarth will choke on the 64 bit cryptography calls!

Do this by just renaming libcrypto in /opt/googleearth. The reason is that the ssl libs in a 64bit Ubuntu install default to use only 64bit encryption calls.  

The install error that you are showing tells me that you are missing the standard 32 bit crypto...when you install wine, wine must do 32 bit ssl thus the 32bit system crypto libs are made visible in the directory tree by default.

You don't need WINE for Google Earth 5. Just download the linux version and install. Worked fine for me.

---

### Post by Tony_photoplus on 2009-03-28
Thanks guys for your help here, sorry haven't been replying as I have been to bad to do much.  I have a restriction on bandwidth as it the package I can afford.  I use my bandwidth up within 2 weeks and then evrything to do with Linux comes to a stop.  Why that is I don't know, yet when I am on Windows things are slow but still functional, but not Linux.  Can't fathom that one out??  But in on the 5th April I can start downloading again and resolving problems.  IN fact the slowness of the bandwidth cause a lot problems rather than resolves them.  So will let you know if resolved later


Thanks

Tony

---

