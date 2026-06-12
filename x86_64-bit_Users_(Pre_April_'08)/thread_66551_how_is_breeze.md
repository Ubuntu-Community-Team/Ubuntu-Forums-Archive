---
title: "how is breeze"
date: 2005-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2005-09-17
Hy:
I tried the Hoary 64 version when it came out, but I ran into too many problems I wonder if any of you have tried Breese and would like to have some feedback to what you expirienced.

---

### Post by Laerte Andrade on 2005-09-17
Well, two weeks ago I've installed Breezy Colony CD 4 for a friend who had just bought a computer at work. Most of the main components are running just fine, and the hardware detection was flawless. However, I've had a lot of trouble installing the particular software she has to use, like data reduction facilities for astrophysics (ESO-MIDAS and IRAF). They require some old libraries (like [libc5](http://packages.ubuntu.com/breezy/oldlibs/libc5) for example) that are easy to find under the x86 version, but are not available for the AMD64 version. 

Anyway, my first impression was really good. It is much better than the Hoary version, that's for sure. A minor(?) nitpick: I prefer the old version of Nautilus, without the browser-like feeling.

---

### Post by Kuolio on 2005-09-18
My breezy is working like a charm, not that big improvement from Hoary though. I've noticed some minor usability changes, but nothing "OH MY GOD, THIS IS SO GREAT" experiences yet.

Well, hmm.. as nothing broke down for me, and things work the same or little better than in Hoary, i'd say "go for it" if asked about wether to install Breezy or not.

---

### Post by tonym on 2005-09-19
The main thing that stopped me from using hoary AMD64 was that I couldn't get OpenOffice to print.  That seems to be fixed in breezy and I've been using since the preview release without problems.

---

### Post by FluffyElmo on 2005-09-19
How are you installing Breezy? Is it safe to do a dist-upgrade now or do you have to start with a clean install? I'd tried it a month or two ago and beat a hasty retreat back to Hoary due to X issues. Liked what I saw though and would like to give it another go...

---

### Post by Kuolio on 2005-09-19
I tried dist-upgrade 1st, but as i had quite many "customisations" going with unofficial repositories, hacks, tweaks and such, it borked the system. Ended up doing a clean breesy preview install and it all went fine, with no complaints or errors.

So.. if you have tweaked your system alot, or have lots of unofficial repo's stuff, then I think clean install is the right way to go.

---

### Post by DancingSun on 2005-09-19
I have a separate partition for "/home", if I were to do a clean install of Breezy, how would I go about it?

Do I just select the "/" partition for installation? Will I lose the contents in the "/home" partition?

---

### Post by mlomker on 2005-09-19
> 
Do I just select the "/" partition for installation? Will I lose the contents in the "/home" partition?

Yes, no problem...just tell it to reformat /.  That is how my system is set up.  Do yourself a favor in case you have to roll back--tar your /etc directory and save it to your /home before you upgrade.

---

### Post by wmcbrine on 2005-09-19
[QUOTE=Laerte Andrade]They require some old libraries (like [libc5](http://packages.ubuntu.com/breezy/oldlibs/libc5) for example) that are easy to find under the x86 version, but are not available for the AMD64 version.[/quote]Try a 32-bit chroot environment for these.

> *A minor(?) nitpick: I prefer the old version of Nautilus, without the browser-like feeling.*Browser mode is an option in Hoary. I'd guess it's also an option in Breezy, just turned on by default. (?)

---

### Post by tikal26 on 2005-09-20
thanks foryou replies, I guess it does not hurt to give it a try

---

