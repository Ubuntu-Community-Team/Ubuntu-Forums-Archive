---
title: "Linux32 and linux-util"
date: 2008-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by MystikIncarnate on 2008-02-11
i have a seriously serious question here....

I've been running ubuntu-studio 7.10 for a good while now, almost full time in fact.  In an effort to be a full time linux user, i've been looking into various game alternatives and VMs/Emulators/Compatability layers... including WINE, and VM Ware.

I stumbled across some information about Doom 3 being Linux compatable... well, since they're obviously not throwing out the code for Doom 3 for me to compile, i have to go with the binaries they've put out... problem is, i'm using a Core 2 based CPU, with EM64T, and the 64-bit core of Ubuntu 7.10.  so i need linux32 in order to run the application.  though, when i do, it works flawlessly (after some minor modifications to graphics and game settings)...

HOWEVER, i do a LOT of work from the console, and to have various linux utilities ( 'more' comes to mind), i need the package 'linux-util' ... unfortunately, for whatever reason, linux32 and linux-util WILL NOT both be installed at the same time... if i install linux-util, linux32 gets removed... if i install linux32, linux-util goes away.

is there any way around this? it's rather frustrating to have to install/uninstall things every time i want to play the game (not to mention how useful features from both apps are)

Thanks in advance.

---

### Post by Cappy on 2008-02-11
util-linux contains linux32. Don't remove util-linux ^^

---

### Post by MystikIncarnate on 2008-02-13
does it?

jeeeez, thanks! i wish i was more aware of these packages and what they contain!  there should be a list on the wiki or something! gah.

:)

---

### Post by steveneddy on 2008-02-17
I run a 64 but machine and for other issues, I had to install and run the 32 bit version of util-linux and uninstall the 64 bit version and show it in Synaptic as locked.

But I also have the lib32 packages installed so 32 bit software can run on my 64 bit machine.

---

### Post by Cappy on 2008-02-17
I don't know what issues you were having but you probably could have left the 64-bit version installed and let getlibs install the 32-bit util-linux libraries into /usr/lib32

---

### Post by steveneddy on 2008-02-17
> **Cappy said:**
> I don't know what issues you were having but you probably could have left the 64-bit version installed and let getlibs install the 32-bit util-linux libraries into /usr/lib32

The issues were my hwclock wouldn't stay synced. After a couple of weeks it would be off by months. I couldn't get the hwclock in the BIOS to tick, but with the addition of the 32 bit util-linux, and yes, I had to uninstall the 64 bit version, the clock ticks every time.

I can't prove it, but I think it had something to do with the -rt kernel in 64 bit and my hardware that caused the original issue requiring the substitution of the 32 bit util-linux package.

---

