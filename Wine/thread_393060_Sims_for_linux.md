---
title: "Sims for linux"
date: 2007-03-25
forum: Wine
---

### Post by Aurigas on 2007-03-25
Hi, I want to play with the sims on ubuntu and i read there is a native version for linux. where can I buy it? is there any patch for the people who have buy it for windows system? Thx!

---

### Post by rolando2424 on 2007-03-25
As far as I know, there is no native version of Sims (1 and 2) for Linux.

I don't know if they will run on Wine or Cedega though...

---

### Post by timcredible on 2007-03-25
well, the sims is available on the ps2.  maybe that's the native linux version you heard about.

---

### Post by Lystrodom on 2007-03-25
Doesn't work in Wine, according to the appDB.

---

### Post by hikaricore on 2007-03-26
> **timcredible said:**
> well, the sims is available on the ps2.  maybe that's the native linux version you heard about.

Think you mean ps3?

And to the OP, yea sims will probably not work under linux.

[Wine Application Database]("http://appdb.winehq.org") search for your game and find out yourself.

---

### Post by bwingbob on 2007-03-26
TransGaming use to sell a version of the Sims for Linux. Not sure if it is still available though.

I purchased TransGaming's Kohan port years ago, I haven't messed with it in quite a while, but I enjoyed it and it worked as advertised. I also use to subscribe to WineX, it's called Cedega now. When I was using it, the games that were fully supported pretty much ran as well on Linux as Windows, occasionally better. :) 

[TuxGames]("http://www.tuxgames.com") has a selection of native Linux games.

---

### Post by chrisLACHCIK5084 on 2007-05-26
sims 2 does not work in ubuntu at all, even thru wine. it'll ask for the second cd and when you open your disc tray, wine will still be using that source and so it'll come up with a stupid error each time and you'll just have to restart your computer after you stop the install.

---

### Post by hikaricore on 2007-05-26
Not that it matters but you could copy the contents of the discs to your hard drive and try to install.

Sims 2 does not run worth anything under wine so again it's pointless.

You don't have to restart your computer you can just kill the wine process or run:

> wineserver -k

---

### Post by ash45 on 2008-09-06
hi just to let you know yes there is a sims for Linux its the first one it used to be bundled with mandrake a few years ago i used to have a copy but i gave it away i haven't been able to find a copy since tho but there definitely was one :)

---

### Post by rossjman1 on 2008-09-06
From Wikipedia:
> # The Sims was ported to Linux using Transgaming's WineX technology (now known as Cedega) and was bundled with Mandrake Linux Gaming Edition. However, both WineX and the Cedega engine are unable to run the Windows version of the game. The original port will no longer run on modern Linux distributions and is unable to accept the various add-on packs intended for the Windows version.[citation needed]

---

### Post by anjilslaire on 2008-09-06
this thread is over a year old...

btw, It does run under an OpenBox WinXP VM, even without hardware acceleration. Still, that's a poor option :(

---

### Post by schmindy on 2008-09-14
[http://ubuntuforums.org/showthread.php?t=919372](http://ubuntuforums.org/showthread.php?t=919372)

---

### Post by rettichschnidi on 2009-01-31
Hi 

I got the Sims for Linux running under Ubuntu 8.10 x86.

Note 1: I didn't test that solution for a long game so I'm not sure if it runs stable.
Note 2: You have to have the Sims for Linux, the updates for Sims AND Cedega

Here are my steps:

Copy simsdata.rpm from CD and the updates The_Sims-3.2-1.i386.rpm and
WineX_Sims-3.2-2.i386.rpm to a writable directory.

convert them to deb's (I'm using Ubuntu 8.10 32bit):
```
alien *rpm
```

install the files:
```
sudo dpkg -i *deb
```

run ```
the_sims 
```once, it will ask for the serial, check the CD and start the Sims. Quit the Sims ASAP, it would not work now.

delete old WineX:
```
rm -rf /usr/lib/the_sims/winex_sims/*
```

Copy fresh Winex/Cedega (4.1.1 works for me):
```
sudo cp -R ~/.cedega/.winex_ver/winex-4.1.1/winex/* /usr/lib/the_sims/winex_sims/ 
```


run ```
the_sims
``` or ```
the_sims -r1024x768
``` again, should work now. 


Would be happy to hear if it worked out for you.

---

### Post by anjilslaire on 2009-02-01
I.m confused. Why would cedega be required for Linux build of the Sims? 
Does it get installed from the game disc? If it's required, then I'd say its not *really* "for Linux"...

---

### Post by hikaricore on 2009-02-01
Same reason the EVE for Linux requires cedega.  Because they really didn't bother to port it.

---

### Post by rettichschnidi on 2009-02-02
Yes, it's not a "real" port. But AFAIR it's still the only way to get "the Sims" running under Linux (no, a VM doesn't count, at least for me)

---

### Post by anjilslaire on 2009-02-03
> **rettichschnidi said:**
> (no, a VM doesn't count, at least for me)

Agreed. I was just giving an option I've confirmed.

---

### Post by m3t3ors on 2010-08-27
i have a copy of mandrake with the sims linux version, i have had it running on ubuntu a few years back. but havent tried recently

---

### Post by marks760108 on 2011-02-08
i know cedega says it will work, but i dont know how to use cedega, any help would be appreciated

---

### Post by lisati on 2011-02-08
Wow! A thread started in 2007 is revived! May it rest in peace!

---

