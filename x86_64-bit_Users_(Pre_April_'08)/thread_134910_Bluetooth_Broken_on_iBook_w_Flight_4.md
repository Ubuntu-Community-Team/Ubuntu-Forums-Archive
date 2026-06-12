---
title: "Bluetooth Broken on iBook w/ Flight 4"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by spaceballl on 2006-02-22
Hey guys,

I filed this bug here...
[https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415](https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415)

Basically, my bluetooth mouse and keyboard no longer work w/ Flight 4. I reinstalled Flight 3 and they're back to working. is there anything i can do to help make sure this gets worked out before the first RC comes out? I filed a bug...

-Kev

---

### Post by spaceballl on 2006-02-23
anyone else having this problem?

---

### Post by eidex on 2006-02-27
I can confirm this bug (ibook G4 12" 1200) , BT Mouse not working any more...

---

### Post by eidex on 2006-02-27
Strange:

> paul@wolf:~$ sudo hidd --search
Password:
Searching ...
        Connecting to device 00:0A:95:0A:3E:6C
Can't get device information: Host is down
paul@wolf:~$ sudo hidd --search
Searching ...
paul@wolf:~$ sudo hidd --search
Searching ...
        Connecting to device 00:0A:95:0A:3E:6C
paul@wolf:~$

After reading your bugreport on launchpad.net i started hidd, the first time it found nothing, the second time even less and the third time it connectes and works fine now :)

---

### Post by spaceballl on 2006-02-27
[QUOTE=eidex]Strange:
After reading your bugreport on launchpad.net i started hidd, the first time it found nothing, the second time even less and the third time it connectes and works fine now :)[/QUOTE]

Haha how about after you restart?

What's odd is that I can use my bluetooth keyboard early in the boot sequence to choose which OS to boot... so something during the boot sequence Fs it up. In any case, I'm currently using OS X more than Ubuntu, but I want to use Ubuntu more often, but i can't until this is fixed! I hope it gets fixed by the time Beta comes out!

---

### Post by CallMeAl on 2006-04-20
This is apparently still an issue two months later.  I downloaded the daily build of the beta live cd dated 4/20, and I'm having this exact same problem on a Mini.Anyone have ideas as to when this might be resolved?

Thanks,


--Al

---

### Post by spaceballl on 2006-04-21
it's ridiculous. Here's a workaround.

Remove all bluez-* packages.

---

### Post by balleklorin on 2006-05-25
I can confirm this issue with flight 7  AMD64 also... :(

---

### Post by spaceballl on 2006-05-26
[QUOTE=balleklorin]I can confirm this issue with flight 7  AMD64 also... :([/QUOTE]
the easy workaround is to use synaptic and remove all bluez* packages. Not that this is a permanent solution, but it fixes things.

---

### Post by josephedwardmartinez on 2007-08-06
I may be too late on this thread but I was able to get my MX5000 keyboard/mouse combo to work using the workaround above.

Version: Ubuntu 6.06 Alternate Install

---

