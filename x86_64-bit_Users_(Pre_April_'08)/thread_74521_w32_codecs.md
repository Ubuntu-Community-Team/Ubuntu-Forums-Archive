---
title: "w32 codecs"
date: 2005-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by luckyaba on 2005-10-11
Im trying to get the codecs working in 64 bit and i have them in /usr/local/lib/codecs. i try and play a file in amarok and it just skips right through them. how would i fix this?

---

### Post by gorod on 2005-10-12
Which backend does your amarok using? If gstreamer , have you got the approapriate plugin for that particular codec ? If xine-lib test if xine recognises your codecs. Is the path where you installed the codecs in /etc/ld.so.conf ? Did you ran ldconfig? Also what do you mean with w32 codecs? If you mean windows 32bit codecs then they wont work with amarok (unless you will compile it in 32bit). As for 64bit windows codecs then they are non existant at the moment. Even win64 uses 32bit codecs with 32bit media player.

---

### Post by DancingSun on 2005-10-12
gorod, have you been able to get win32codec to work in 64-bit Ubuntu?  Have you tried the pitfdll plugin for gstreamer?  I wasn't able to compile it from source.

---

### Post by gorod on 2005-10-13
You need 32bit gstreamer for that, which will not be compatible with 64bit gnome. You can forget it unless you install some dedicated program for use with win32 codecs like mplayer that i described in other thread or 32bit xine. The only thing i know works 64-32 is konqueror with 32bit plugins (originated in suse), here are detailed instructions [http://forums.gentoo.org/viewtopic.php?t=216959](http://forums.gentoo.org/viewtopic.php?t=216959)  which is abit pita unless you are an experienced user.

---

