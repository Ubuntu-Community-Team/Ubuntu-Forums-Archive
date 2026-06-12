---
title: "Sudo apt-get can't find Fluxbox"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frank65 on 2006-04-11
Man, I just don't give up, do I?

I downloaded Fluxbox again... thought I'd take another stab at it. I got the file from fluxbox.org and is the latest development version 0.9.15.1.

I used the Archive Manager to extract the files and specified for it to go in my home folder. And there it sits, fat dumb and happy.

At this point I tried **sudo apt-get install fluxbox-0.9.15.1**. The terminal returns:
  [B]  Reading package lists... Done
    Building dependency tree... Done
    E: Couldn't find package fluxbox-0.9.15.1[/B]

Before I start fiddling with some Linux vital organs and screw things up again, I thought I'd leave things alone for right now and ask the experts. Can to steer me in the right direction from here?

Thanks.

---

### Post by Rxke on 2006-04-11
I'm a bit confused with what you want to do... 

apt-get install installs stuff that's in the repositories, like your installdisk and the official, etc. package collections online, so ```
sudo apt-get install fluxbox
``` Note: that's *without* the version number... Would install the (latest) fluxbox version (and possible dependencies) that is 'officially' supported by Ubuntu. Probably not as 'fresh' as 0.9.15.1, but then at least you'll be sure it works...

(FWIW: I've got the 6.06 testing version running, and there it is .9.14-1)

---

### Post by linear on 2006-04-11
What you have there is source code, and if you're committed to the newest fluxbox you'll need to compile it.
 
Suggested reading: [CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware") and [CompilingEasyHowTo]("https://wiki.ubuntu.com/CompilingEasyHowTo")
 
You'll need the **build-essential** package for sure; I'd also recommend **checkinstall** (lets you build a package for easy removal at the same time you install).
 
Or you could stick to the current supported version...

---

