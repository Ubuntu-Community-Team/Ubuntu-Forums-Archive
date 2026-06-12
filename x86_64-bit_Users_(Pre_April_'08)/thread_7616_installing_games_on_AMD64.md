---
title: "installing games on AMD64"
date: 2004-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mistic on 2004-12-09
hi there,

I'm installing Ubuntu on a friends AMD64, and he wants to play Q3A, ET, Doom3 and stuff, now i know there are linux-binaries for them, i've allready downloaded them, chmodded and ran them, problem is the install fails, it says:
```

This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on x86_64/glibc-2.0
```

anyone knows how to fix this?

grtz
Mistic

---

### Post by dmatrix on 2004-12-09
The only way that I know of is to go thru the work and build a 32bit chroot. Details on this can be found here:

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

It sure would be nice if someone could come up with a better solution something is probably missing in the ia32-libs. As well it sure would be nice if there was a ia32-libs with support for wine/cedega. I would love to rid myself of this 32bit chroot for gaming....

Anyone have any better ideas for running 32 bit binaries like wine/cedega and some Loki installers on AMD64 Ubuntu?

---

### Post by mistic on 2004-12-09
i think that is a bit overkill

these installers work perfectly on gentoo so it should be possible without the chroot... 

its not for using wine/cedega, its all for games that should run natively under linux (all games by ID-software) 

my idea is that a game that doesn't come out for linux natively isn't worth playing :)

---

### Post by ahyden on 2004-12-23
I managed to install both Doom 3 and Quake 3 on amd 64 without having to create a 32bit chroot environment.

Doom 3 just worked, no problem here, however when I tried to run the quake3 linux installation binary I got a message similar to yours. I had to unpack and run the installation manually:

sh linuxq3apoint-1.32b-3.x86.run --target q3
cd q3/
sudo ./setup.sh

I think this also works for other .run files from id-software, but I havn't tried.

Hope it helped  :p

---

### Post by setite on 2004-12-24
[QUOTE=mistic]i think that is a bit overkill

these installers work perfectly on gentoo so it should be possible without the chroot... 

its not for using wine/cedega, its all for games that should run natively under linux (all games by ID-software) 

my idea is that a game that doesn't come out for linux natively isn't worth playing :)[/QUOTE]

pfft... thats insane... until the entire gaming community embraces linux there will always be good games that were not released for it...

---

### Post by mistic on 2004-12-25
[QUOTE=setite]pfft... thats insane... until the entire gaming community embraces linux there will always be good games that were not released for it...[/QUOTE]

but for real gaming, i've got about 21 gaming-consoles lying around, so that pretty much enables me to play any game :-)


[look here](http://users.skynet.be/mistic/tehLair) 

but seriously, i can't bring myself to running windows just for gaming anymore... right now I have absolutely NO windows anymore, the only windows around is that of my roommate and even he is starting to switch :-)

I've even converted all the PC's back home to linux (saves me a whole lot of problems each time I get home :-) ) plus as soon as it all is installed, it is easy enough for anyone to use...

grtz
Mistic

btw thx hayden for the help...

---

### Post by golpira on 2004-12-27
For what it's worth, I have Unreal Tournament 2003 running fine one a dual opteron.  Single-player, internet play, and server hosting all work fine.  Epic did a great thing in releasing both 32-bit and 64-bit ports of the game for Linux.

---

### Post by litbos on 2004-12-28
I try to install ennemy-territory on my AMD64 and i have the same error , when i have a fedora core 3 X86_64 i use this command

linux32 sh et----.run 

and it's work very well , did you know how to find the package linux32 or how to install enney territory without linux32.

i have try with the command --taerget but the program a file default.cfg 

can you give me a solution

thanks

---

### Post by Dylanby on 2004-12-28
I got that error when trying to install Doom 3. I found this on the Linux Games forums:

> I am running Debian unstable for the amd64 arch. The doom3 installer thought I had glibc2.0 installed but I really have 2.3.2. Thus the install failed.

Here are my steps for working around this problem:

sh doom3-linux-1.1.1282.x86.run --noexec --keep
cd doom3-linux-1.1.1282
ln -s bin/Linux/amd64/glibc-2.1 bin/Linux/amd64/glibc-2.0
./setup.sh 

This worked, but led me to other problems:
[http://www.ubuntuforums.org/showthread.php?t=9256](http://www.ubuntuforums.org/showthread.php?t=9256)

---

### Post by litbos on 2004-12-29
when i have fedora core amd64 , it's work with this command

```
linux32 ./et----.run
``` 

i have compile linux32 source , but i don't work 

 :-(

---

### Post by pay on 2007-01-06
This is quite late but now that quake3 is open source there is a 64bit version of the engine that you could use. [http://ioquake3.org/?page=get](http://ioquake3.org/?page=get)

---

### Post by dmn_clown on 2007-01-07
As often as people run into this you'd think they'd make it a sticky either here or on the gaming forums ](*,) 

*shrugs*

---

### Post by Xpress211 on 2007-05-15
> **mistic said:**
> hi there,

I'm installing Ubuntu on a friends AMD64, and he wants to play Q3A, ET, Doom3 and stuff, now i know there are linux-binaries for them, i've allready downloaded them, chmodded and ran them, problem is the install fails, it says:
```

This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on x86_64/glibc-2.0
```

anyone knows how to fix this?

grtz
Mistic


[Loans weather biology Debt Consolidation plants](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

