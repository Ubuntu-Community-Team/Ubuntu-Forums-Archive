---
title: "firefox 1.5.0.1"
date: 2006-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ssam on 2006-02-10
hello

i have build firefox 1.5.0.1 for all you eager badgers.

you can download it from [http://tygier.co.uk/pub/firefox-1.5.0.1.en-US.linux-powerpc.tar.gz](http://tygier.co.uk/pub/firefox-1.5.0.1.en-US.linux-powerpc.tar.gz)

to install it you need to unpack it somewhere (/opt/firefox-1.5.0.1 is a good choice) and set up symlinks in your /usr/bin. if you need proper instructions see [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) (they also detail backing up the profile and things)

this works for me, and fixes a few bugs from 1.5. i can't guarantee that it will work for you.

it was built with the following mozconf

```
. $topsrcdir/browser/config/mozconfig
# Options for 'configure' (same as command-line options).
ac_add_options --enable-application=browser
ac_add_options --enable-optimize
ac_add_options --disable-tests
ac_add_options --disable-official-branding
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-xft
ac_add_options --disable-freetype2
ac_add_options --enable-svg
ac_add_options --enable-canvas

CC=/usr/bin/gcc-3.3
CXX=/usr/bin/g++-3.3

```

and the following commands in the unpacked source directory.

```
export MOZCONFIG=/home/sam/mozconfig
make -f client.mk build
make -C browser/installer

```

please post any problems.

sam

---

### Post by Xumbi on 2006-02-11
Thanks ssam!  I was hoping someone would compile 1.5.0.1 and package it up.  I followed the wiki guide and I'm posting this "Deer Park" 1.5.0.1 on my iBook 800MHz running Breezy!

---

