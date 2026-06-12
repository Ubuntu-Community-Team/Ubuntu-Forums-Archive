---
title: "[WIne] How do I remove Wine COMPLETELY!"
date: 2013-02-10
forum: Wine
---

### Post by ksaul on 2013-02-10
I installed Wine 1.5 (or tried to..) yesterday in attempt to be able to use Adobe After Effects on my Ubuntu x86 machine.. I followed some How-To "patch" Wine to run 64bit applications.. well it did not work and now I cant even install/run normal applications.

[url=http://wiki.winehq.org/Wine64]WoW64 / Win64 on Precise[/url (winehq)
[the patch guide I used](http://forums.ddo.com/showthread.php?t=399395) (unofficall)

How do I completely un-do everything that the above link had me do (safely) and remove wine, winetricks and all configurations so I can start from scratch and have a working Wine again?

> 
sudo apt-add-repository --remove ppa:ubuntu-wine/ppa
sudo apt-get --purge remove wine*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine3264
E: Unable to locate package wine64
E: Unable to locate package wine-git

---

### Post by Bufeu on 2013-02-10
> **ksaul said:**
> I installed Wine 1.5 (or tried to..) yesterday in attempt to be able to use Adobe After Effects on my Ubuntu x86 machine.. I followed some How-To "patch" Wine to run 64bit applications.. well it did not work and now I cant even install/run normal applications.

[url=http://wiki.winehq.org/Wine64]WoW64 / Win64 on Precise[/url (winehq)
[the patch guide I used]("http://forums.ddo.com/showthread.php?t=399395") (unofficall)

How do I completely un-do everything that the above link had me do (safely) and remove wine, winetricks and all configurations so I can start from scratch and have a working Wine again?This should work fine:```
sudo apt-get purge wine* ; sudo dpkg --purge wine*
```

---

### Post by ksaul on 2013-02-10
> **Bufeu said:**
> This should work fine:```
sudo apt-get purge wine* ; sudo dpkg --purge wine*
```

i tried..

> sudo apt-get purge wine* ; sudo dpkg --purge wine*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine3264
E: Unable to locate package wine64
E: Unable to locate package wine-git
dpkg: warning: there's no installed package matching wine3264
dpkg: warning: there's no installed package matching wine64
dpkg: warning: there's no installed package matching wine-git


i also tried

> 
 sudo ppa-purge ppa:ubuntu-wine/ppa
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Package revert list generated:
 wine1.5/precise wine1.5-amd64/precise wine1.5-dbg/precise wine1.5-dev/precise 
wine1.5-i386:i386/precise wine-gecko1.9/precise wine-gecko1.9:i386/precise 
wine-mono0.0.4/precise wine-mono0.0.8/precise winetricks/precise

Disabling ubuntu-wine PPA from 
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'precise' for 'wine1.5' was not found
E: Release 'precise' for 'wine1.5-amd64' was not found
E: Release 'precise' for 'wine1.5-dbg' was not found
E: Release 'precise' for 'wine1.5-dev' was not found
E: Release 'precise' for 'wine1.5-i386:i386' was not found
E: Release 'precise' for 'wine-gecko1.9' was not found
E: Release 'precise' for 'wine-gecko1.9:i386' was not found
E: Release 'precise' for 'wine-mono0.0.4' was not found
E: Release 'precise' for 'wine-mono0.0.8' was not found
Unable to find an archive "precise" for the package "wine1.5"
Unable to find an archive "precise" for the package "wine1.5-amd64"
Unable to find an archive "precise" for the package "wine1.5-dbg"
Unable to find an archive "precise" for the package "wine1.5-dev"
Unable to find an archive "precise" for the package "wine1.5-i386:i386"
Unable to find an archive "precise" for the package "wine-gecko1.9"
Unable to find an archive "precise" for the package "wine-gecko1.9:i386"
Unable to find an archive "precise" for the package "wine-mono0.0.4"
Unable to find an archive "precise" for the package "wine-mono0.0.8"
Unable to find an archive "precise" for the package "wine1.5"
Unable to find an archive "precise" for the package "wine1.5-amd64"
Unable to find an archive "precise" for the package "wine1.5-dbg"
Unable to find an archive "precise" for the package "wine1.5-dev"
Unable to find an archive "precise" for the package "wine1.5-i386:i386"
Unable to find an archive "precise" for the package "wine-gecko1.9"
Unable to find an archive "precise" for the package "wine-gecko1.9:i386"
Unable to find an archive "precise" for the package "wine-mono0.0.4"
Unable to find an archive "precise" for the package "wine-mono0.0.8"

---

### Post by Bucky Ball on 2013-02-10
*Thread moved to **Wine**.*

When I first started using Ubuntu in 2007 I installed it, for no reason that I can remember, and found I couldn't get every trace of it out of the machine. Must be a Windows thing because I remember how hard it could be to uninstall some things you didn't want in Win, too. The main program would be gone but you would be left with its 'mushroom spores' scattered about.

Good luck. I didn't succeed in eradicating Wine fully.

---

### Post by offgridguy on 2013-02-10
Like the OP i never had success at installing or using wine,  I tried the commercial version called crossover, got it installed
but could never get it to work either.
    Since I have windows I never use wine, it was just an experiment that didn't work.  However i see that the ubuntu christian edition comes with wine and wine tricks pre-installed, i
wonder if that makes a difference ?  I haven't tried it myself.

---

### Post by CK000 on 2013-06-10
Hello I ran the code in the second post and it is STILL running! It has already begun to purge and remove almost everything from my computer. What is going on and have I may an awful mistake? Perhaps this code was wrong? I'm sorry for any confusion I am in a panic as my whole computer seems to have changed!!

---

### Post by Bucky Ball on 2013-06-10
That command should not have changed your system, just removed Wine (or most of it). Did you copy/paste the commands in? If not, you may have made a mistake in translation.

You would have a better chance of assistance if you post a new thread with a title more appropriate to your problem, and include the command you used in your post. This thread hasn't seen action for three months and although you're trying to remove Wine, your actual issue is unrelated to the thread title here. 

PS: If the computer is not doing anything, just sitting there at a desktop, have you tried rebooting it then doing and update? As I mentioned previously, uninstalling *all* of Wine I found to be pretty much and impossibility. If I ran 'locate wine' in a terminal it always found something. Haven't touched it since 2007.

---

### Post by CK000 on 2013-06-12
Thank you for your time and your assistance. 

I did indeed copy and paste the command, but it no longer matters at least to me.

I decided to do a fresh install which obviosuly deleted everything. However I had backups of my home folder so all is well.

I assume provided I don't actually run WINE there should be no issue leaving it there now? Please move this thread if necessary.

Thank you once again and my apologies if this reply is in the wrong place.

---

