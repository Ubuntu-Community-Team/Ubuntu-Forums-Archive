---
title: "What will Crossover buy me?"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2007-05-08
I have been playing with 64 bit Ubuntu for the last six months and have never been able to get multi-media working completely under either Dapper or now Feisty.  I have done everything I can find on the forum: ran Kilz script to install 32 bit Firefox, install and run Automatix2, and add the Mediubuntu repositories, worked through the tutorial on adding multi-media to Feisty.  All this stuff seems to run without error but I still don't have w32codecs (nor can I find them) or get the flash plug-in to work in Firefox 32.  This is background now here is the question.

Automatix offers the capability to download and then buy the Crossover software which I believe allows you to run Windows plug-in, codecs and programs under WINE.  If I understood the Codeweavers website, this can be done legally without Microsoft licenses.  Will buying and installing Crossover allow me to build a 64 bit Ubuntu desktop upon which all the "normal" multi-media stuff will work?  All I am really looking for at this point is a "vanilla" desktop that will do what my XP desktop doesl only faster and with better security.

Thanks,
joe

---

### Post by scrooge_74 on 2007-05-08
WINE or Crossover will give you the ability to use certain software. I only use WINE for running games and Crossover to run my accounting program since it refuses to work under WINE anymore.  

Example, with WINE you need to manually install IE6, pluggins and such, with Crossover you click on the supported programs (like IE6) and they will install by themself.

I have read you can use the standard 32 bit version of Ubuntu on a 64 bit system, since it has more driver support and such.

I can do what XP does and faster without using WINE or Crossover by using the 32 bit version of Ubuntu and staying as far away as possible from Automatix2.

---

### Post by david_2001 on 2007-05-09
I can confirm that the standard 32-bit version of Crossover Linux certainly does work on Ubunutu amd64.  It just needs the ia32 compatibility libraries installed and the XLOCALELIBDIR environment variable set correctly.

Medibuntu has a w64codecs package for feisty but there's not much in it.  For flash player, mplayer with w32codecs etc. I just set up a 32-bit chroot.  This was very easy to do and also allows me to continue using my Epson Perfection 3170 Photo scanner, which relies on a proprietary 32-bit-only binary.

---

### Post by scrooge_74 on 2007-05-10
Glad to hear you have manage to get a work around on things

---

### Post by david_2001 on 2007-05-10
> **scrooge_74 said:**
> Glad to hear you have manage to get a work around on things

What I didn't realise until yesterday was that feisty's 64-bit version of mplayer plus the Medibuntu w64codecs package has everything I need, including the real codec.  I haven't tried nspluginwrapper yet, so I still only have flash player working in 32-bit firefox.  Actually, though, I prefer using the chroot because it keeps 32-bit and 64-bit neatly separated.

---

