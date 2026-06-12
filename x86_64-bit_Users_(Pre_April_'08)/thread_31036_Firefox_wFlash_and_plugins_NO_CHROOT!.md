---
title: "Firefox w/Flash and plugins NO CHROOT!"
date: 2005-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ShavedApe on 2005-05-01
forgive me if this is old news and i missed it

I tried so hard to compile a 32bit firefox on amd_64 ubuntu with no luck.

The installation made from the firefox installer on an i386 ubuntu install runs on my ubuntu amd_64 install, and uses 32bit plugins.
as a Kubuntu user, i no longer need gnome support either.

I had ubuntu_i386 running previously, and had my ~/lib/ directory backed up. so i just copied over ~/lib/mozilla-firefox/ and it runs fine (i think it's faster than with the gnome integration too)

if someone wants to try, you can probably install a 32bit chroot ([http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575))
then download and run the firefox installer in the chroot. re-name the directory mozilla-firefox and copy to where you want it.

i still get some locale errors, but it runs great.

someone better versed at this should make a 32bit package for firefox that installs on amd_64

---

### Post by ShavedApe on 2005-05-01
it turns out this was a fine ballancing act that i couldn't keep up :)

lost java, tried to get it working again, but never got futher than it loading the plugin and craching when an applet ran.

all of a sudden it's complaining about pango libraries, and not being able to open them.
playing with java versions shouldn't have affected this, but......

oh well, if anyone else has luck this way let me know

---

