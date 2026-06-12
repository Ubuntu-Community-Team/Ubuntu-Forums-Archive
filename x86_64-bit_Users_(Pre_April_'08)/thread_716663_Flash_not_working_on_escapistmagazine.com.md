---
title: "Flash not working on escapistmagazine.com"
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by dandandan on 2008-03-06
For example:

[http://www.escapistmagazine.com/articles/view/editorials/zeropunctuation/2808-Zero-Punctuation-Crysis](http://www.escapistmagazine.com/articles/view/editorials/zeropunctuation/2808-Zero-Punctuation-Crysis)

Flash doenst work in 64bit Ubuntu/Firefox, works with 32bit.

I only see a white square.

I have tried the current version of Flash and the older more bugfree Version.

Does it work for anyone?

---

### Post by ZapalacX on 2008-03-06
working just fine on 64bit with the r48.

---

### Post by Kilz on 2008-03-06
Same here, the r48 plugin works for me on that site.

---

### Post by dandandan on 2008-03-06
File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

says about:plugins
i installed it using your script Kilz (i thinkit was yours wasnt it?)

any idea what could be wrong with my ff/flash?

---

### Post by Kilz on 2008-03-06
> **dandandan said:**
> File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

says about:plugins
i installed it using your script Kilz (i thinkit was yours wasnt it?)

any idea what could be wrong with my ff/flash?

Conflicting files left in by previous attempts to install flash.

---

### Post by dandandan on 2008-03-06
dan@sued0r:/usr/lib/firefox/plugins$ ls
libtotem-basic-plugin.so        libtotem-narrowspace-plugin.xpt  mplayerplug-in-rm.xpt
libtotem-basic-plugin.xpt       libunixprintplugin.so            mplayerplug-in.so
libtotem-gmp-plugin.so          mplayerplug-in-dvx.so            mplayerplug-in-wmp.so
libtotem-gmp-plugin.xpt         mplayerplug-in-dvx.xpt           mplayerplug-in-wmp.xpt
libtotem-mully-plugin.so        mplayerplug-in-qt.so             mplayerplug-in.xpt
libtotem-mully-plugin.xpt       mplayerplug-in-qt.xpt            npwrapper.libflashplayer.so
libtotem-narrowspace-plugin.so  mplayerplug-in-rm.so

can u spot anything?
or tell me where i could look?

---

### Post by Kilz on 2008-03-06
/usr/lib/mozilla/plugins 
~/.mozilla/plugins

Those are common locations in addition to the one you listed.

---

### Post by dandandan on 2008-03-08
i purged flashplugin package and manually removed all remaining flash files in those dirs, then reinstalled flash using your scripts but still flash is not working on that site, instead of flash windows i still see a white square.

any more ideas?

---

### Post by speedsix on 2008-04-09
I get the same thing, 64bit Hardy, was the same with Gutsy I believe.

Other flash videos work, youtube etc.

---

### Post by Yellow Pasque on 2008-04-09
Start firefox in a terminal. Does the terminal give any messages when you go to that site?

---

### Post by speedsix on 2008-04-11
Found the problem, it was Adblock!

---

