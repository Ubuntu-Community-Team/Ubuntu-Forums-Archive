---
title: "mplayer plug for amd64"
date: 2005-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-03-18
i just installed mplayer and wanted to install the mozilla plugin, but when i tried, it listed a bunch of 32bit versions of mplayer as deps, whats up with that?? anyone know a workaround

---

### Post by dmatrix on 2005-03-18
I wish I did too. I have a 32bit chroot setup for Firefox 32bit with Flash plugins and mplayer-plugin + w32codecs. RealPlayer 10 is another one I cannot get working on AMD64. 

Instuctions on building a 32bit chroot for Firefox, w32codecs and realplayer10:
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

---

### Post by blinksilver on 2005-03-18
I'm not ready to chroot just yet, if the mplayer can be converted over why not the plugin, i mean its basically a small link to the mplayer codecs and engine, why is it not portable??? Its open source, thats the whole point

---

### Post by wmcbrine on 2005-03-18
Well, the plugin may be, but the win32 codecs, Flash and Real Player aren't. So someone will have to remove those dependencies and repackage.

---

### Post by blinksilver on 2005-03-18
and that is the answer i wanted, this suck, but i guess i have to deal

---

