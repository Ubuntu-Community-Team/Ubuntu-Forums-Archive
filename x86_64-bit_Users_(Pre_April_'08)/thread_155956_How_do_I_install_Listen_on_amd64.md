---
title: "How do I install Listen on amd64?"
date: 2006-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xilon on 2006-04-06
I tried a few times, installing from source, from the deb (which is i386) and also through the repositories (which don't seem to work). I'm a newb as far as Linux goes atm, but I tried *make*ing Listen and I got a few errors with dependencies missing (pygtk-devel), which I was unable to install.

Here's what I get when I try to *make* it again
```

Checking for Python... /usr/bin/python
Checking Python version: 2.4
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6
not found
Listen requires pyGTK-devel
make: *** [check] Error 1

```
There are no "pygkt*" packages in the repo, I tried installing python-dev_2.4.2-0ubuntu2_all which didn't help either. python-gtk2-dev has heaps of dependencies so I don't really want to install that unless that is what is required.

---

### Post by skylark on 2006-04-07
I'm not familiar with Listen at all (in fact I don't even know what it is).

Maybe to get that python stuff installed though, try from a command line: ```
apt-cache search pygtk
``` This lists some possible candidate packages. For example python-gnome2-dev and python-gtk2-dev. You can get more info on these packages: eg ```
apt-cache showpkg python-gtk2-dev
```. I'm not which you need but hopefully one or the other will let you finish compiling Listen. If you provide a link to where Listen is I'll also have a shot at compiling it if you want.

---

### Post by skylark on 2006-04-07
Ahh I finally found what listen was. [http://listengnome.free.fr/](http://listengnome.free.fr/)

Yeah looks like there is a 32-bit dapper apt source but the breezy one is out of date (and probably no 64-bit, but I might have missed it). So building from source looks like the only option for you at the moment.

However looking at the build requirements, it might need packages more recent than what is available in Breezy. You might potentially have to try out Dapper to get the latest version of Listen working! I'll try and look into building it myself tomorrow (no time right now), and let you know how it goes.

---

### Post by Xilon on 2006-04-09
Since I'm pretty new to linux I'm not too keen on upgrading the distro to an unstable one, but Dapper seems to have HEAPS of benefits so I might try it out... I want to use XGL anyway ;)

---

### Post by eladamri on 2006-06-12
I tried this for a while yesterday and had success after a couple hours.

First, I naievely tried using the package manager as per [http://ubuntuforums.org/showthread.php?t=156547]("http://ubuntuforums.org/showthread.php?t=156547"). By adding ```
deb http://theli.free.fr/packages/dapper/ ./ 
``` to my sources.list. Apt-get would not find Listen.

I then tried building from source for a while resulting in failure even after I had all of the dependencies.

What finally worked in the end was installing via the .deb file. I simply downloaded it and ran ```
sudo dpkg -i --force-architecture listen_0.4.3-1_i386.deb
```

I am now happily running Listen on my AMD64.

It really is a pretty impressive program. If you like Amarok, but are equally annoyed by it then you'll love Listen.

---

### Post by Horgrathi on 2006-07-09
[My Question Was Solved]

---

