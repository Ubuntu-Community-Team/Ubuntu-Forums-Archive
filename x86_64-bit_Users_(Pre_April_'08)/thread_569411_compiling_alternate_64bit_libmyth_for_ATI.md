---
title: "compiling alternate 64bit libmyth for ATI"
date: 2007-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by fcollman on 2007-10-07
I'm trying to get mythtv setup on my new machine which has an ATI x1900 xtx graphics card and a pcHDTV 5500.  I've got everything working, except for that I'm getting the blue tint on everything that people have experienced.

The only solution i've seemed to find on this (save not using any real driver at all which seems just silly) is to use a recompiled version of libmyth... and someone has provided one on launchpad, but its been compiled for 32 bit.  (this fix is described here)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/73102](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/73102)

seems this has worked for a number of people.... but I wanted to try to get it working on a 64 bit kernel.  I've tried downloading the source from 
[http://packages.ubuntu.com/feisty/source/mythtv](http://packages.ubuntu.com/feisty/source/mythtv)

and recompiling it myself with the fix to the one sourcefile as described.

I had to download a bunch of developer's libraries to get through the ./configure and make steps.

I did make install... and it seemed to work, but the problem wasn't solved.

I'm a bit of a newbie.. so I was wondering if I did something wrong... like for instance I didn't really have to specify that this was a 64 bit version... so perhaps the libraries didn't go into the right place etc...

does anyone have mythtv working with ATI drivers on a 64 bit system?

---

