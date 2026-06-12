---
title: "No sound in wine"
date: 2011-08-25
forum: Wine
---

### Post by hnasiet on 2011-08-25
yesterday, I was going to play in no$gba, since I didn't play for almost one year, but then I realized that It didn't have any sound, I tried to test the sound in winecfg but an error message appears ("audio test failed!"). I'm using wine 1.3.26.

---

### Post by thatguruguy on 2011-08-25
The sound system was completely re-written for 1.3.26.  Open winecfg and click the "Audio" tab.  In the "Hardware Acceleration" area, make sure to choose "Emulation."

---

### Post by hnasiet on 2011-08-26
> **thatguruguy said:**
> The sound system was completely re-written for 1.3.26.  Open winecfg and click the "Audio" tab.  In the "Hardware Acceleration" area, make sure to choose "Emulation."
thanks, but it didn't work :s

Edit: fixed for me. I just installed 1.2, previously I couldn't install it because of the directory .wine. But now that I deleted it everything is working fine. thanks again.

---

### Post by dino99 on 2011-08-27
new fix coming with 1.3.27 in a few days

---

