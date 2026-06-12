---
title: "Removing Evolution/Empathy from 9.10 prevents boot"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by matchrocket on 2009-11-01
So, I upgraded to 9.10, which went very very smooth.  After a few days of running I decided to remove, again, evolution and the newly install empathy.  I don't use either and didn't see the need to have them installed.

I removed them via the package manager, marked for complete removal and rebooted.   When the system came backup, gdm loads, you get the new ubutu logo and load bar, then something strange happens....

I just get a terminal window in the upper left and nothing else. You can launch some graphical configuration apps (nvidia-config for example), but the main desktop won't load.  I have tried reinstalling both applications, and doing a re-configure of gdm, no dice.  KDE also wont load and acts the same way.  Even tried re-installing gdm.

Are these two apps so deeply integrated into 9.10 that I have totally hosed my system?

---

### Post by gerben1 on 2009-11-02
I have had a similar problem about a year ago. As you can read here:
[http://ubuntuforums.org/showthread.php?t=784388](http://ubuntuforums.org/showthread.php?t=784388)

In my case it was solved by reinstalling the ubuntu-desktop package:
```

sudo apt-get install ubuntu-desktop

```

---

### Post by BuffaloX on 2009-11-03
I want to get rid of evolution too.
I got the exact same problem.
Seems the new notifier is tied to evolution somehow.
Well have to get rid of that too then, but don't know how.

Evolution is probably great for office work and such, but total overkill for me. I use thunderbird.

---

### Post by wojox on 2009-11-03
You can get rid of evolution, just leave evolution-data-server-common and evolution-data-server alone.

---

### Post by BuffaloX on 2009-11-03
Didn't work for me.
libebook1.2-9 removes evolution-data-server
and if I reinstall evolution-data-server it still won't boot into Gnome.

I still get the small terminal window.
Had to restore by sudo apt-get install ubuntu-desktop.

---

### Post by lswb on 2009-11-03
I haven't installed 9.10 yet (I think I'll wait til they've fixed some of the bugs in 9.04 1st :) ) but the same sort of thing has happened with earlier releases. If the same pattern exists in 9.10, this may help.

Install ubuntu-desktop to bring back all your gui stuff. ubuntu-desktop is a "virtual package" which means it depends on lots of other packages but contains no programs itself. Once ubuntu-deskop has finished installing, you can then uninstall it. The packages installed along with it will not be removed, but they can now be uninstalled individually without uninstalling the whole desktop. (No gurarantee, but this worked in 9.04 and earlier versions for me)

---

### Post by BuffaloX on 2009-11-03
That still works, that's how I got my system back.

---

