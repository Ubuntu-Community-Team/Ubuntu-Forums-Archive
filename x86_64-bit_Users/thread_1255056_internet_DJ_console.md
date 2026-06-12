---
title: "internet DJ console"
date: 2009-09-01
forum: x86 64-bit Users
---

### Post by shadow mosis on 2009-09-01
i was trying to install it but i got this at the end of it...

The following packages have unmet dependencies:
  openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b14-1.4.1-0ubuntu11) but it is not going to be installed
                 Recommends: ttf-wqy-zenhei but it is not installable
                 Recommends: ttf-telugu-fonts but it is not installable
                 Recommends: ttf-oriya-fonts but it is not installable
                 Recommends: ttf-kannada-fonts but it is not installable
                 Recommends: ttf-bengali-fonts but it is not installable
E: Broken packages

i tried installing Opednjdk but i cant do that because i get the conflicting software error and honestly am starting to regret getting ubuntu, i just not that skilled in using it :confused:.... if some one could help me i would really appreciate it....thank you..

---

### Post by bobince on 2009-09-01
How are you trying to install it? From Ubuntu repos? It's best to [compile idjc yourself](http://www.onlymeok.nildram.co.uk/download.html): the version in Ubuntu is really old and doesn't support MP3 properly (due to legal shenanigans).

The error appears to be a general-purpose wedged dependency; you can get in this sort of state when you've got a corrupted package download, installed things from clashing repositories, or someone at Debian or Ubuntu messed up (which thankfully doesn't happen as often as it used to). Try marking all packages connected to openjdk or Java in general for removal then updating.

(It's nothing to do with idjc, which does not use Java of any kind. You'll probably get that error trying to install anything now your deps are wedged.)

---

### Post by shadow mosis on 2009-09-04
thanks for helping me, i tried doing it through a terminal... im just having a hard time learning how to use and understanding ubuntu...thanks for your help...

---

