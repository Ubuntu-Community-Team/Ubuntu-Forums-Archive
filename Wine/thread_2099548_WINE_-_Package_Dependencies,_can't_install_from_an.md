---
title: "WINE - Package Dependencies, can't install from anywhere"
date: 2012-12-29
forum: Wine
---

### Post by SamD92 on 2012-12-29
Running Ubuntu 12.10 64-bit
on the following system:
Core i5-2500k @ 4ghz
8GB DDR3-1600 RAM
1TB HDD, dual booting Win 7 and Ubuntu
XFX Radeon HD 6870


I'm trying to install wine so I can run the Reaper DAW. I've tried working with Ardour but I can't even get sound from my m-audio mobile pre, and the UI doesn't really appeal to me.

Anyway, on to the first and main issue.
Every single time I try to install wine, no matter what I've done, it comes up with this package dependency error.

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

I've also tried it through Terminal with similar results.

And occasionally "The application Ubuntu Software Center has experienced an internal error."
when I try through software center.

So far my experience all around with Ubuntu has been very buggy, I'll boot sometimes and it says I'm in low graphics mode and no matter what I do nothing happens and I have to restart until it works.

Anyway, that's another thread all together. I'm just tired of beating my head against a brick wall trying to get WINE to work.

After that I'll try on my own for a while to get my audio interface to work before I take up more forum space.

---

### Post by dino99 on 2012-12-31
install wine1.5 from the ppa (search "ubuntu wine ppa")

---

