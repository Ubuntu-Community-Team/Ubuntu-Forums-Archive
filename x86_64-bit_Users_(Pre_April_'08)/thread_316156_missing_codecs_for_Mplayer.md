---
title: "missing codecs for Mplayer"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by juah on 2006-12-10
Downloaded from

[http://ubuntu.moshen.de/dists/edgy/multimedia/](http://ubuntu.moshen.de/dists/edgy/multimedia/)

and installed

sudo dpkg -i mplayer-skins_2-6_all.deb
sudo dpkg -i mplayer_1.0-rc1-0.0raof1_amd64.deb

Works well with 64-bit Firefox and MediaPlayer Connectivity (wma and wmv9)

issue #1:

Should this work with mozilla-mplayer plugin, wasn't successful with that.

issue #2:

Ran into some nasty win codecs: got these from the command line

Requested audio codec family [wma9spdmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wma9spdshow] (afm=dshow) not available.
Enable it at compilation.


Can I enable these easily without compiling...

---

### Post by pay on 2006-12-10
> **juah said:**
> Ran into some nasty win codecs: got these from the command line

Requested audio codec family [wma9spdmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wma9spdshow] (afm=dshow) not available.
Enable it at compilation.


Can I enable these easily without compiling...
No compilling wouldn't fix the problem as they are win32 binary codecs, hence you would need the 32bit version of mplayer to play them. You could always convert them to another more friendly format

---

### Post by juah on 2006-12-10
Thanks for encouragement ;) . At least it seems I haven't misinstalled the player (?) The RAOF Mplayer seems to handle easily wmv9 and some wma-files as well (wma2). That is why I thought all the usual win32 codecs be available.

---

