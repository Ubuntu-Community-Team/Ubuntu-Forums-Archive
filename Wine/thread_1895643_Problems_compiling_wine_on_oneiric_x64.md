---
title: "Problems compiling wine on oneiric x64"
date: 2011-12-15
forum: Wine
---

### Post by Freek07 on 2011-12-15
I'd like to play Entropia Universe. Davvvvve reported it's working with doublebuffer patch ([http://bugs2.winehq.org/attachment.cgi?id=27310](http://bugs2.winehq.org/attachment.cgi?id=27310)).

The problem is I have x64 machine and "apt-get build-deps wine" goes well but when I configure (ubuntu's!) wine it needs a lot of other i386 stuff. For example, libfreetype6-dev:i386.

Installing libfreetype6-dev:i386 would remove gcc and replace it with gcc:i386 and remove a lot of other stuff as well...and I don't want to break my system.

So, I have two questions:
a) is there precompiled ubuntu x64 wine with doublebuffer patch?
or
b) how can I compile it without breaking my system? :(

---

### Post by ergo-proxy on 2011-12-16
I had no problem with compiling wine under oneiric x64, make sure you have wine ppa added. For 1.3* use ***sudo apt-get build-dep wine1.3.***
**** 
If you want just to compile wine without installing it in system just run:
 
./configure
make
 
and all required binaries are placed in the same directory. To add a patch check winehq faq

---

### Post by thatguruguy on 2011-12-16
Wine is a 32-bit program, even on a 64-bit system.  You can read why Wine is structured the way it is [here]("http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8").

That's why it brings in the 32-bit packages.

---

