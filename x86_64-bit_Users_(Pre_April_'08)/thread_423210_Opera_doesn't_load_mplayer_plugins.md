---
title: "Opera doesn't load mplayer plugins"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ledah on 2007-04-25
Hi,

my Opera (9.20 static at Kubuntu 7.04 64Bit) doesn't load all plugins in the directory /usr/lib/opera/plugins. Only the flash plugin and the NS4Plugin Proxy are shown in the plugins dialog. The mplayer plugins were ignored. If I click the button "Find new ...", Opera doesn't find new plugins.

Any idea? :)

---

### Post by Ledah on 2007-04-26
Ok, the plugins were from the 64bit mozilla-mplayer package, so I guess they don't work with the 32bit Opera. Now I extracted the plugins of the 32bit package, but they don't work, too :(

---

### Post by kuja on 2007-04-26
Ledah, you'd also need mplayer to be 32-bit too probably.

---

### Post by Ledah on 2007-04-26
That's a good point :D
Is it possible to have the 32bit and the 64bit version installed? I have compiled the SMPlayer, which requires the 64bit mplayer.

---

### Post by kuja on 2007-04-26
Might be possible, I'm not really all that sure. It'll depend if you can find a way to force-install mplayer32, a package conq  makes.  That or maybe you can convince him to make a Feisty package? (Then again, if you've got mad skillz, you may be able to play around with the package to make it work on Feisty, I've half the mind to do it myself, when I get time.) If you manage to get it installed, be sure to symlink the regular mplayer binary to /usr/bin/mplayer64, and change the /usr/bin/mplayer symlink to point to the mplayer32 binary.

---

