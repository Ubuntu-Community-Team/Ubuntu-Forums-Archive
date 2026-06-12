---
title: "Any Delphi or Kylix program for Amd64???"
date: 2005-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by nrayever on 2005-09-10
i'm having a problem trying to find a object pascal ide program, such as kylix 3.0 (delphi's clone for linux) that really works on amd64. according to borland, kylix system requirements, it just work with x86 processors. may i'm doing something wrong... i some one could help me to solve this. maybe suggesting me another program or telling me howto install kylix on my amd64.

then, what kind of problem do i have with kylix 3.0??
```
                                   BORLAND KYLIX 3

Checking dependencies...
Kernel version >= 2.2.0....OK
Glibc version >= 2.1.2....OK
X11 Server....OK
Libjpeg version >= 6.2.0....OK
Libgtk version >= 1.2.0....OK


This installation does not support glibc-2.0 on x86_64

Please contact Technical Support.
``` 

any suggestions??? please help!!! i need it, because i have to make several programs for a final project for my university.

nrayever

---

### Post by FluffyElmo on 2005-09-14
Free Pascal has a compiler for amd64:
[http://www.freepascal.org/fpc.html](http://www.freepascal.org/fpc.html) 

It may or may not do what you need, in my day Pascal assignments didn't have guis...but times have probably changed:)

---

### Post by FluffyElmo on 2005-09-14
One more thought, if freepascal won't suffice you'll almost certainly be able to install Kylix using a 32bit chroot:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by acariquara on 2005-09-18
[QUOTE=nrayever]i'm having a problem trying to find a object pascal ide program, such as kylix 3.0 (delphi's clone for linux) that really works on amd64. according to borland, kylix system requirements, it just work with x86 processors. may i'm doing something wrong... i some one could help me to solve this. maybe suggesting me another program or telling me howto install kylix on my amd64.

then, what kind of problem do i have with kylix 3.0??
```
                                   BORLAND KYLIX 3

Checking dependencies...
Kernel version >= 2.2.0....OK
Glibc version >= 2.1.2....OK
X11 Server....OK
Libjpeg version >= 6.2.0....OK
Libgtk version >= 1.2.0....OK


This installation does not support glibc-2.0 on x86_64

Please contact Technical Support.
``` 

any suggestions??? please help!!! i need it, because i have to make several programs for a final project for my university.

nrayever[/QUOTE]
 Sorry if I sound sarcastic, but seems like a good opportunity to learn Python :)

Python+boa constructor 0wns Kylix, multiplatform and already x86_64.

---

### Post by nrayever on 2005-09-18
[QUOTE=acariquara]Sorry if I sound sarcastic, but seems like a good opportunity to learn Python :)

Python+boa constructor 0wns Kylix, multiplatform and already x86_64.[/QUOTE]

maybe a nice suggestion, but i don't have time to learn python.  i need an easy pascal object ide program. plus, i would like that the application should  be multiplatform. 

once i tryed chroot32, but no luck. maybe i'm to stupid, but i made it as the howto said and something messed up. don't ask me in which step, because i just, copy'n'paste the instructions. but i might try again. or maybe using bochs  :grin:  :grin:  any other suggestion will be accepted

---

### Post by acariquara on 2005-09-19
[QUOTE=nrayever] but i might try again. or maybe using bochs  :grin:  :grin:  any other suggestion will be accepted[/QUOTE]

Ugh. If you are going to do the emulation route at least use VMWare... it is x86-to-x86 anyway. Bochs is a nice IA32 emulator but all calls are emulated and not "translated" like VMWare - that's good because you can emulate a x86 architeture on non-x86 processors (PowerPC etcetera), but the performance hit is considerable.

---

### Post by acariquara on 2005-09-19
oh and BTW this is way offtopic but here's what I did with VMWare... see, I still have WindowsXP on some machines but at least I got rid of MS Orifice :razz: - all OOo, all the time.

Except there's the occasional j*rk that insists on using Powerpoint presentations, and Impress filters are not that top-notch (some graphical glitches that would go unnoticed in Word documents but with Powerpoint presentation is a must). 

So what did I do? 

Even on my machine using WindowsXP I installed an old copy of Win2000 that was laying around inside VMWare, and installed the Orifice in the virtual machine only. Pretty much the same way antivirus companies test their virus removal tools... ironic? Actually, i *did* take that idea from them.  :roll: 

Windows XP without Office keeps sanity at check. Lesser of two evils, should I say. Vista? Thanks to Ubuntu, I do not care. Not anymore. I'm free.

---

### Post by nrayever on 2005-09-20
[QUOTE=acariquara]Windows XP without Office keeps sanity at check. Lesser of two evils, should I say. Vista? Thanks to Ubuntu, I do not care. Not anymore. I'm free.[/QUOTE]

hehehehehe, that's cool!!. something similar happend to me. since i'm using ubuntu my friends ask me for a good antivirus or a solution for a spyware, so i told them: 

"i don't know what is that!!! because i use linux, firefox, oO and no antivirus!!"

then they gave me a look (like want to kill u, or wtf is THAT!!) so then i suggest them to use clamAV and firefox for winbugz. that makes them happy!!  :grin:  :grin: 

changing subject, maybe i should try again with chroot32 or give a try with vmware.

thanks guys!!

---

