---
title: "Problems with flash (buttons)"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by Eiven on 2009-11-13
Any flash files work fine except for the buttons. The buttons on any flash video or file are either very slow or don't work at all. Is there a fix to this, or is it just one of those problems i have to live with?

---

### Post by ubernoob on 2009-11-13
Same problem here. :(

---

### Post by Cuddles McKitten on 2009-11-13
That usually means you're on a 64 bit system, but you're using the 32 bit flash from the repos.  Uninstall the repo's flash player, download the 64 bit flash from Adobe.com, and put libflashplayer.so in your ~/.mozilla/plugins/ folder.

Edit: here's a link for the download: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

