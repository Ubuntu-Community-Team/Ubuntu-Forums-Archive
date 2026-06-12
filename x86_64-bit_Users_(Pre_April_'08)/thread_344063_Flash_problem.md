---
title: "Flash problem"
date: 2007-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by markus79 on 2007-01-22
Hi,

I'm having a problem installing Flash 9, despite all the helpful posts already.

I'm running a 32-bit version of Firefox with the help of this script /usr/bin/firefox32

```

#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox

```

From all the posts it looks like you should just copy flashplayer.xpt and libflashplayer.so into your plugins directory. I have so many plugin directories, and I've copied them to all, just in case, but I'm still having problems.

about:plugins in Firefox shows most of my plugins are in the /usr/lib/mozilla/plugins directory. The flash files are in this directory, but the about:plugins page doesn't show them.

I also have them in:

/home/mark/.mozilla/plugins
/home/mark/.firefox/plugins
/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins

But still no luck. Any ideas? Thanks

markus

---

### Post by markus79 on 2007-01-22
I downloaded this handy script and all my plugins worked!

[http://home.comcast.net/~next/base-plugins-browsers-0-6.tar.gz](http://home.comcast.net/~next/base-plugins-browsers-0-6.tar.gz)

---

### Post by Kilz on 2007-01-22
> **markus79 said:**
> Hi,

I'm having a problem installing Flash 9, despite all the helpful posts already.

I'm running a 32-bit version of Firefox with the help of this script /usr/bin/firefox32

```

#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox

```

From all the posts it looks like you should just copy flashplayer.xpt and libflashplayer.so into your plugins directory. I have so many plugin directories, and I've copied them to all, just in case, but I'm still having problems.

about:plugins in Firefox shows most of my plugins are in the /usr/lib/mozilla/plugins directory. The flash files are in this directory, but the about:plugins page doesn't show them.

I also have them in:

/home/mark/.mozilla/plugins
/home/mark/.firefox/plugins
/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins

But still no luck. Any ideas? Thanks

markus

The plugins for Firefox32 may be found in /usr/lib32/firefox32/plugins you may want to copy the plugin there.

---

