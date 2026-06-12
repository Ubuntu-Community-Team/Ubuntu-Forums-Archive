---
title: "64bit worth it?"
date: 2006-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by OptimusPrime on 2006-10-25
So, is it worth using the 64bit version of Ubuntu? I do right now, but it is really hard to do some things with it.  Is it possible to install 32bit on a 64bit?

---

### Post by TheWizzard on 2006-10-26
> **OptimusPrime said:**
> So, is it worth using the 64bit version of Ubuntu? I do right now, but it is really hard to do some things with it.  Is it possible to install 32bit on a 64bit?

if you have an amd64 i would advice you to install the 32 bit ubuntu and install the k7 kernel. search for "linux-image" in your package manager.

---

### Post by FewClues on 2006-10-29
> **TheWizzard said:**
> if you have an amd64 i would advice you to install the 32 bit ubuntu and install the k7 kernel. search for "linux-image" in your package manager.

I am at a loss!  I'm running 6.06 LTS   2.6.15-27-amd64-generic and have had no problems with any application.  What are some of the programs you are having problems with using 64bit?

---

### Post by prs on 2006-10-29
I'd say go for the 64-bit version - there are very few applications that I have to run in 32 bit mode (e.g. wine and flash with firefox32) but otherwise it works flawlessly for me.

---

### Post by Garf on 2006-10-29
> **prs said:**
> I'd say go for the 64-bit version - there are very few applications that I have to run in 32 bit mode (e.g. wine and flash with firefox32) but otherwise it works flawlessly for me.

I'm gonna install 64 bit Ubuntu in a few days (when my new computer arrives)... Can you outline what you have to do to get it to use Firefox and flash 32? Do you have to install a different Firefox? Or even have two?

Thanks...

---

### Post by incubus on 2006-10-30
Check the sticky thread in this section of the forum.  If it's not there, look for Kilz's signature.  He created a firefox32 package for us, 64bit users.  It works flawlessly and I'm writing using it right now.  It's got Flash and all other fancy things.

I've been using Ubuntu 64bit for months now and can't complain.

incubus

---

### Post by incubus on 2006-10-30
Here it is:
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

incubus

---

### Post by hajk on 2006-10-30
> **incubus said:**
> Here it is:
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

incubus

I also want to mention the possibility of installing 32-bit packages in a 32-bit chroot environment, it isn't all that difficult to do (see the Ubuntu Wiki page DebootstrapChroot). I think you should read up on both possibilities before deciding for yourself, despite the outspoken opinions against chroot by some people on this forum. I, for one, prefer the chroot because using it for 32-bit packages is a piece of cake once the initial bother of the setup has passed.

---

