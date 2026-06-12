---
title: "Adobe Flash simple fix for choppiness!"
date: 2009-09-24
forum: x86 64-bit Users
---

### Post by DodgeV83 on 2009-09-24
I posted this on the 64bit forums, but it should apply to all Ubuntu (maybe even all Linux) users.

It seemed no matter what I did, flash was incredibly choppy on my dual-core recent Dell laptop. I had simply given up lately and decided it was just something I'd have to deal with as long as I was with Linux. This was a contributing factor to me dropping Linux for Windows a while back, but I figured I could do without flash videos...

Well today I had enough and looked again for a solution. I noticed the video was noticeably better when the laptop is plugged in, even though choppiness was still abundant enough to make me simply not want to watch any flash videos full-screen.

After trying all the beta NVidia drivers and everything else on the forums, I never thought to check my CPU.

My research brought me here:

[http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10](http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10)

I simply added the **Gnome CPU Frequency Scaling Monitor** to my panel and set it to as high as it goes, 2.4GHZ.

FLASH IS PERFECT NOW!

I hope this helps someone out!

Edit:  Found another factor.  Even after this "fix", it gets completely choppy again (unwatchable for me) after going into **suspend mode** and coming back.  Going into Hibernate mode does not have this effect.  **No more suspend mode for me!**

---

### Post by philinux on 2009-09-24
When I switch to full screen flash my cpus go to almost max anyway.

However some full screen flash really benefits from the performance setting. Ie full on.

It seems the on demand setting does not always give the best result.

---

### Post by michael37 on 2009-09-24
My two year old laptop for some reason does not exhibit the same problem with flash.  I did notice that flash uses 70% CPU plus another 20% for Xorg when playing HD content, however, it's still quite smooth.  I have a well outdated ATI video card.  

I am wondering what else are you using?  Compiz?  

Btw, you may find [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=132600") useful, esp comment 13.  Given that flash is rendered on the CPU and barely touches video, I have no idea why nvidia owners are plagued with more problems than others.

P.S.  I also reproduced the problem where CPU does not switch to high speed when flash is playing.  Very strange indeed.

---

### Post by DodgeV83 on 2009-09-25
Found another factor.  Even after this "fix", it gets completely choppy again (unwatchable for me) after going into **suspend mode** and coming back.  Going into Hibernate mode does not have this effect.  **No more suspend mode for me!**

---

### Post by DodgeV83 on 2009-09-25
> **michael37 said:**
> My two year old laptop for some reason does not exhibit the same problem with flash.  I did notice that flash uses 70% CPU plus another 20% for Xorg when playing HD content, however, it's still quite smooth.  I have a well outdated ATI video card.  

I am wondering what else are you using?  Compiz?  

Btw, you may find [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=132600") useful, esp comment 13.  Given that flash is rendered on the CPU and barely touches video, I have no idea why nvidia owners are plagued with more problems than others.

P.S.  I also reproduced the problem where CPU does not switch to high speed when flash is playing.  Very strange indeed.

One reason might be, the graphics card has something to do with the computer going into suspend mode.  I know this only because before I install the "restricted" nvidia driver, I can't suspend my machine.

Since I have found extreme choppiness in flash videos after coming back from a suspend (I never turn off my machine, only using suspend mode until I found this bug), it makes sense for it to be related to the graphics card.

---

