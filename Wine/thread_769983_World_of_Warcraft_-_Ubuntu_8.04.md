---
title: "World of Warcraft - Ubuntu 8.04"
date: 2008-04-27
forum: Wine
---

### Post by Jaxilian on 2008-04-27
I have graphics problem with World of warcraft under the new Ubuntu 8.04. I can get it to run, but the whole gaming window (running windowmode) is blinking like every half second. I tried fullscreen too, but same result.

I am using Wine 0.9.60. The game works, but it's annoying as hell to have this graphic issue.
I have the ATI Catalyst™ 8.4 Proprietary Linux x86 Display Drivers installed that I got from [http://ati.amd.com](http://ati.amd.com).

Before I installed Ubuntu I had OpenSuse 10.3 installed with same video drivers as above and then I had no problem with the game.

Anyone know what this could be?

---

### Post by Mr_Congeniality on 2008-04-27
Alot of people are having issues with Wine on Hardy right now.  What's even worse is that Hardy is less successful than it was in its development versions.

If you try doing everything the same on Ubuntu Gutsy 7.10, everything will work perfectly.

As for 8.04 Hardy, it should still be considered under development because of how many problems it is having.

---

### Post by Jaxilian on 2008-04-27
> **Mr_Congeniality said:**
> Alot of people are having issues with Wine on Hardy right now.  What's even worse is that Hardy is less successful than it was in its development versions.

If you try doing everything the same on Ubuntu Gutsy 7.10, everything will work perfectly.

As for 8.04 Hardy, it should still be considered under development because of how many problems it is having.

Thanks for your answer

---

### Post by evozniak on 2008-04-27
try to disable desktop efects,
if game is flickring when compiz is enabled and not when disabled. are the popular bug with DRI and AIGLX.

---

### Post by Jaxilian on 2008-04-27
> **evozniak said:**
> try to disable desktop efects,
if game is flickring when compiz is enabled and not when disabled. are the popular bug with DRI and AIGLX.

Is desktop effects on by default?

---

### Post by evozniak on 2008-04-27
yeap, hardy is out the box with efects on by default!

---

### Post by andrewjoy on 2008-04-27
I would stick with 7.10 for now, wine form what i can see has major problems in 8.04 lucky i noticed a few post about it realy i was going to let the upgrade run whilst in wrok today, it would have been kind of hard to raid tonight with the screen flashing.

---

### Post by Jaxilian on 2008-04-27
> **andrewjoy said:**
> I would stick with 7.10 for now, wine form what i can see has major problems in 8.04 lucky i noticed a few post about it realy i was going to let the upgrade run whilst in wrok today, it would have been kind of hard to raid tonight with the screen flashing.

I solved this issue for me. I just went to:
System > Preferences > Appearance > Visual effects
and I set it to **None**

I now get same as I did in Opensuse. I haven't explored the whole world yet, but I think it's ok.

---

### Post by ribbon on 2008-05-03
This fix also worked for me -- setting visual effects to none!
Hopefully we can get both work at some point :)

Now to get my side mouse buttons working :X

---

### Post by Luke has no name on 2008-05-03
I'm getting memory access violation errors. I can't even start the game!

---

### Post by Demoncrat on 2008-05-03
I have the same problem as the above poster atm, but with the difference that it has worked for me under Ubuntu 8.04.

The only thing I have changed is that I removed "nvidia-glx" from synaptic and replaced it with "nvidia-glx-new". Since I did that, I get a "memory violation" error.

I'm going to reroll them now... I'll keep you posted.


Update: I rerolled to the previous drivers, and everything works fine now (even with desktop effects enabled it seems)


d

---

### Post by andrewjoy on 2008-05-03
> **flodis said:**
> I solved this issue for me. I just went to:
System > Preferences > Appearance > Visual effects
and I set it to **None**

I now get same as I did in Opensuse. I haven't explored the whole world yet, but I think it's ok.


Ooo realy i may give this a try then in a week or so ( got a prolog/ai and sum stupid opperating systems in java exam :( ) i have been considering builing the sorce of wine on a 64 bit 8.04 install as i know others who have tested the 64 bit verson of 8.04 and have reported firefox3 and flash working correctly ( 64bit verson of firefox3 as well).

---

### Post by evozniak on 2008-05-04
Luke try this.
reboot your computer and on System select choose Memtest
in geral there errors ocuors when your phiscal memory contais a error

---

### Post by PinguimMaluco on 2008-06-23
Hello, fellows! I'm running Wow on Ubuntu 64 8.04, with Wine. My problem here is that the game run "fine" but when I try to connect to any server, the game stop on the message "Connected". Could someone give me any light on this problem? I appreciate the atetion.

Oh, I almost forgot to post my system. It's a pentium 4 3.0 ghz, 1gb RAM, graphic card Geforce 7300SE with 512 mb. I had the last Wine (1.0) too.

---

### Post by atowell on 2008-07-03
> **flodis said:**
> I solved this issue for me. I just went to:
System > Preferences > Appearance > Visual effects
and I set it to **None**

I now get same as I did in Opensuse. I haven't explored the whole world yet, but I think it's ok.

Thank you for posting your solution to this! I'm using Hardy and I've been jumping through a few hoops in order to get WoW working, but it's worth it if I don't have to use vista.

---

### Post by bobo on 2008-09-23
I've got WOW working with the exception of the framerate.  It's running at 2 FPS.  Now granted I'm in Shat, but I can run through there fine on the same machine in Windows.  

Laptop info:
Intel Core2 Duo
2Gb RAM
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Any help would be appreciated.

---

### Post by Mistrblank on 2008-09-26
> **bobo said:**
> I've got WOW working with the exception of the framerate.  It's running at 2 FPS.  Now granted I'm in Shat, but I can run through there fine on the same machine in Windows.  

Laptop info:
Intel Core2 Duo
2Gb RAM
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Any help would be appreciated.

Integrated Intel 945 graphics are a known fail in terms of WoW and wine.  It's just not powerful enough to power the game on.  Your best bet is to try with the opengl recommendation off (go with Directx by default), but I wouldn't hold out a lot of hope as I couldn't get it to work on my macbook's integrated video and it works fine in OSX and Windows on the same machine.

---

