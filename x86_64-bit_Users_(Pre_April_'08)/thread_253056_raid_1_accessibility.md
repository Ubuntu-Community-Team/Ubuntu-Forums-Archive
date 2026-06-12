---
title: "raid 1 accessibility"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by quadergh on 2006-09-07
I am a newbie to Linux I have Ubuntu 6.06. I deleted windows on my fastest machine.  I want to know how to access my two sata drives that are in raid 1 configuration. I have lots of data saved on that pair.  I tried Ubuntu about a month ago and I don't think I did anything special, but I was able to read and write to the drives.! Thnx.  Quadergh

---

### Post by RAOF on 2006-09-07
In raid 1 it's easy.  Just mount either of the pair, and because all the data is mirrored on both discs you can read/write just fine.  Of course, this means that the two discs are no longer RAIDed together.

If you want to keep the discs RAIDed, I'd check out [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

