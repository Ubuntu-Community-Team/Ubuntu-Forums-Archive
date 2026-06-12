---
title: "Um, Hello Ubuntu x64?  Black display on boot w/ Asus P5B, 8800GTX"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sabrewulf on 2007-06-07
So after reading this thread - [http://ubuntuforums.org/showthread.php?t=466851](http://ubuntuforums.org/showthread.php?t=466851)

I thought "aha, my problem is solved."  Alas, no.  I followed those instructions successfully and to the letter, and yet still I am left with a non-working Ubuntu install.  Once it starts booting into GUI mode, all I get is a black (but active) screen, and a lot of hard drive activity, which leads me to believe Ubuntu is loading, but since I can't see anything it's kinda hard to tell.

I can successfully boot into recovery mode, but that's not what I installed Ubuntu for...  so does anyone have any suggestions?  My HW config is as follows:

Core 2 Duo E6600
Asus P5B Deluxe (Intel P965)
GeForce 8800GTX
4x1GB system memory
Creative X-Fi

Any help would be greatly appreciated!

---

### Post by sabrewulf on 2007-06-07
For anyone reading this thread later, after searching this thread - [http://ubuntuforums.org/showthread.php?t=375853](http://ubuntuforums.org/showthread.php?t=375853)

I was able to get Ubuntu (both liveCD and post-install) booting successfully by adding "agp=off" to the kernel boot options.

---

