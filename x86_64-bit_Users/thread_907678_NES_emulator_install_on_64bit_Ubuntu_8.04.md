---
title: "NES emulator install on 64bit Ubuntu 8.04"
date: 2008-09-01
forum: x86 64-bit Users
---

### Post by Mhawkins1 on 2008-09-01
I have tried to download and install several NES emulators. I can get the download part but the installation and use part I can't. Can someone walk me through the process. Any help would be appreciated. Thanks!

Additional Info:
I have tried every emulator listed on this page:  [http://www.zophar.net/linux/nes.html]("http://www.zophar.net/linux/nes.html")

---

### Post by kjohansen on 2008-09-01
i get a 404 on the page you list.

i dont know how the install works since I cant see the emulator but im going to guess open a terminal in the downloaded directory and then

./configure
make
sudo make install

---

### Post by cariboo on 2008-09-01
There are several emulators available in the repositories, two in particular:

snes9x-x
xmess-x

You can find them by searching in System-->Administration-->Synaptic Package Manager

Jim

---

### Post by xen-uno on 2008-09-02
snes9x works pretty good here. I've turned on Scale, Hi-Res, Full Screen, and set TV Mode to Normal. Looks pretty good that way. Were these snes games (ie Street Fighter II) that low of a resolution on a TV (I don't recall)?

---

### Post by Avoozl on 2008-09-02
Probably.  A standard television has a much lower resolution than a standard computer monitor.  I have an "HD" television that is actually lower resolution than my monitor... but the TV is a lot bigger. :)

---

### Post by xen-uno on 2008-09-02
I thought it would be closer to NTSC upper rez limit (just short of VGA). With no video options or window resizing, rez appears to be about 1/2 that. Looks as I remember it now after playing it a bit.

---

### Post by tvon on 2008-12-29
Apologies for digging up an old thread, but I've been toying around with XMESS for SNES emulation tonight and discovered that the **-vidmod 1 -ef 3 -fullscreen** options work very well with a 37" hdtv.  I'm really surprised how good it looks, I was using snes9x before and wasn't able to make it look this good.  You can check the help output to see what thos options mean/do.

Overall MESS is more of a pain to setup but given the wide range of systems it can emulate I think I'll be sticking with it.

---

