---
title: "Relative NOOB with a wireless question..."
date: 2005-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by snare687 on 2005-03-26
Greetings all...

Just got my Averatec 6240 Athlon64 laptop back from being serviced.  Had been running SuSE 9.2 Pro 64bit prior to service and drive wipe.  Decided to give Ubuntu a shot on reinstall.  Any advice on how to get the RT2500.ko to insert so I can use the Ralink drivers for my wireless?  I managed to get the module to compile, just lost on the where and what next...  Had the wireless working natively under SuSE...  Any advice appreciated...

Cheers,

Greg Dubetz

---

### Post by songochain on 2005-03-27
[QUOTE=snare687]Greetings all...

Just got my Averatec 6240 Athlon64 laptop back from being serviced.  Had been running SuSE 9.2 Pro 64bit prior to service and drive wipe.  Decided to give Ubuntu a shot on reinstall.  Any advice on how to get the RT2500.ko to insert so I can use the Ralink drivers for my wireless?  I managed to get the module to compile, just lost on the where and what next...  Had the wireless working natively under SuSE...  Any advice appreciated...

Cheers,

Greg Dubetz[/QUOTE]
 If u've the driver for windows xp 64 u can install it using ndiswrapper

---

### Post by mthaddon on 2005-03-27
And if you can't find the driver, chances are linuxant may have it:

[http://www.linuxant.com](http://www.linuxant.com)

---

### Post by songochain on 2005-03-28
[QUOTE=mthaddon]And if you can't find the driver, chances are linuxant may have it:

[http://www.linuxant.com](http://www.linuxant.com)[/QUOTE]
 paying for a driver?

---

### Post by mthaddon on 2005-03-28
I got mine from there and didn't pay a penny for it. Not sure where you're looking....

I guess I should clarify - I'm meaning to get the Windows 64 bit driver from here for use with ndiswrapper.

---

### Post by songochain on 2005-03-28
[QUOTE=mthaddon]I got mine from there and didn't pay a penny for it. Not sure where you're looking....

I guess I should clarify - I'm meaning to get the Windows 64 bit driver from here for use with ndiswrapper.[/QUOTE]
 I downloaded linuxant driver and i saw 30 trial days... but if u've a free linuxant driver, where did u download it? Because i' m watting for a release of windows 64 driver to can use my wifi card

---

### Post by X3N on 2005-04-03
[QUOTE=snare687]Greetings all...
I managed to get the module to compile, just lost on the where and what next...  Had the wireless working natively under SuSE...  Any advice appreciated...
[/QUOTE]

Isn't it just a case of /sbin/modprobe nameofmodulecompiled ?

and aslong as you have the iwconfig and those wireless tools installed you'll be able to configure it.
 
And you might be wanting to add an alias for it for modprobe that would look a bit like wlan0 nameofmodulecompiled

---

