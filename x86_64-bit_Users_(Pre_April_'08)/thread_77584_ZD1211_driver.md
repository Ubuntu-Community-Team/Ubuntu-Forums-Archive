---
title: "ZD1211 driver"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by spoetnik on 2005-10-17
I am trying to use an USB WLAN stick on my iBook. It is supposed to work with a zd1211 driver. There is no package for this driver, so i have to compile this driver myself. Unfortunatly the compilation and installation seems to go wrong every time. Is the someone so kind to make a package for ppc from this driver?? That way i could you my iBook wireless like it should (Damn airport extreme and broadcom :( )

Thanks in advance, an mayby a suggestion to include this driver in the next ubuntu release??

here are the instructions.
[https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

I followed the above instructions.

Made the simlinks, but to my kernel 2.6.12

Do make, and get the following error;

[FONT="Lucida Console"]spoetnik@elmo:~/Desktop/zd1211$ sudo make
cat /home/spoetnik/Desktop/zd1211/src/zddevlist | awk -f /home/spoetnik/Desktop/zd1211/src/zddevlist.awk > /home/spoetnik/Desktop/zd1211/src/zddevlist.h
make: *** [/home/spoetnik/Desktop/zd1211/src/zddevlist.h] Error 1
[/FONT]

---

### Post by ghee22 on 2005-10-17
same problem here on intel x86 based comp.. i posted a topic but like this, no replies..  :(

---

### Post by spoetnik on 2005-10-18
Damn. I really hope someone could solve this problem, or even make this driver available in the Ubuntu distribution.

This chipset is widely used in some USB-wlan sticks, and would help a lot of Powerbook user with unsuported airport extreme.

---

### Post by ghee22 on 2005-10-18
[QUOTE=spoetnik]Damn. I really hope someone could solve this problem, or even make this driver available in the Ubuntu distribution.[/QUOTE]

maybe if we keep this topic new... someone will finally notice... did you check out their wiki page on it?
[https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

it's only for 5.04 (not working for 5.10 :???: ) but maybe it can help us toward a solution...

---

### Post by REBELinBLUE on 2005-10-18
I used that wiki entry to set mine up in 5.10. You need to install gcc-3.6 (could be 3.4 not sure off hand) and of course change the kernel version when creating the symlinks

---

### Post by spoetnik on 2005-10-18
I Installed the building-essentials, and changed the simmlinks to the good kernel. I wil try it witch gcc installed
I let you al know

---

### Post by ghee22 on 2005-10-18
[QUOTE=REBELinBLUE]I used that wiki entry to set mine up in 5.10[/QUOTE]

how about we create a wiki for the same page for 5.10?

---

### Post by spoetnik on 2005-10-18
Got my old nast CAT 5 cable running down the stairs to my nifty G4 iBook, just to have a netwerk connection. This way i hope to install the driver for my WLAN.

To bad...

spoetnik@elmo:~/WLAN driver/zd1211$ sudo make
Makefile:100: warning: overriding commands for target `/home/spoetnik/WLAN'
Makefile:97: warning: ignoring old commands for target `/home/spoetnik/WLAN'
make: Circular /home/spoetnik/WLAN <- /home/spoetnik/WLAN dependency dropped.
make: *** No rule to make target `driver/zd1211/src/zddevlist', needed by `/home/spoetnik/WLAN'.  Stop.

Stupid me. I should rememeber NO SPACES IN DIRECTORY NAMES!!

But still....

spoetnik@elmo:~/zd1211$ sudo make clean
make -C /home/spoetnik/zd1211/src/modules-2.6.12 clean
make: *** /home/spoetnik/zd1211/src/modules-2.6.12: No such file or directory. Stop.
make: *** [clean] Error 2

spoetnik@elmo:~/zd1211$ sudo make
mkdir -p /home/spoetnik/zd1211/src/modules-2.6.12
(cd /home/spoetnik/zd1211/src/modules-2.6.12; \
  ln -sf /home/spoetnik/zd1211/src/Makefile; \
  for i in /home/spoetnik/zd1211/src/*.c /home/spoetnik/zd1211/src/*.h; \
  do \
  ln -sf ${i}; \
  done; \
)
make V=0 -C /usr/src/linux SUBDIRS=/home/spoetnik/zd1211/src/modules-2.6.12 modules
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[2]: scripts/Makefile.build: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[1]: *** [_module_/home/spoetnik/zd1211/src/modules-2.6.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9'
make: *** [all] Error 2

spoetnik@elmo:~/zd1211$ sudo make install
make V=0 -C /usr/src/linux SUBDIRS=/home/spoetnik/zd1211/src/modules-2.6.12 modules
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[2]: scripts/Makefile.build: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[1]: *** [_module_/home/spoetnik/zd1211/src/modules-2.6.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9'
make: *** [all] Error 2


Please someone any suggestion??

---

### Post by spoetnik on 2005-10-18
[QUOTE=REBELinBLUE]I used that wiki entry to set mine up in 5.10. You need to install gcc-3.6 (could be 3.4 not sure off hand) and of course change the kernel version when creating the symlinks[/QUOTE]

Maybe you can send me the compiled module?? Are you using an G4 PPC to???

Thanks,

spoetnik

---

### Post by stefanborremans on 2005-10-19
Just try

$ sudo -H -s
# modprobe zd1211
# ifconfig <wlan adapter name> up
# iwconfig

Now you should see wirless extensions for your wlan adapter.

---

### Post by spoetnik on 2005-10-19
"No wireless extensions"

this is what i expected, an can't get the drivers installed. Thats the problem!

---

### Post by ghee22 on 2005-10-19
[QUOTE=REBELinBLUE]You need to install gcc-3.6 (could be 3.4 not sure off hand)[/QUOTE]

it is gcc-3.4, your suspicion was valid.  problem is, gcc-3.4 is not on cd and also, this is my only way of connecting to the internet through this laptop.  :(

---

### Post by ghee22 on 2005-10-19
[QUOTE=spoetnik]Maybe you can send me the compiled module?? Are you using an G4 PPC to???

Thanks,

spoetnik[/QUOTE]
if they send u the compiled module and it works, i have an excellent idea.

create a wiki (with attachments) of compiled modules!
please let me know if/when it works

---

### Post by spoetnik on 2005-10-20
It would be better if someone could and would compile an installable package for this driver...

---

### Post by ghee22 on 2005-10-21
[QUOTE=spoetnik]It would be better if someone could and would compile an installable package for this driver...[/QUOTE]

ubuntu support, we're crying out loud for help! :(

---

### Post by spoetnik on 2005-10-26
^^kick^^

please someone help. My girlfriend starts to hate me because i have to leave her everey evening and go upstairs to "old school" connect my ibook to an outdated wire.....

---

### Post by ghee22 on 2005-10-28
^bump^

trying to install ubuntu 5.04 (which worked with zd1211 instructions) and using apt-get dist-upgrade tonight.

will update this forum.

---

### Post by ghee22 on 2005-10-30
[QUOTE=ghee22]^bump^

trying to install ubuntu 5.04 (which worked with zd1211 instructions) and using apt-get dist-upgrade tonight.

will update this forum.[/QUOTE]
^^BUMP^^&

It works!  I installed 5.04, installed the ZD1211 using the ubuntu wiki. i then added this command:
```
alias wlan0 zd1211
```
in /etc/modules
so that i modprobe would survive a reboot

internet works on 5.04, so i downloaded and burned a copy of 5.10.  put the cd in and used the upgrade all packages option.  incurred some package errors but it was all good because after a reboot (don't forget to remove the 5.10 cd) , i still had my wireless usb card working!!!

tell me how this works out for y'all.

---

### Post by spoetnik on 2005-10-31
I took the same hardy road. To bad that this seems the only easy way to get a zd1211 device to work..

---

### Post by dom on 2005-10-31
i just got this device working, with WPA. [ [http://ubuntuforums.org/showthread.php?p=458488](http://ubuntuforums.org/showthread.php?p=458488) ]

any tips for having it automatically set up after a boot ?


for anybody who wants it, i have no problem sending or uploading (to where ?) my compiled drivers and the wpa_supplicant file.
-I compiled the zd1211 driver on Hoary. {worked with wep, no wpa}
-I upgraded to Breezy.
-wpa_supplicant still didn't work so I build that on Breezy with zydas support.


thks

dom

---

### Post by six6 on 2005-11-01
Help please! 

I recently bought an IOGEAR GWU523 (which has the zd1211 chipset) to use with my iBook and Ubuntu. When plugged in the device seems connected according to dmesg:
```
Nov  1 18:55:29 localhost kernel: zd1211 - version 5000
Nov  1 18:55:29 localhost kernel: Release Ver = 4802
Nov  1 18:55:29 localhost kernel: EEPORM Ver = 4330
```

and lsmod lists zd1211, but 'sudo ifup wlan0' or similar command doesn't work (it says "Ignoring unknown interface wlan0=wlan0."). Also, lsusb freezes when run and boot will hang at the hotplug stage with the IOGEAR usb stick inserted.

I've tried the stock zd1211 (module bundled with the kernel) and from the sf.net site. What could still be the issue? Why isn't the interface detected?

Lastly, I have identical results testing this under an i386 Breezy install. :(

---

### Post by spoetnik on 2005-11-03
I got to compile and install the driver, but i get the exact same error message as above. Is this a problem with the driver?

---

### Post by six6 on 2005-11-06
I tried purchasing a different usb wireless adapter in case the IOGEAR usb stick was bad. I bought a Hawking HWU54G usb adapter (same zd1211 chipset) and tried the steps for connection. No luck :(. I still receive the same dmesg output but never see an interface.

Though on an i386 Breezy install the interface did show up for a little while (maybe 5 min), and I was able to scan for networks with NetworkManager (v0.5.1). So there is hope! From the sounds of it we're not alone finding that the adapter isn't working well, there are some [gentoo](http://forums.gentoo.org/viewtopic-t-318537.html) users experiencing similar issues.

---

### Post by six6 on 2005-11-12
**Problem solved for me!** :)

I used a vanilla 2.6.14.2 kernel from kernel.org, made it with 'make-kpkg --initrd kernel_image' and built the zd1211 module from the zd1211-driver-r38 svn tarball. Works like a charm!

dmesg output:
```

 _____     ____    _    ____
|__  /   _|  _ \  / \  / ___|
  / / | | | | | |/ _ \ \___ \
 / /| |_| | |_| / ___ \ ___) |
/____\__, |____/_/   \_\____/
     |___/
zd1211 - version 2.0.0.0
Release Ver = 4330
EEPORM Ver = 4330
PA type: 0
AllowedChannel = 000107ff
Region:16
usbcore: registered new driver zd1211
```

And so far NetworkManager (version currently in universe) works with the chipset, though it thinks it's a wired connection. I'm building NM 0.5.1 to see if things work better with a newer NM version; as of yet I can't associate to a specific wireless network or use WEP/WPA.

---

### Post by Audiophiliac on 2006-04-04
I have Ubuntu 5.04. Linux header can't be found and installed. Make clean ang make install don't work. No such command it says. Cd zd1211 didn't work. No such folder. How come it wroks for you guys boohoohoo.

---

### Post by dom on 2006-07-14
> **Audiophiliac said:**
> I have Ubuntu 5.04. Linux header can't be found and installed. Make clean ang make install don't work. No such command it says. Cd zd1211 didn't work. No such folder. How come it wroks for you guys boohoohoo.

you need to install a few thing before you build the zydas driver and wpa-supplicant for it, such as the kernel headers and the openssl headers. 

look to :

[http://ubuntuforums.org/showthread.php?t=195259&highlight=zydas](http://ubuntuforums.org/showthread.php?t=195259&highlight=zydas)

which has compiled most of the information needed for this from the various threads, and improved a few things.

the pre-up and post-down entries in the interfaces file is definitely a lot simpler than writing one's own init script !!

---

### Post by JeBeKe on 2006-08-31
Everything works like a charm on Ubuntu 6.06. There is one problem.

When starting up my machine, the device gives a read problem, hence the
device is not detected. It's even not shown in lsusb.
After unplugging/plugging everything goes smootly.

Any idea why the device is not detected during startup?

JBK

---

### Post by dom on 2006-09-19
i would look at /etc/modules to make sure you did this step right :
[COLOR="Sienna"]
5.4.1.5. Add to modprobe config in order for wireless config to survive reboot

    *   echo zd1211 >> /etc/modules[/COLOR]

after that, i'd be looking at trying the device on another machine, even with another os, if possible, to make sure it's not the dongle thats fupped.

if that's ok, perhaps try another usb hub (substitute usb card, or add one if onboard usb in use for e.g.)

there may be other software things to check, i'm sure others can help there, and if any of the above means buying hardware, then a complete re-try of the install might be preferrable first !

---

### Post by pizpot on 2007-04-14
did you notice the zd1211 thing that you can install with Synaptic?

---

