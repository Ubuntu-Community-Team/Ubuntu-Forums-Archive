---
title: "Running Hearthstone in Wine o Ubuntu 13.10"
date: 2013-12-13
forum: Wine
---

### Post by Ertai87 on 2013-12-13
Alright, so I'll start by saying my computer is really old and doesn't meet minimum specs for Hearthstone, but if the game is just slow or bad graphics I'd like to try it anyway.  But I can't get it to run at all.  Here's what's going on:

I got the program installed by upgrading Wine to 1.7.  Now when I launch it (by using the desktop icon because I don't know how to launch it using command line cause I'm a total noob), a box pops up that says "Error" in the title bar, but the content of the window doesn't load.  I think it loaded once and told me it was an OpenGL issue, but I can't get it to reappear.  The odd thing is that it doesn't appear to be a memory issue because my computer doesn't hang.  Everything runs fine, except that this error message (and consequently the Hearthstone application) doesn't load.

What does happen though is that this error message traps my mouse.  I can recover my mouse by ALT-TABbing to another window and then killing the Wine process from command line (remember, my computer isn't hanging so this is a fairly straightforward process), but this might be relevant data to anyone trying to help me solve this problem.

I know anyone answering this question would probably like a hardware profile.  I'd be happy to provide one, if someone would tell me how to generate it.  I'm running a Dell Inspiron 6400 with 1GB RAM, if that helps at all (yes, I know HS requires 2GB minimum, but if I can get some functionality out of 1GB I'll see what I can do; if it's too crappy I'll give up, but if not I'd like to play; I'm going to buy a new computer in about 4 months but I can't get one until then so I have to deal with this mess for the time being).

Thanks.

---

### Post by codenine75a on 2013-12-15
What is the size of your swap partition?  You can try to increase the size of your swap partition to run it because you stated it requires a 2GB minimum.

---

### Post by Ertai87 on 2013-12-16
It should be the default size, whatever Ubuntu suggests when it installs.

That said, I think the problem has to do with rendering by OpenGL, not any sort of memory issue.  If it was a memory issue, I'd think the computer would lock up or something, and it doesn't lock up at all.  Everything runs perfectly fine in the background,  except HS doesn't load properly.

---

### Post by Thee on 2013-12-16
Might not be related to your CPU or memory, but your graphics card or drivers.

---

### Post by Ertai87 on 2013-12-16
Possible.  I can't change my hardware, but I can change my software.  Thus a few questions:

1) If I provide my graphics card model (I don't know how to get it, but if someone tells me how to get it I can provide it), can someone tell me if there are better drivers than the Ubuntu default ones?

2) Is there a workaround to make Wine not try to render using OpenGL?  I read on Blizzard's forums that there's a way to do it, but the forum thread was full of power users, which I am not, and hence I don't know what they were talking about.  Something called D3D9 or something...

---

### Post by wildmanne39 on 2013-12-16
*Thread moved to **Wine**.*

---

### Post by Thee on 2013-12-17
Well, by searching your laptops model, I found that you have an ATI Mobility Radeon X1400, which is the lowest supported graphics card by Hearthstone, but still supported.
Now is your card supported on Ubuntu by ATI, that is a different story. You can see what driver you are using by going into System Settings > Software & Updates > Additional Drivers.
There, if possible, you should be able to choose a proprietary driver, which you should, if you want good 3D support for games. You can also check if 3D acceleration is enabled by typing:
```
glxinfo | grep direct
```
in the Terminal.

Hearthstone works fine with OpenGL, I'm running it without any problems, but I have a newer card.
So, check drivers, I think they are the problem, and if you are in luck, it should work when you select the proprietary drivers.

One more thing, if you didn't already, make sure you do what is described here in the "Installation Fix"
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=28875](http://appdb.winehq.org/objectManager.php?sClass=version&iId=28875)

It is necessary to be able to run the launcher properly.

---

### Post by Mark Phelps on 2013-12-17
IF indeed, your card is the ATI X1400, then sorry to say, there are no current Additional Drivers that will work with that card.  AMD dropped restricted driver support for that card YEARS ago -- so today, you are stuck with the default open-source drivers -- which are installed automatically during initial setup.

---

### Post by Ertai87 on 2013-12-18
According to "Devices" under System Settings, my graphics driver is Intel® 945GM x86/MMX/SSE2.  Is this useful information?

---

### Post by Mark Phelps on 2013-12-18
>  Is this useful information? 

Yes ... but ... Intel does not provide "Additional Drivers" and the ones you have now are the default Intel drivers that are installed during setup.

Sorry, but, as far as I know, there are no newer drivers for the Intel 945x series.

---

### Post by Ertai87 on 2013-12-18
In other words, my computer can't run HS?

---

### Post by Thee on 2013-12-18
Well it is below the specs required, so it's probably that, because it normally works without any problems.

---

### Post by Mark Phelps on 2013-12-18
> **Ertai87 said:**
> In other words, my computer can't run HS?

The problem is that your PC has a very OLD video chipset -- one for which newer drivers are not available.

It's not a Hearthstone problem, per se; it's an old video chipset problem.

---

