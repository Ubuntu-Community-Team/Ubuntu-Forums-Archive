---
title: "How to install realplayer on x64?"
date: 2007-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Renato Souza on 2007-10-31
I would like to know how to install realplayer on gutsy 64 bits. I have searched the forum and asked on irc. No one seems to know.

Is it possible for me to get it running?

Thank you

---

### Post by _simon_ on 2007-10-31
I don't remember doing anything special.

Just download and execute the bin.

[http://www.real.com/linux/](http://www.real.com/linux/)

---

### Post by cjazz on 2007-10-31
Download RealPlayer10GOLD.bin and make the file executable ("chmod a+x RealPlayer10GOLD.bin" from the command line), then run the bin file by typing "./RealPlayer10Gold.bin."

I should say that in the past, I've encountered some problems, with the bin file refusing to install because it couldn't find libstdc++.so.5, even though that library  was already on my system. I believe that was because my system is 64-bit Ubuntu and Real Player is 32-bit. For me, that was resolved when I installed ia32-libs.

---

