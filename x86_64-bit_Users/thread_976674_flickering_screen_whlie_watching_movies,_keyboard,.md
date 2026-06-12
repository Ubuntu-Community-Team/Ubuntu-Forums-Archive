---
title: "flickering screen whlie watching movies, keyboard, headset"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by leroux on 2008-11-09
Hi everyone

i'm running Kubuntu 8.10 on my machine:
Gigabyte ga-p35-ds3p
intel dual core (a little overclocked), 2 GB RAM
ATI Radeon x1950 512 MB (yes i know nvidia would be better)
Screen: Samsung Sync Master 226 cW :popcorn:
keyboard: Cherry eVolution G230 Swiss layout.

I'm a newb, just to warn you! Sorry to embarrass you!

I've got a flickering screen when i'm watching movies (Kaffeinne, M-Player, Dragon-Player). I've got the ati Catalyst installed. (Res.: 1680:1050 should be ok) 

xorg.conf:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"

(buy nvidia?)

My keyboard looks like this:

[http://wikis.sun.com/download/attachments/23397070/SwitzerlandFR_Solaris_Keyboard_Layout.png](http://wikis.sun.com/download/attachments/23397070/SwitzerlandFR_Solaris_Keyboard_Layout.png)

The circumflexes aren't working (configured ch de_sundeadkeys). I've tried to change the compose key, utf-8, etc still no circumflexes on e,a,o,i,etc. Tilde doesn't work either. I've been surfing for quite along time through the forum but nothing i've tried worked yet. (this isn't an issue in windoze damnit!)

Last but not least my headset doesn't work (plantronics ultra-cheap), well i can hear but the mic doesn't work. Maybe i'm unable to configure kmix like it should be, perhaps i should get another one.

Great work guys. The first time I've tried an linux dist was 6 years ago (fedora) and i didn't manage to get anything done. I've started with Ubuntu gutsy and really liked it. Ubuntu is a very good and easy way to enter the linux-world (userfriendly, u dont like that word don't you :lolflag: ).
But the new Kubuntu 8.10 just takes my breath away! It was very easy to install, quick also. It boots quickly and KDE4 is quite sexy (for an OS)!
Great work guys! I love you! U :guitar: !

Thanx for your passion, assistance and patience
Greetings from Belgium
leroux

---

### Post by Kilz on 2008-11-09
> **leroux said:**
> Hi everyone

i'm running Kubuntu 8.10 on my machine:
Gigabyte ga-p35-ds3p
intel dual core (a little overclocked), 2 GB RAM
ATI Radeon x1950 512 MB (yes i know nvidia would be better)
Screen: Samsung Sync Master 226 cW :popcorn:
keyboard: Cherry eVolution G230 Swiss layout.

I'm a newb, just to warn you! Sorry to embarrass you!

I've got a flickering screen when i'm watching movies (Kaffeinne, M-Player, Dragon-Player). I've got the ati Catalyst installed. (Res.: 1680:1050 should be ok) 



If you have desktop effects enabled with ATI graphics (nvidia? I prefer ati, the HD 3870 x2 is just awesome) the video will sometimes flicker. I managed to get rid of it by changing the video output to Xv in my media players. Since I dont run KDE I dont have kaffine installed. So I cant tell you where to change the settings for it. Mplayer can be adjusted by selecting Xv in the Video tab in preferences. If it doesnt solve it, just disable desktop effects while watching movies.

---

### Post by leroux on 2008-11-10
Hi Kilz
thanx for your reply!
disabeling the desktop effects stops the flickering! I'm still looking for some other way to solve this. Changing player settings didn't change anything! Maybe i should get a better graphics card!
Thanx again!

---

### Post by AmanicA on 2008-11-11
I managed to get kaffeine to stop flickering for me by doing:
In Kaffeine click on Settings, then Xine Engine Parameters, then video and change the selection to xshm instead of auto.  See if that works.
[http://www.kubuntuforums.net/forums/index.php?topic=3095873](http://www.kubuntuforums.net/forums/index.php?topic=3095873)

---

