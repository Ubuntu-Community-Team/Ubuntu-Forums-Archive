---
title: "apt-get for i686"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by gga73 on 2008-01-06
I guess the title says it all.  One of the annoying things about my 64-bits ubuntu box, is that I am unaware of how can I trick apt-get to retrieve 32-bits packages (libraries mainly) and place them into /usr/lib32.

The main 64-bits repositories have the basic ia32 libraries but I'm looking to install other 32-bits libraries for development (say, boost) and have apt-get also upgrade them together with my 64-bits libs (so both the 32-bits and 64-bits libs are always in sync).

I'm also trying to avoid the hassle (and disk waste) of installing a chroot environment.

Is there any way to do it?

---

### Post by Kilz on 2008-01-06
> **gga73 said:**
> I guess the title says it all.  One of the annoying things about my 64-bits ubuntu box, is that I am unaware of how can I trick apt-get to retrieve 32-bits packages (libraries mainly) and place them into /usr/lib32.

The main 64-bits repositories have the basic ia32 libraries but I'm looking to install other 32-bits libraries for development (say, boost) and have apt-get also upgrade them together with my 64-bits libs (so both the 32-bits and 64-bits libs are always in sync).

I'm also trying to avoid the hassle (and disk waste) of installing a chroot environment.

Is there any way to do it?

search for getlibs

---

### Post by macaholic on 2008-01-06
[Here]("http://ubuntuforums.org/showthread.php?t=474790") is the thread about getlibs.

---

### Post by gga73 on 2008-01-07
Thanks, it is a nice work-around.

It handles at least half of what I wanted.

I take it there's no way to have apt-get manage 32-bit updates automatically then?

---

### Post by Cappy on 2008-01-07
> **gga73 said:**
> 
I take it there's no way to have apt-get manage 32-bit updates automatically then?

There's not. ```
getlibs --upgrade
``` will be an option in the near future. Logging, removal of libraries, and upgrading libraries are all in the same category.

Unfortunately, that will still be a manual upgrade. There isn't any way to do it automatically unless you had the 64-bit library installed and apt-get would check with getlibs everytime it installed a library to see if that 32-bit library was installed. What a pain.

In short, there's nothing you can do right now but run getlibs on that package/library again if you know there is an upgrade.

---

