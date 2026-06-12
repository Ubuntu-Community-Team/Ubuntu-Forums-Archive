---
title: "libSDL crap after COMPLETE REINSTALL"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by yodaky on 2006-08-25
I installed Ubuntu last night and had most things to my liking.  However, some how earlier today libSDL "disappeared" and when I tried to run MPlayer or Tremulous they wouldn't, stating it could not find libSDL-1.2.so.0

I have since re-installed my Ubuntu and the ONLY changes I made to my system before trying to run Tremulous where installing my nVidia drivers and installing lib32sound2 so CS:S will have sound.

Any idea what is wrong?  If I go to /usr/lib I can see the symbolic link it has made (I assume) to libSDL-1.2.so.0.7.2, or something like that.  I tried installing libSDL-1.2debian-all but that did not help :(

---

### Post by yodaky on 2006-08-25
OK, I was just reading a howto on getting w32codecs installed a 64 bit system and when I ran the command:

sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6

I noticed the ia32-libs-sdl and decided to try to run Tremulous again.  It worked.  Hopefully it will stay working this time :/

---

### Post by Kilz on 2006-08-25
> **yodaky said:**
> OK, I was just reading a howto on getting w32codecs installed a 64 bit system and when I ran the command:

sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6

I noticed the ia32-libs-sdl and decided to try to run Tremulous again.  It worked.  Hopefully it will stay working this time :/

The reason it worked after you installed the packages is Tremulous is a 32bit application. The package ia32-libs-sdl provides the 32bit libraries the 32bit application needs.

---

