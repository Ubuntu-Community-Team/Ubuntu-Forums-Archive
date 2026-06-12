---
title: "Wine and USB 2.0 Support"
date: 2008-02-14
forum: Wine
---

### Post by brokencrystal on 2008-02-14
Does anyone know if the team is working on a version of wine with USB support?  I would like to get my Microsoft Zune to work under Linux.  If I could get the Zune software installed under Wine and have access to my USB 2.0 ports, this just might work...  If they are not currently working on this...  Can I put in a request and where?

---

### Post by BlackSwordD2 on 2008-06-20
here instructions of how to vote for apps in Wine

[http://appdb.winehq.org/help/?sTopic=voting](http://appdb.winehq.org/help/?sTopic=voting)

---

### Post by Faud on 2008-06-20
If you look at their newsletter usb support is one of the things that they are looking at working on.

---

### Post by Gina on 2009-03-02
Any advamce on this?  Does anyone know?  A link would be helpful - a search on USB seems to turn up pretty much everything but connecting to USB devices in Wine!

---

### Post by Hugh Mulqueen on 2009-12-30
any update on this? Apearently its possible with the patches there by Alexander Morozov applied; In the following website:

[http://wiki.winehq.org/USB]("http://wiki.winehq.org/USB")

Anybody give it a go? I'd imagine if you have to go into the wine registry and fix and apply patches it would be fairly difficult.

---

### Post by -Ender on 2009-12-30
I tried about a month ago, but unfortunately I couldn't get the patches to work.

---

### Post by HeadHunter00 on 2010-01-10
> **Hugh Mulqueen said:**
> any update on this? Apearently its possible with the patches there by Alexander Morozov applied; In the following website:

[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

Anybody give it a go? I'd imagine if you have to go into the wine registry and fix and apply patches it would be fairly difficult.
Wonderful job. It works.

---

### Post by -Ender on 2010-01-11
Was there anything special that you had to do to get it to work, or did you just follow those instructions verbatim?

Edit:
I saw that he modified the text files that need to be applied, but I can't download them as they don't seem to be up anymore. So, could you upload the copies of these two files since I can't access them:
[ftp://ftp.etersoft.ru/pub/people/amorozov/0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt](ftp://ftp.etersoft.ru/pub/people/amorozov/0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt)
[ftp://ftp.etersoft.ru/pub/people/amorozov/0002-Re-generate-some-files.txt](ftp://ftp.etersoft.ru/pub/people/amorozov/0002-Re-generate-some-files.txt)

---

### Post by futaris on 2010-03-16
```
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git

sudo apt-get build-dep wine
**sudo apt-get install libusb-1.0-0-dev**

git branch usb-1.1.28 wine-1.1.28
git checkout usb-1.1.28
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.1.28/0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.1.28/0002-Re-generate-some-files.txt
git am 0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt 0002-Re-generate-some-files.txt
**./tools/make_makefiles**
./configure
make depend
make
make install
```

That should work.

---

### Post by nuffy on 2010-03-21
Hi futaris,

I started to implement your instructions....everything was going fine until I entered 'git branch usb-1.1.28 wine-1.1.28' where I got this error message 'fatal: Not a git repository (or any of the parent directories): .git'

Where has it gone wrong??

Thanx........nuffy

---

### Post by tippitoes on 2010-03-28
Hi nuffy,

I also followed futaris' instructions and had the same error message, but was able to proceed if I typed:

cd ~/wine-git

However, I got right through to the last command no problem, but for "make install" it spits out a whole page of stuff.  One part being:

make [2]: Nothing to be done for 'all'.

And the last line being:

make: *** [dlls/_install_] Error 2

Any help from anyone would be greatly appreciated!

---

### Post by muncy on 2010-04-05
I got the same error as tippitoes when I put in the last line BUT when I put a usb device in now I get a D drive in wine. Open this and I can read what is on the device.

In other words. It works!

---

### Post by joeoshawa on 2010-04-24
First off I have noticed that alot of people cannot get samsungs pc studio working in wine. I have it working it says pc studio 3 everything seems to work however i cannot connect to the phone due to you guessed it no usb support in wine. i tried the above all all went well till make  this is the error i get 
make[2]: Entering directory `/home/joe/wine-git/dlls/usbhub.sys'
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o usbhub.o usbhub.c
usbhub.c:26:20: error: libusb.h: No such file or directory
usbhub.c:74: error: expected specifier-qualifier-list before ‘libusb_device’
usbhub.c: In function ‘usbhub_ioctl’:
usbhub.c:139: error: ‘uint8_t’ undeclared (first use in this function)
usbhub.c:139: error: (Each undeclared identifier is reported only once
usbhub.c:139: error: for each function it appears in.)
usbhub.c:139: error: expected ‘;’ before ‘bus_number’
usbhub.c:158: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:158: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:158: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:159: warning: implicit declaration of function ‘libusb_get_bus_number’
usbhub.c:159: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:159: error: ‘bus_number’ undeclared (first use in this function)
usbhub.c:162: error: storage size of ‘desc’ isn’t known
usbhub.c:164: warning: implicit declaration of function ‘libusb_get_device_descriptor’
usbhub.c:164: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:162: warning: unused variable ‘desc’
usbhub.c:196: error: expected ‘;’ before ‘bus_number’
usbhub.c:210: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:210: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:210: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:211: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘usbhub_internal_ioctl’:
usbhub.c:327: error: ‘libusb_device_handle’ undeclared (first use in this function)
usbhub.c:327: error: ‘husb’ undeclared (first use in this function)
usbhub.c:331: warning: implicit declaration of function ‘libusb_open’
usbhub.c:331: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:338: warning: implicit declaration of function ‘libusb_set_configuration’
usbhub.c:344: warning: implicit declaration of function ‘libusb_get_active_config_descriptor’
usbhub.c:344: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:354: error: dereferencing pointer to incomplete type
usbhub.c:355: error: dereferencing pointer to incomplete type
usbhub.c:356: error: dereferencing pointer to incomplete type
usbhub.c:357: error: dereferencing pointer to incomplete type
usbhub.c:359: error: dereferencing pointer to incomplete type
usbhub.c:363: error: dereferencing pointer to incomplete type
usbhub.c:365: error: dereferencing pointer to incomplete type
usbhub.c:367: error: dereferencing pointer to incomplete type
usbhub.c:369: error: dereferencing pointer to incomplete type
usbhub.c:371: error: dereferencing pointer to incomplete type
usbhub.c:372: error: dereferencing pointer to incomplete type
usbhub.c:377: warning: implicit declaration of function ‘libusb_free_config_descriptor’
usbhub.c:380: warning: implicit declaration of function ‘libusb_close’
usbhub.c:392: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:396: warning: implicit declaration of function ‘libusb_claim_interface’
usbhub.c:400: warning: implicit declaration of function ‘libusb_set_interface_alt_setting’
usbhub.c:403: warning: implicit declaration of function ‘libusb_release_interface’
usbhub.c:422: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:431: warning: implicit declaration of function ‘libusb_bulk_transfer’
usbhub.c:473: error: storage size of ‘desc’ isn’t known
usbhub.c:475: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:473: warning: unused variable ‘desc’
usbhub.c:492: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:496: error: dereferencing pointer to incomplete type
usbhub.c:497: error: dereferencing pointer to incomplete type
usbhub.c:497: error: dereferencing pointer to incomplete type
usbhub.c:498: error: dereferencing pointer to incomplete type
usbhub.c:500: error: dereferencing pointer to incomplete type
usbhub.c:504: error: dereferencing pointer to incomplete type
usbhub.c:505: error: dereferencing pointer to incomplete type
usbhub.c:505: error: dereferencing pointer to incomplete type
usbhub.c:506: error: dereferencing pointer to incomplete type
usbhub.c:508: error: dereferencing pointer to incomplete type
usbhub.c:512: error: dereferencing pointer to incomplete type
usbhub.c:513: error: dereferencing pointer to incomplete type
usbhub.c:514: error: dereferencing pointer to incomplete type
usbhub.c:525: warning: ISO C90 forbids mixed declarations and code
usbhub.c:527: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:529: warning: implicit declaration of function ‘libusb_get_string_descriptor’
usbhub.c:545: warning: ISO C90 forbids mixed declarations and code
usbhub.c:556: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:558: warning: implicit declaration of function ‘libusb_control_transfer’
usbhub.c:559: error: ‘LIBUSB_REQUEST_GET_STATUS’ undeclared (first use in this function)
usbhub.c:575: warning: ISO C90 forbids mixed declarations and code
usbhub.c:589: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘create_root_hub_device’:
usbhub.c:1226: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘enum_reg_usb_devices’:
usbhub.c:1316: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘register_usb_device’:
usbhub.c:1406: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘start_device_drivers’:
usbhub.c:1442: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘enum_usb_devices’:
usbhub.c:1464: error: ‘libusb_device’ undeclared (first use in this function)
usbhub.c:1464: error: ‘devs’ undeclared (first use in this function)
usbhub.c:1464: error: ‘dev’ undeclared (first use in this function)
usbhub.c:1464: warning: left-hand operand of comma expression has no effect
usbhub.c:1465: error: storage size of ‘desc’ isn’t known
usbhub.c:1465: warning: ISO C90 forbids mixed declarations and code
usbhub.c:1483: warning: implicit declaration of function ‘libusb_init’
usbhub.c:1488: warning: implicit declaration of function ‘libusb_get_device_list’
usbhub.c:1490: warning: implicit declaration of function ‘libusb_exit’
usbhub.c:1500: warning: implicit declaration of function ‘libusb_ref_device’
usbhub.c:1501: warning: implicit declaration of function ‘libusb_get_device_address’
usbhub.c:1509: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:1512: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:1520: warning: implicit declaration of function ‘libusb_free_device_list’
usbhub.c:1465: warning: unused variable ‘desc’
make[2]: *** [usbhub.o] Error 1
make[2]: Leaving directory `/home/joe/wine-git/dlls/usbhub.sys'
make[1]: *** [usbhub.sys] Error 2
make[1]: Leaving directory `/home/joe/wine-git/dlls'
make: *** [dlls] Error 2

now i had a look around and i noticed the first error libusb.h someone mentioned that it is usb.h is the file it is looking for. I am still a newbie so sorry for any newbie errors i have made but could someone please help me out here i was exstaic to learn the program works when you make sure you download the one for xp it would be perfect if i could get usb support working in wine and delete winblows altogether this is the only thing stopping me. I still cannot get the sph-m540 working in linux but if the t456 works i can just transfer the memory card. thanks in advance.

---

### Post by joeoshawa on 2010-04-25
I really need this to work does anyone have any ideas please.

---

### Post by joeoshawa on 2010-05-02
Upgrade to ubuntu 10.4 haven't checked if wine works but when i plug the phone in it automatically connects and downloads all the pics. Seems 10.4 comes with a program that does it.  Great job btw. Now if i could only get someone to respond to my postings life would be grand.  At least a read your crappy posting you suck would be a responce.

---

### Post by muncy on 2010-05-02
Glad you got it sorted. I know it is frustrating when nobody replies to your post but I didn't want to get your hopes up by seeing that you had a reply then finding it just said 'Sorry - no idea'

---

### Post by snnicky on 2010-06-22
I tried update the patches made by Alexander Morozov for wine 1.1.28 to be applicable to wine 1.2 rc4. That compiles for me. Please try the patch [http://snnicky.com/wine-1.2-rc4/0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt](http://snnicky.com/wine-1.2-rc4/0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt). I combined 2 Alexander's patches into one.

---

### Post by Declan Moriarty on 2010-07-06
I have Just installed Wine version 1.1.42 Beta on Ubuntu 10.04 and USB 2.0  works.  I put a USB Stick in and it was assigned the G: drive and Notepad was able to access the files.  I haven't done any patches to Wine.

---

### Post by loveice on 2010-07-28
> **joeoshawa said:**
> First off I have noticed that alot of people cannot get samsungs pc studio working in wine. I have it working it says pc studio 3 everything seems to work however i cannot connect to the phone due to you guessed it no usb support in wine. i tried the above all all went well till make  this is the error i get 
make[2]: Entering directory `/home/joe/wine-git/dlls/usbhub.sys'
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o usbhub.o usbhub.c
usbhub.c:26:20: error: libusb.h: No such file or directory
usbhub.c:74: error: expected specifier-qualifier-list before ‘libusb_device’
usbhub.c: In function ‘usbhub_ioctl’:
usbhub.c:139: error: ‘uint8_t’ undeclared (first use in this function)
usbhub.c:139: error: (Each undeclared identifier is reported only once
usbhub.c:139: error: for each function it appears in.)
usbhub.c:139: error: expected ‘;’ before ‘bus_number’
usbhub.c:158: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:158: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:158: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:159: warning: implicit declaration of function ‘libusb_get_bus_number’
usbhub.c:159: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:159: error: ‘bus_number’ undeclared (first use in this function)
usbhub.c:162: error: storage size of ‘desc’ isn’t known
usbhub.c:164: warning: implicit declaration of function ‘libusb_get_device_descriptor’
usbhub.c:164: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:162: warning: unused variable ‘desc’
usbhub.c:196: error: expected ‘;’ before ‘bus_number’
usbhub.c:210: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:210: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:210: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:211: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘usbhub_internal_ioctl’:
usbhub.c:327: error: ‘libusb_device_handle’ undeclared (first use in this function)
usbhub.c:327: error: ‘husb’ undeclared (first use in this function)
usbhub.c:331: warning: implicit declaration of function ‘libusb_open’
usbhub.c:331: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:338: warning: implicit declaration of function ‘libusb_set_configuration’
usbhub.c:344: warning: implicit declaration of function ‘libusb_get_active_config_descriptor’
usbhub.c:344: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:354: error: dereferencing pointer to incomplete type
usbhub.c:355: error: dereferencing pointer to incomplete type
usbhub.c:356: error: dereferencing pointer to incomplete type
usbhub.c:357: error: dereferencing pointer to incomplete type
usbhub.c:359: error: dereferencing pointer to incomplete type
usbhub.c:363: error: dereferencing pointer to incomplete type
usbhub.c:365: error: dereferencing pointer to incomplete type
usbhub.c:367: error: dereferencing pointer to incomplete type
usbhub.c:369: error: dereferencing pointer to incomplete type
usbhub.c:371: error: dereferencing pointer to incomplete type
usbhub.c:372: error: dereferencing pointer to incomplete type
usbhub.c:377: warning: implicit declaration of function ‘libusb_free_config_descriptor’
usbhub.c:380: warning: implicit declaration of function ‘libusb_close’
usbhub.c:392: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:396: warning: implicit declaration of function ‘libusb_claim_interface’
usbhub.c:400: warning: implicit declaration of function ‘libusb_set_interface_alt_setting’
usbhub.c:403: warning: implicit declaration of function ‘libusb_release_interface’
usbhub.c:422: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:431: warning: implicit declaration of function ‘libusb_bulk_transfer’
usbhub.c:473: error: storage size of ‘desc’ isn’t known
usbhub.c:475: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:473: warning: unused variable ‘desc’
usbhub.c:492: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:496: error: dereferencing pointer to incomplete type
usbhub.c:497: error: dereferencing pointer to incomplete type
usbhub.c:497: error: dereferencing pointer to incomplete type
usbhub.c:498: error: dereferencing pointer to incomplete type
usbhub.c:500: error: dereferencing pointer to incomplete type
usbhub.c:504: error: dereferencing pointer to incomplete type
usbhub.c:505: error: dereferencing pointer to incomplete type
usbhub.c:505: error: dereferencing pointer to incomplete type
usbhub.c:506: error: dereferencing pointer to incomplete type
usbhub.c:508: error: dereferencing pointer to incomplete type
usbhub.c:512: error: dereferencing pointer to incomplete type
usbhub.c:513: error: dereferencing pointer to incomplete type
usbhub.c:514: error: dereferencing pointer to incomplete type
usbhub.c:525: warning: ISO C90 forbids mixed declarations and code
usbhub.c:527: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:529: warning: implicit declaration of function ‘libusb_get_string_descriptor’
usbhub.c:545: warning: ISO C90 forbids mixed declarations and code
usbhub.c:556: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:558: warning: implicit declaration of function ‘libusb_control_transfer’
usbhub.c:559: error: ‘LIBUSB_REQUEST_GET_STATUS’ undeclared (first use in this function)
usbhub.c:575: warning: ISO C90 forbids mixed declarations and code
usbhub.c:589: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘create_root_hub_device’:
usbhub.c:1226: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘enum_reg_usb_devices’:
usbhub.c:1316: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘register_usb_device’:
usbhub.c:1406: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘start_device_drivers’:
usbhub.c:1442: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c: In function ‘enum_usb_devices’:
usbhub.c:1464: error: ‘libusb_device’ undeclared (first use in this function)
usbhub.c:1464: error: ‘devs’ undeclared (first use in this function)
usbhub.c:1464: error: ‘dev’ undeclared (first use in this function)
usbhub.c:1464: warning: left-hand operand of comma expression has no effect
usbhub.c:1465: error: storage size of ‘desc’ isn’t known
usbhub.c:1465: warning: ISO C90 forbids mixed declarations and code
usbhub.c:1483: warning: implicit declaration of function ‘libusb_init’
usbhub.c:1488: warning: implicit declaration of function ‘libusb_get_device_list’
usbhub.c:1490: warning: implicit declaration of function ‘libusb_exit’
usbhub.c:1500: warning: implicit declaration of function ‘libusb_ref_device’
usbhub.c:1501: warning: implicit declaration of function ‘libusb_get_device_address’
usbhub.c:1509: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:1512: error: ‘struct DeviceInstance’ has no member named ‘dev’
usbhub.c:1520: warning: implicit declaration of function ‘libusb_free_device_list’
usbhub.c:1465: warning: unused variable ‘desc’
make[2]: *** [usbhub.o] Error 1
make[2]: Leaving directory `/home/joe/wine-git/dlls/usbhub.sys'
make[1]: *** [usbhub.sys] Error 2
make[1]: Leaving directory `/home/joe/wine-git/dlls'
make: *** [dlls] Error 2

now i had a look around and i noticed the first error libusb.h someone mentioned that it is usb.h is the file it is looking for. I am still a newbie so sorry for any newbie errors i have made but could someone please help me out here i was exstaic to learn the program works when you make sure you download the one for xp it would be perfect if i could get usb support working in wine and delete winblows altogether this is the only thing stopping me. I still cannot get the sph-m540 working in linux but if the t456 works i can just transfer the memory card. thanks in advance.


diff --git a/dlls/usbhub.sys/usbhub.c b/dlls/usbhub.sys/usbhub.c
index 8568b9c..3454473 100644
--- a/dlls/usbhub.sys/usbhub.c
+++ b/dlls/usbhub.sys/usbhub.c
@@ -22,6 +22,7 @@
 #include <stdio.h>
 #include <stdlib.h>
 
+#undef HAVE_LIBUSB_H
 #ifdef HAVE_LIBUSB_H
 #include <libusb.h>
 #elif defined(HAVE_USB_H)

---

### Post by MrVas on 2010-11-07
Thank you all for the hints to get me where I needed to get (Wine with USB support). The notes below are based on building Wine on a virtual 32-bit Ubuntu 9.10 (Karmic Koala) system running in a VirtualBox session on 64-bit Ubuntu 10.04 (Lucid Lynx).

```
cd ~
mkdir wine-git
cd wine-git

sudo apt-get build-dep wine

git clone git://source.winehq.org/git/wine.git .
git checkout wine-1.3.3
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.3.3/*.txt
git am *.txt
```
You may have noticed that I skipped installing Ubuntu's libusb-1.0.0-dev package. I did this on purpose, since that package is old and does not work with Wine/USB patches provided by Alexander Morozov. Download the latest libusb package and build it from scratch:```
mkdir ~/libusb
cd ~/libusb  
wget http://sourceforge.net/projects/libusb/files/libusb-1.0/libusb-1.0.8/libusb-1.0.8.tar.bz2/download
tar jxvf libusb-1.0.8.tar.bz2
cd libusb-1.0.8
./configure
./make
sudo ./make install
```
Create symbolic links for newly installed libusb:
```
sudo ln -s /usr/local/lib/libusb-1* /lib
```
Now you should be able to start building the Makefile for Wine:
```
cd ~/wine-git
./tools/make_makefiles
./configure
```
Verify that libusb is being used:
```
grep libusb config.log
```
..and now build Wine.
```
make depend && make
```
Enjoy!!!

Vas

PS. Here are other links that helped me:

[http://forum.winehq.org/viewtopic.php?t=9663&view=previous](http://forum.winehq.org/viewtopic.php?t=9663&view=previous)
[http://forum.winehq.org/viewtopic.php?t=9463](http://forum.winehq.org/viewtopic.php?t=9463)
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

---

### Post by sysghost on 2010-11-07
> **MrVas said:**
> Thank you all for the hints to get me where I needed to get (Wine with USB support). The notes below are based on building Wine on a virtual 32-bit Ubuntu 9.10 (Karmic Koala) system running in a VirtualBox session on 64-bit Ubuntu 10.04 (Lucid Lynx).

```
cd ~
mkdir wine-git
cd wine-git

sudo apt-get build-dep wine

git clone git://source.winehq.org/git/wine.git .
git checkout wine-1.3.3
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.3.3/*.txt
git am *.txt
```
You may have noticed that I skipped installing Ubuntu's libusb-1.0.0-dev package. I did this on purpose, since that package is old and does not work with Wine/USB patches provided by Alexander Morozov. Download the latest libusb package and build it from scratch:```
mkdir ~/libusb
cd ~/libusb  
wget http://sourceforge.net/projects/libusb/files/libusb-1.0/libusb-1.0.8/libusb-1.0.8.tar.bz2/download
tar jxvf libusb-1.0.8.tar.bz2
cd libusb-1.0.8
./configure
./make
sudo ./make install
```
Create symbolic links for newly installed libusb:
```
sudo ln -s /usr/local/lib/libusb-1* /lib
```
Now you should be able to start building the Makefile for Wine:
```
cd ~/wine-git
./tools/make_makefiles
./configure
```
Verify that libusb is being used:
```
grep libusb config.log
```
..and now build Wine.
```
make depend && make
```
Enjoy!!!

Vas

PS. Here are other links that helped me:

[http://forum.winehq.org/viewtopic.php?t=9663&view=previous](http://forum.winehq.org/viewtopic.php?t=9663&view=previous)
[http://forum.winehq.org/viewtopic.php?t=9463](http://forum.winehq.org/viewtopic.php?t=9463)
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

A few minor corrections / spellings:
wget from sourceforge: remove the "/download" at the end. Else wget catches the wrong content.
"./make" should be "make"
libusb: no need to create symbolic links, they're already there.

Otherwise a nice guide. Thanks.

---

### Post by BushMissile on 2011-01-04
I hate to sound like a newbie but do I need to run a "make install" after MrVas's instructions?  Or does the "make depend && make" command cover that?

---

### Post by r2ramos on 2011-01-16
Followed the instructions and installed the patched wine via playonlinux according to [this]("http://www.playonlinux.com/en/topic-2273-Custom_wine_version_a_PlayonLinux.html"). POL recognizes the wine version (supposedly patched). Still dont know how to use usb; cant see the device im plugging with wine.

Any help?

---

### Post by philnice on 2011-01-18
I have compiled wine 1.3.10 with usb patches to use with my hercules mp3e2 console and still, i don't know how to check wether or not is working.
I beleive there are a few things to be done from this point, but for this we 'll need some help.
So, ubuntu gurus, bring the light to us..!

---

### Post by marin123 on 2011-01-21
ok, so i followed build instructions (a bit altered) and successfully built wine 1.3.11 with usb patches.

the problem is that every time i run program in wine i get error message that wine failed to load Usbhub.sys, but i have the right path in registry and a file in c drive. i want to try load windows' usbhub.sys but i have 64 bit windows and get error message that 64 bit app cannot be loaded.

now i'm waiting for a friend to send me proper files and then i will see what happens.

after i get usbhub working, i will need to work on driver location for mass storage.

cross your fingers guys :) and i hope someone will get inspired by this and make something ridiculous, like making this to work :D

---

### Post by philnice on 2011-01-21
marin123, good luck! :D i only know a few things, perhaps you need to load 32bit version of the sys. file you need first? just a thought. Also, any suggestion, on a way to check if my installation is work or not? hercules mp3e2 does give me some error report in the log file viewer, but nothing from wine.
Lastly, getting this to work isn't an easy task. Otherwise, there would be packages precompiled for every wine version available. Many guys around here had put a lot of effort on this, but with no luck.
It is up to wine developers to finally deal with amorozov's patches or whatever, and add usb support. I think they keep rescheduling this.

---

### Post by philnice on 2011-01-25
Well, all of you who seeking for usb support in wine, may want to read the release criteria for version 1.4, and smile...! :D
[http://wiki.winehq.org/WineReleaseCriteria](http://wiki.winehq.org/WineReleaseCriteria)

---

### Post by marin123 on 2011-01-26
> **philnice said:**
> Well, all of you who seeking for usb support in wine, may want to read the release criteria for version 1.4, and smile...! :D
[http://wiki.winehq.org/WineReleaseCriteria](http://wiki.winehq.org/WineReleaseCriteria)

i have already read that, but we will have to wait and see will it happen and will it work.

if it does, then:

```
sudo apt-get install wine1.4
sudo apt-get remove windows
```
:D

---

### Post by philnice on 2011-01-26
> marin123 wrote: 
"sudo apt-get install wine1.4
sudo apt-get remove windows" :lolflag:
Seriously, perhaps this could be the main reason for any delays in wine - usb support...

---

### Post by Evil Wayz on 2011-05-23
> 
```

git clone git://source.winehq.org/git/wine.git .
git checkout wine-1.3.3

```


When I get to here, this is what happens;

wolf@server:~/wine-git$ git clone git://source.winehq.org/git/wine.git .
Cloning into ....
source.winehq.org[0: 209.46.25.134]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
wolf@server:~/wine-git$ git clone git://source.winehq.org/git/wine.git 
Cloning into wine...
source.winehq.org[0: 209.46.25.134]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
wolf@server:~/wine-git$ git checkout wine-1.3.3
fatal: Not a git repository (or any of the parent directories): .git

---

### Post by philnice on 2011-05-23
> **Evil Wayz said:**
> When I get to here, this is what happens;

wolf@server:~/wine-git$ git clone git://source.winehq.org/git/wine.git .
Cloning into ....
source.winehq.org[0: 209.46.25.134]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
wolf@server:~/wine-git$ git clone git://source.winehq.org/git/wine.git 
Cloning into wine...
source.winehq.org[0: 209.46.25.134]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)
wolf@server:~/wine-git$ git checkout wine-1.3.3
fatal: Not a git repository (or any of the parent directories): .git

This is what you entered above: git clone git://source.winehq.org/git/wine.git .
And this is how it should be: git clone git://source.winehq.org/git/wine.git ~/wine-git

---

### Post by Chlewey on 2012-07-24
> **futaris said:**
> (...)```
**./tools/make_makefiles**
./configure
make depend
make
make install
```That should work.

I have followed these and MrVas instructions (changes made for using USB 1.5.7 instead of 1.1.28 or 1.3.3) on a Ubuntu 12.04 64 bit system however when I run the make commands it says that there are no rules to build 'depend' nor a 'makefile'.  I found a 'Makefile.in' but i?m not sure if it is enough to rename it.

---

### Post by Chlewey on 2012-07-24
Following an error message it seems my problem is that I have a 64 bit Ubuntu 12.04 system and wine should be compiled in 32 bits.

I followed instructions in [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) and built wine in a 32 bit chroot (applying the USB patches) and everything seemed to build okay.

I had to delete my .wine directory and reinstall my application.  It installed okay.

However the problem persists: the application cannot find the USB ports.

My application is Full Gauge's SITRAD Local application ( [http://www.sitrad.com/](http://www.sitrad.com/) ) connected to a Sitrad CONV32 RS485 to USB converter via a USB port.

It seems my better option right now is tu buy a MS Windows License.

---

### Post by Lyfang on 2012-07-24
> **Chlewey said:**
> Following an error message it seems my problem is that I have a 64 bit Ubuntu 12.04 system and wine should be compiled in 32 bits.

I followed instructions in [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) and built wine in a 32 bit chroot (applying the USB patches) and everything seemed to build okay.

I had to delete my .wine directory and reinstall my application.  It installed okay.

However the problem persists: the application cannot find the USB ports.

My application is Full Gauge's SITRAD Local application ( [http://www.sitrad.com/](http://www.sitrad.com/) ) connected to a Sitrad CONV32 RS485 to USB converter via a USB port.

It seems my better option right now is tu buy a MS Windows License.

Are you shure there are only Windows programs to connect your Microsoft Zune? Why you should support Linux:
> **Lyfang said:**
> Open Source often respects users freedom. How can this slow down development of software?
Or try Windows 8 Release Preview for free(?) from [http://windows.microsoft.com/en-US/windows-8/release-preview](http://windows.microsoft.com/en-US/windows-8/release-preview)

I suggest to install VirtualBox:
```
sudo apt-get install virtualbox
```
I also recommend installing VirtualBox Extension Pack & Guest Additions.

---

### Post by Chlewey on 2012-07-24
> **Lyfang said:**
> Are you shure there are only Windows programs to connect your Microsoft Zune? No Zune.  An industry propietary hardware for sensing enviromental variables in refrigeration and greenhouse industries.
> **Lyfang said:**
> Why you should support Linux:
I'd like Linux support however for several reasons including further development of the application.  However I did not design their software.  I have no access to source code and it seems that the vendor is not providing it.  Our solution is still too small for getting them interested in sharing source code with us, and in the mean time we need to have a pilot running in production mode.

Cost is not a big issue (a rather have a fully licensed Win7 than a test licensed Win8 system** if** I cannot get it running on a really free environment)

The problem is that it seems to be too many small issues, and patches and modules that need to be installed first that I'm not sure that it is worth the trouble (for now).

I will spend another half day trying to get it work on a 32-bit Ubuntu with an USB-patched Wine.

---

### Post by Lyfang on 2012-07-25
> **Chlewey said:**
> No Zune.  An industry propietary hardware for sensing enviromental variables in refrigeration and greenhouse industries.

I hope that my suggestions were helpful & not seen as giving you a hard time. I read an article: [Windows 8 to Remove Zune Support]("http://maketecheasier.com/windows-8-to-remove-zune-support/2012/02/27") To bad that USB support is still considered unfinished by the Wine developers, otherwise a Wine release with USB support could have made things much easier.

---

### Post by Lyfang on 2012-08-03
How experimental is the USB support implementation in Wine? Are the USB patches based on making Wine use the Windows API for USB support?

---

### Post by pluMmet on 2012-10-29
> **futaris said:**
> ```
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git

sudo apt-get build-dep wine
**sudo apt-get install libusb-1.0-0-dev**

git branch usb-1.1.28 wine-1.1.28
git checkout usb-1.1.28
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.1.28/0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.1.28/0002-Re-generate-some-files.txt
git am 0001-Add-support-of-native-Windows-drivers-for-USB-tokens.txt 0002-Re-generate-some-files.txt
**./tools/make_makefiles**
./configure
make depend
make
make install
```

That should work.

I'm still very noob... are these instructions still valid for v12.10?

---

### Post by pluMmet on 2012-10-29
I'm hoping these are current instructions?

```
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git

sudo apt-get build-dep wine

git checkout wine-1.4.1
wget ftp://ftp.etersoft.ru/pub/people/amorozov/usb/1.4.1/*.txt
git am *.txt

mkdir ~/libusb
cd ~/libusb  
wget http://sourceforge.net/projects/libusb/files/libusb-1.0/libusb-1.0.8/libusb-1.0.8.tar.bz2/download
tar jxvf libusb-1.0.8.tar.bz2 *(tar jxvf download)
cd libusb-1.0.8 
./configure
./make
sudo ./make install
sudo ln -s /usr/local/lib/libusb-1* /lib

cd ~/wine-git
./tools/make_makefiles
./configure

make depend && make
```

---

### Post by pluMmet on 2012-10-29
I've gotten to the end and neither 

```
make depend && make
```

or

```
make depend
make
make install
```

will work... Help!

---

### Post by pluMmet on 2012-10-29
This apperas to be the reason...

```
configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.

```

What to do?

---

### Post by pluMmet on 2012-10-29
```
sudo apt-get install ia32-libs
```

Still does not work :(

---

### Post by Lyfang on 2012-10-29
> **pluMmet said:**
> ```
sudo apt-get install ia32-libs
```

Still does not work :(
Brainstorming: build-essential, libc6-dev-i386 packages?

---

### Post by DieselSnorter on 2012-11-10
> **pluMmet said:**
> This apperas to be the reason...

```
configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.

```

What to do?

also what I get here.

---

### Post by mark bower on 2013-01-03
And just for the record in Wine 1.4.1, Uub 12.04LTS:  My jump drives and a USB device for the Dynam RC controller are recognized.  However, a USB device with cord which connects my Spektrum RC controller to USB is not recognized under Wine which prevents using a simulator program called "Aerofly Professional".  This program with the Spectrum controller and USB connector work just fine in XP.

---

