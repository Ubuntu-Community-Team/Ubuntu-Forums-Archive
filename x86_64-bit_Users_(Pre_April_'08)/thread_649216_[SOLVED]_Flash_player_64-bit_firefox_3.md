---
title: "[SOLVED] Flash player 64-bit firefox 3?"
date: 2007-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by macaholic on 2007-12-24
I have Firefox 3.0b3pre installed on my 64 bit gutsy, and I was wonderign if there was anyway to get flash working in it, it works on firefox 2, just not 3. Any help would be greatly appreciated.

---

### Post by macaholic on 2007-12-24
FIxed it, just had to copy the plugin to the new firefox plugin folder like so,
```
cp /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox-3.0/plugins
```

---

### Post by mirzmaster on 2007-12-28
> **macaholic said:**
> FIxed it, just had to copy the plugin to the new firefox plugin folder like so,
```
cp /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox-3.0/plugins
```

Actually, I would suggest making a symbolic link instead of copying the plugin file.  The advantage of linking is that if the plugin is updated in /usr/lib/flashplugin-nonfree, you won't need to re-copy it.  :)

Try this:

```
ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox-3.0/plugins
```

---

### Post by macaholic on 2007-12-29
Ya, thanks that is a much better idea.

---

### Post by jejones3141 on 2008-02-27
A couple of things:

Since we're talking 64-bit, doesn't Firefox3 need npwrapper.libflashplayer.so to use the 32-bit nonfree flash plugin?

Also, as things stand I see no /usr/lib/firefox-3.0, but rather /usr/lib/firefox-3.0-3.0b3pre.

I symlinked npwrapper.libflashplayer.so to /usr/lib/firefox-3.0-3.0b3pre, but I'm still getting the "you need the latest flash" blurb from youtube. Any suggestions?

---

### Post by wingnux on 2008-02-27
It didn't work for me =/ I was messing around with the java packages since it doesn't run any .jar file and suddenly flash stopped working on firefox 3.

---

