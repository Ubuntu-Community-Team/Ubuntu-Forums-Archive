---
title: "100% CPU usage in Wine, not experienced until now"
date: 2012-01-05
forum: Wine
---

### Post by Anuovis on 2012-01-05
Sometimes I like to play *Emperor: Rise of the Middle Kingdom* and it worked flawlessly with Ubuntu 10.04 and whatever Wine version that was available at that time. It has platinum Ubuntu ratings on WineHQ database and should run perfectly as long as you set the windowed mode.

However, with Ubuntu 11.10 the game exe file uses at least 70% of the CPU and regularly shoots up to 100% causing terrible lag. I tried different versions of Wine and display modes (with virtual desktop, without), even running it in Unity 2D envionment but they all produce the same results.

My hardware is the same (except the swapping of the default RAM chip for two newer ones), the installation files are the same.

I tried searching for the answer but there seems to be very different cases of 100% usage with all sorts of things. Could not find any case with this particular game though.

The game is ancient and requires 400 Mhz CPU / 64 MB  of RAM / 4MB graphics card. 
I have Dell Inspiron 6400 / Intel Core Duo 2Ghz / 2GB of RAM / 128 MB ATI x1400 video card.

What could cause this? Could a downgrade in Ubuntu possibly help?

I could live without it but I can not understand why something that was working perfectly would suddenly start to kill my laptop.

---

### Post by Basher101 on 2012-01-05
it can only be either the video driver (which i doubt, since then you would have GPU load not CPU), or most probably newer kernel having some bug. Try installing an older or newer version from the beta repositories, otherwise your only choice is to roll back to 10.04


regards

---

### Post by Anuovis on 2012-01-05
Come to think about, I also experienced some 100% CPU peaks while watching a high definition video the other day. It was either 11.04 or 11.10. Then I just assumed my laptop was not able to handle it properly.

Could this be related to the power regression bug in the latest kernels?

---

