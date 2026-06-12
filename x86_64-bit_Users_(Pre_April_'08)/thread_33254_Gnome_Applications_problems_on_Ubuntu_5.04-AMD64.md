---
title: "Gnome Applications problems on Ubuntu 5.04-AMD64"
date: 2005-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by zodmaner on 2005-05-10
Hello, a couple of questions here if you may:

In my current installation of Ubuntu two application will alway crash, the first one is gThump, an image viewer, which runs just fine but will crash when I change directory to root directory (/). the other is Totem movie play(sorry if I got the name wrong) which will always crash every time I try to open it.

I've tried reinstall, but it doesn't help. I don't have any problem like this when running Slackware 10.1 (Totem works fine, haven't tried gThump cause I didn't install Gnome).

What do you guys thinks? I'd love to hear you thought on this, also is it just me or is it very VERY hard to do a 'make' command work in Ubuntu (I'm newbie, so I maybe wrong on this) the default installation of Ubuntu doesn't come with kernel-source, you have to get it you self and it wouldn't let you use other dicectory other then you /home, does anyone know a work around on this?(I've tried to complies my USB modem driver on Ubuntu , the first time I tried it fails to complies because I don't have gcc install, the second time because I don't have kernel source and so on...)

Thanks for all you input.  :) 

my system:

AMD 64 3200+ (2.0 GHz)
512 MB RAM
Asus A8N-SLI Deluxe (with on board sound and LAN card-Marvell Yucon I think.)
ATI X700 XT
SATA 160 GB HD (forget the brand, gotta check on this.)
Billion BIPAC-7000 USB ADSL Modem -* Does anybody know how to make this darn thing work with linux? I tried every thing
([http://www.linuxquestions.org/questions/showthread.php?s=&threadid=319800](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=319800), 
[http://ubuntuforums.org/showthread.php?t=31640](http://ubuntuforums.org/showthread.php?t=31640), [http://www.linuxquestions.org/questions/showthread.php?s=&postid=1631258#post1631258](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1631258#post1631258))
and the thing still refuse to work.(first two major effort in Ubuntu, where I have problem trying to complies the driver. The third major effort in Slackware10.1, which, although the driver complies nicely, for some reasons it fails to detect my modem. :neutral: )

---

### Post by Lakesis on 2005-05-10
Hi zodmaner!

First of all, sorry for not answering your topic. I would like to help you but as you will se I'm unable at this right moment.

I've a quite similar sytem: AMD64, SATA HD and an ATI x700 PCI Express.
The problem is that my X don't work, not even with the "vesa" driver. My ATI is causing problems that I don't know how to solve.

I've tried several ATI Install guides (included the one in this forum) without a satidfactory result. I've even read that this card is not still supported!

As we have the same (or very similar) card I would like to know how did you manage to use the desktop manager.

I'm interested in the same software you find problems in, so I think I'll be able to help solving your problems once I get the X xD

Thanks and sorry again!

---

### Post by zodmaner on 2005-05-10
Hello there Lakesis   :smile: always glad to see fellow AMD & ATi around.  :grin: 

Not sure that I can help you either, all I did was run xserver config though command: 

sudo dpkg-reconfigure xserver-xorg

I then setup my card using 'vesa' drive, set my screen resolution and refresh rate  according to my monitor spec and that it.

Could you post the error message? I'm sure someone here will be able to tell you what's went wrong from it.

again, nice knowing you Lakesis.  ;-)

---

### Post by Lakesis on 2005-05-14
Hi again!

I finally managed to get my X runnig with the vesa driver.
I've checked the applications you mention and I have the same problems, just in case you wanted to know xD
gThumb crashes when I reach the root directory and I can't open totem...
Don't know why.

See you!

---

### Post by zodmaner on 2005-05-16
:) Thanks for the info Lakesis, good to know that I'm not the only one with these problems.

---

### Post by Jarz Corp on 2005-05-18
Well U and me makes 5 or something.

I have similar problems:

Totem won't play anything at all, unable to open resource for writing. Which is pants when all I do is try to open a .avi file on network drive where it shouldn't write at all.

The thing with gthumb is a stupid bug, if U write the dir where U want to go in the address field it works no prob, but for some stupid reason it cant browse across directories where it has different right levels, or the user running it of course.

I think that most of our problems are within the 64bit realm, codecs not existing etc.

What makes it worse is to things.

1: When u post problems like this U get gits like me who are no help at all but only can say ditto.

2: U get answers from guys that tell U to read the guide and do this and do that after U already having explained to them that U have tried these things.

It would be fun if there was ONE app that could play all video formats and not having to go through 3, xine-mplayer-vlc (totem isnt really a player only a frontend) everytime we wanted to watch some video.

---

