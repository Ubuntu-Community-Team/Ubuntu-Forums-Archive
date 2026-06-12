---
title: "Is anyone running Wine on AMD64?"
date: 2005-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by handy on 2005-12-18
I'd sure like to be able to run Wine, has anyone got it happening on 64bit hardware?

Thanks for your time.

handy

---

### Post by CrownRoyal on 2005-12-18
[QUOTE=handy]I'd sure like to be able to run Wine, has anyone got it happening on 64bit hardware?

Thanks for your time.

handy[/QUOTE]

I tried to getting it working yesterday but the compile errors out and there's no binary that I've found for AMD64. :( I just joined to look for help on this. I'd like to use Ubuntu for audio apps. So far, I've got somethings working but need help with Jack and a few other things. It's HARD to figure it all out.

---

### Post by nalmeth on 2005-12-18
Wine is not supported on 64-bit architecture yet. 
You can still use wine on you system however..
Follow this howto, replacing EVERY instance of hoary with breezy (don't forget any!). 

[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)

This will setup a 32-bit system inside your 64-bit.
you can symlink the app name to your 64-bit system, so that every time you execute it, it will run the 32-bit version. 

for wine I suppose you would do (after installing of course!):

sudo ln -s /usr/local/bin/wine /usr/local/bin/do_dchroot 

CrownRoyal:
What are your problems?

---

### Post by handy on 2005-12-19
Thanks for your reply nalmeth :-) 

I'll give it a go for sure.

handy

---

### Post by agsansoo on 2005-12-20
I'm running cross-over Office ! Isn't that wine ? 
And yes I'm running 64-bit !

Linux engr64 2.6.12-10-amd64-generic #1 Fri Nov 18 11:51:07 UTC 2005 x86_64 GNU/Linux

What are you trying to run with wine ?

---

### Post by mesilliac on 2005-12-20
If you don't want to use a chroot you might be able to get wine working using "ia32-libs" and an i386 wine .deb. Instructions are buried in this thread: [http://www.ubuntuforums.org/showthread.php?t=96620](http://www.ubuntuforums.org/showthread.php?t=96620). It seems to be working for me with this method, but I had to find a couple 32bit libraries that weren't in ia32-libs myself. I've only used it to run starcraft so far, but that works fine.

---

### Post by handy on 2005-12-21
[QUOTE=agsansoo]I'm running cross-over Office ! Isn't that wine ? 
And yes I'm running 64-bit !

Linux engr64 2.6.12-10-amd64-generic #1 Fri Nov 18 11:51:07 UTC 2005 x86_64 GNU/Linux

What are you trying to run with wine ?[/QUOTE]

I'd like to run DVDshrink, as much of Macromedia Studio MX 2004 as I can - Dreamweaver at least, have a try with some games.  Not a lot really.  I'm actually wondering if it is worth the trouble to go the "chroot" way?

How do you like "CrossOver"?

Cheers,

handy

---

### Post by handy on 2005-12-21
[QUOTE=mesilliac]If you don't want to use a chroot you might be able to get wine working using "ia32-libs" and an i386 wine .deb. Instructions are buried in this thread: [http://www.ubuntuforums.org/showthread.php?t=96620](http://www.ubuntuforums.org/showthread.php?t=96620). It seems to be working for me with this method, but I had to find a couple 32bit libraries that weren't in ia32-libs myself. I've only used it to run starcraft so far, but that works fine.[/QUOTE]

Thanks for this tip, I had a look at the thread, it looks a lot less involved than the "chroot" way.  If I had a lot of windoze stuff that I wanted to run I would go "chroot", but I don't. :)

I look forward to having no need for ANY windoze associated files...

Cheers,

handy

---

### Post by agsansoo on 2005-12-23
sorry it took so long ... 

Have you looked at xDVDshrink yet ? 

As for CrossoverOffice, It works for what I need it to do. IE, Excel ... Though I have never like wine solutions. I've never tried Macromedia Studio MX 2004 or Dreamweaver, so I not much help. 

Good luck !

---

### Post by handy on 2006-01-05
Well I succumbed to the lure of Wine, without chroot, & installed it using this technique courtesy or **RAOF**:

**Quote:**
**========================**

I know how to get cedega working, with just one flaw...

On the other hand, it looks like I've got wine working at least. If you just grab the i386 breezy binary debs from **[http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)**, you can install them using

**sudo dpkg -i --force-architecture <thingy.deb>**

. Actually, if you can find a cedega .deb, the same trick may work.
**=======================**

The installation was painless, I then installed & used the latest WineTools to setup Wine:

**[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)**

WineTools allows you to install a lot of windows system files, fonts & others, this takes a while to download & install, it did complain  (often) about something inconsequential to do with localisation.  Apart from that it handled 64bit well.

I made the mistake of installing iexplorer with WineTools, it makes a mess of the screen when you load DVDshrink.  I will probably have to uninstall Wine & reinstall it again to get rid of iexplorer.  I could go into the registry but this software doesn't need me screwing around in the registry.  It needs all the help it can get.

I installed "Total Commander" in Wine, it works OK, there is really very little use for it in Wine, so I will uninstall it.  Google Earth doesn't work for me :( 
DVDshrink doesn't either, it is only 1 step away though, I think I will persevere with that one.
X-Lite installed & setup, I haven't got around to testing it yet.
DVDshrink is the one I want, anything else is just a bonus.

I'll let you know how it goes.

handy

---

### Post by handy on 2006-01-08
I had problems & ended up having a look at the 32bit Breezy just out of interest, having never run the 32bit version.  I wrote a bit of a rave about the experience, if your interested it's here:

[http://ubuntuforums.org/showthread.php?t=113788](http://ubuntuforums.org/showthread.php?t=113788)

Cheers,

handy

---

