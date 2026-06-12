---
title: "Desktop effects could not be enabled"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by ecolitan on 2009-05-01
Just reinstalled to x86_64 and cant turn on the desktop effects, it just gives a pop up box saying that "Desktop effects could not be enabled".

Im not sure what information to include in the post for some help with this, laptop is Inspiron 1525.

Any info or ideas would be most appreciated!!

---

### Post by Thelasko on 2009-05-01
What kind of graphics card does it have?

From what I've read, you likely have an Intel 3100.  This is normal behavior for that card.

---

### Post by ecolitan on 2009-05-01
It's a laptop with graphic Intel Inegrated GMA X3100.

Is there really no way to improve this behaviour? It worked with 32bit os but not anymore. I've looked for a driver but can't find anything that's any good.

Thanks!

---

### Post by Thelasko on 2009-05-01
> **ecolitan said:**
> It worked with 32bit os but not anymore.
That should not be the case.

Are you sure it was the same version of Ubuntu?  (other than 32 and 64-bit?)

Your graphics card has been blacklisted for desktop effects.  Enabling desktop effects may make your system unpredictable.  Did you override the blacklist on the 32-bit version?

---

### Post by ecolitan on 2009-05-01
Yeah, i had just upgraded to 9.04 but was only using 32 bit, i just downloaded today 9.04 64bit and installed. The desktop effects features were definatly working before the reinstall to 64bit. 

I asked some questions before the upgrade over here:

[http://ubuntuforums.org/showthread.php?t=1144223](http://ubuntuforums.org/showthread.php?t=1144223)

thanks..

---

### Post by Thelasko on 2009-05-01
The developers have been making changes to the Intel drivers recently.  They're trying to increase it's performance.  Unfortunately, some of the latest drivers aren't as stable as a result.  They might have blacklisted your card on Jaunty as a result.

I'm currently using Hardy Heron (8.04) on my desktop.  It has the desktop version of the Intel X3100 card.  From what I understand, the drivers are much more stable on Hardy than the releases afterwards.  This is because Hardy is an LTS release.  Unfortunately, even with these stable drivers, I'm only capable of the basic desktop effects.  I can't use any of the more advanced ones.

I've heard some people are using the Hardy drivers in Jaunty through a PPA.  You might want to consider that option.

This is not just a 64-bit issue, but a problem across all versions of Ubuntu.

---

### Post by boogers on 2009-05-01
> **Thelasko said:**
> The developers have been making changes to the Intel drivers recently.  They're trying to increase it's performance.  Unfortunately, some of the latest drivers aren't as stable as a result.  They might have blacklisted your card on Jaunty as a result.

I'm currently using Hardy Heron (8.04) on my desktop.  It has the desktop version of the Intel X3100 card.  From what I understand, the drivers are much more stable on Hardy than the releases afterwards.  This is because Hardy is an LTS release.  Unfortunately, even with these stable drivers, I'm only capable of the basic desktop effects.  I can't use any of the more advanced ones.

I've heard some people are using the Hardy drivers in Jaunty through a PPA.  You might want to consider that option.

This is not just a 64-bit issue, but a problem across all versions of Ubuntu.

Yah, Roll back your drivers.  Here check out this page...[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Also maybe this will help for working around blacklist: [http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

---

### Post by ecolitan on 2009-05-01
thanks for your help. this sounds very complicated. i guees i'll just leave it without the effects.

---

### Post by anibalojeda on 2009-05-07
> **ecolitan said:**
> thanks for your help. this sounds very complicated. i guees i'll just leave it without the effects.


Try this on a terminal

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager


log out & then enable your effects (try on own risk)

---

### Post by Xx.NaTo.xX on 2009-05-10
Hi everyone!!

i have the same issue. I've just updated from 8.04 to 9.04, and I get "Desktop effects could not be enabled" every time i try to change visual effects. it didnt happen with 8.04.

is there any way to go back to last drivers??

my computer is a Dell vostro 1400 with Intel Integrated Graphics Media Accelerator X3100.

Thx!!!

---

### Post by balboost on 2009-05-11
hi,

on inspiron 1525, as mine, there are lots of issues with intel chipsets. check this link if this might help you :

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

i choosed to stay with metacity + xcompmgr (to enable composite screen) until a saving update or karmic koala, as any of the solutions proposed worked for me.

good luck :)

---

