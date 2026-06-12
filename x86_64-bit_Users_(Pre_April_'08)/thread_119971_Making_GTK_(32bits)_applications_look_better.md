---
title: "Making GTK (32bits) applications look better"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by awi on 2006-01-20
Hi, I've made "Firefox 1.5 (32bits)" work, thanks to this howto 

[http://www.ubuntuforums.org/showthread.php?t=90106](http://www.ubuntuforums.org/showthread.php?t=90106)

the same procedure works for thunderbird 1.5. 
What I've noticed was that the widgets (radio buttons, scroll bars, buttons, etc.) looks almost all of them without borders, or sometimes not even distiguishable.
Searching through google, I found on debian's AMD64 list, a short tutorial to make Acrobat 7.0 work, and wanted to try myself to eliminate the warnings that printed out the "firefox32" script.

I also made an archive 

```
/etc/gtk32-init
```

that way is easier to maintain, in case that I have to change or add some more lines to the initialization part, to run linux32 apps.
The content of the [FONT="Courier New"]/etc/gtk32-init[/FONT] so far is:

```
GTK_PATH=/usr/lib32/gtk-2.0

PANGO_RC_FILE=/etc/pango32/pangorc
GCONV_PATH=/usr/lib32/gconv
LD_PRELOAD=/usr/lib32/libpangohack.so.0.0
GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders32
export GTK_PATH PANGO_RC_FILE GCONV_PATH LD_PRELOAD GDK_PIXBUF_MODULE_FILE
```

Combining the information on the howto and the one found in this thread:
[http://lists.debian.org/debian-amd64/2005/05/msg00707.html](http://lists.debian.org/debian-amd64/2005/05/msg00707.html)

That reduces the howto's script  to this:

```

#!/bin/sh

. /etc/gtk32-init

linux32 /usr/local/firefox32/firefox $@ &
```


I stil got some minor output:
```

ERROR: ld.so: object '/usr/lib32/libpangohack.so.0.0' from LD_PRELOAD cannot be preloaded: ignored.
(firefox-bin:18025): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:18025): Gdk-WARNING **: cannot set locale modifiers
```

But no doubt that this procedure makes my firefox32 and thunderbird32 look a lot better.

I have a custom gnome theme too, and that made my Open Office apps look exactly as ugly as my two mozillas apps, so I also added this to the first non commented line of

[FONT="Courier New"]/usr/lib/openoffice2/program/soffice[/FONT]

```
--- BEGIN of line added
. /etc/gtk32-init
--- END of line added

```


which is the last script (bash) called, to execute any of the office suite programs, and this way I got the same result as with the Mozillas', a better and more confortable look.
Regards

Awi

---

