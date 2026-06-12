---
title: "Installing nvidia 9472 for the 8800 in 64-bit dapper"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by hagakure on 2006-12-10
After many hours tonight, I've got ubuntu installed on my new box, however, X cannot be initiated because I am using an 8800gts which won't work with the current driver. Trying to install the 9472 driver brings up a message saying its meant for 32 bit systems, and won't install for 64-bit. 

I tried extracting it and installing that way, but after getting pretty far along it comes back saying it cannot create an nvidia.ko file. 

I noticed there are ways to force i386 architecture with dpkg. Is there anyway to get around my problem and use an 8800 in 64 bit dapper?

---

### Post by xopher on 2006-12-10
Make sure you have downloaded the correct (64-bit) version of the driver:

[http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9742.html]("http://www.nzone.com/object/nzone_downloads_linux_display_x86_64_1.0-9742.html")

If you'd like to build your own custom nvidia-glx with 97.42, check this out: 

[https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx](https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx)

Hope this helps. ;)

---

### Post by hagakure on 2006-12-11
*Slaps forehead*

Now I feel dumb, I didn't even know there was a 64-bit driver available. I should have looked better.

Ok, so now I've got X. Bummer I can't get networking to work on this new 680i chipset.

I tired that whole forcedeth, anyways thats another topic..

---

