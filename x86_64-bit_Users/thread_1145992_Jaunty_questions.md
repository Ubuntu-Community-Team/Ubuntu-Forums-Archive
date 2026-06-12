---
title: "Jaunty questions"
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by Chriis on 2009-05-02
thanks to read me, :)

is it normal in jaunty that i got " FATAL: Module evdev not found. " with modprobe evdev ??

i try to install piece of hardware (nostromo n50 )
procedure is like :

[COLOR="Blue"]type:
sudo modprobe evdev (please make sure that your speed pad is not plugged in)
sudo chmod a+rw /dev/input/event1

unpack nostromo_Driver-0.1.3.tar.gz
cd into the directory

Next type:
sudo ./configure
sudo make
sudo make install[/COLOR]

it worked well on gutsy, but even if i try without " sudo modprobe evdev " , it doesnt work on Jaunty, 

the Deamon try to load, but end with :
"nostromo_daemon[7015]: segfault at 696ec9e0 ip 00007fbc6f59aba8 sp 00007fff7a609d20 error 4 in libpthread-2.9.so[7fbc6f593000+17000]" 



please help 

chriis

---

### Post by Chriis on 2009-05-02
bump!

---

### Post by kestrel1 on 2009-05-02
I don't expect the driver is compatible with Jaunty. Gutsy was a while ago now.

---

### Post by Chriis on 2009-05-07
wonder why it should'nt work on jaunty,

Any more help?

thanks

Chriis

---

### Post by Shriner on 2009-05-07
Try going to System, Applications, Hardware Drivers.......maybe it can be done through there.

---

### Post by jespdj on 2009-05-07
> **Chriis said:**
> wonder why it should'nt work on jaunty,
Because some drivers are written for certain versions of the Linux kernel, and every Ubuntu release has a different Linux kernel version. Maybe the driver that you are trying to install isn't made for the Linux kernel version that's used in Jaunty. Check if there's a newer version of that driver available somewhere.

---

### Post by Yellow Pasque on 2009-05-07
Please don't cross-post the same issue,
[http://ubuntuforums.org/showthread.php?t=1145580](http://ubuntuforums.org/showthread.php?t=1145580)

---

### Post by Chriis on 2009-05-07
> Please don't cross-post the same issue,
[http://ubuntuforums.org/showthread.php?t=1145580](http://ubuntuforums.org/showthread.php?t=1145580)

Sorry, but at first, i didn't know that this issue was "arch" dependant.

It's why I re-post in a more appropriate section of the forum.

Chriis

---

