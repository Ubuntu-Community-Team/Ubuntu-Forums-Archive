---
title: "How can I get terraria to run on wine with a 64 bit system?"
date: 2013-05-15
forum: Wine
---

### Post by calinic on 2013-05-15
I just bought my copy of terraria while it was on sale through steam. I've looked around and seen it's a tough processs to get it working. I have a 64-bit system and there seems to be a more complicated way when you have that. Can someone give me clean instructions on how to install and play it? I'm running 13.04 on Ubuntu.

---

### Post by Perfect Storm on 2013-05-16
If you running 64-bit system and want to run steam games (32-bit) you need to install 32-libs to your system.
You can find it in Ubuntu Software Center: **ia32-libs**
or the faster way via terminal:
```
sudo apt-get install ia32-libs
```

EDIT: terraria is Windows only game and do not run natively under Ubuntu. You may try wine and through that install Windows Steam, but it's a hit'n'miss when it comes to Windows game on Linux. Better to dual boot or use games that are available for Linux.

I'm moving this thread to the wine section.
You may try take a look at the stickies in our wine section, lot of good info on the subject.

---

### Post by calinic on 2013-05-16
Thanks for the info. I'll fiddle around with it a little later tonight i guess with the package you told me to istall.

---

