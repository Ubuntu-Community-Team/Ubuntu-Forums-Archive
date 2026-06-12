---
title: "Colors switched in Xubuntu on G3 iMac"
date: 2005-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by pingswept on 2005-11-28
So after a little bit of refresh rate tweaking, I got an old iMac working with Xubuntu. It's still slow (350 MHz) and low on memory, but at least it has Firefox 1.0.7 so Gmail works. With OS 9, I was stuck with Netscape 7 or IE 5.2.

One remaining problem: red seems to have been replaced with blue. I consider this to be a little weird. At cnn.com, for example, the logo is bright blue. All colors are still displayed, but the spectrum is somehow shifted.

Anyone know how this is controlled? In xorg.conf somehow?

---

### Post by pingswept on 2005-11-28
It seems that switching the video card driver listed in /etc/X11/xorg.conf from "fbdev" to "ati" fixes this problem.

Hooray!

---

### Post by neoplasticity on 2005-11-28
could you tell me what settings you used for xconf?

i just installed Xubuntu on top of a server install of 5.10 on an imac 333 rev d

however, when i try to startx, the monitor either turns off or it gets stuck in some grey screen depending on how i've configured it.

also, i can't seem to get into console after i've failed an attempt at startx which is highly annoying because i have to reboot the entire system to try another configuration.

---

### Post by monway on 2005-12-01
You can always compile the latest xorg cvs and install that over the existing one after an xubuntu install. It is to my understanding there has been a lot of fixes and features added since it's very close to the release of xorg7. Give that a try and most possibly your issue will be fixed. Please let me know if this was helpful for you.

---

### Post by pingswept on 2005-12-01
[QUOTE=neoplasticity]could you tell me what settings you used for xconf?[/QUOTE]

Hi Neoplasticity,

My xorg.conf is posted [on my blog]("http://pingswept.org/index.php/xorgconf"), but the formatting is a bit screwed up at present because the Wordpress interprets hashes as list signifiers. I'm going to post a full description of my experience putting Xubuntu on a 400 MHz iMac soon, but maybe that can help you along. The only things I changed were the refresh rates and the driver (fbdev -> ati).

Overall, it's working really well-- much better than OS 9.2. It's only got 64 MB of memory, but Firefox runs surprisingly well. I plan on maxing out the memory when I get the chance. Then the only problem will be the lack of automatic login and startx, but I think I can figure that out. I work in a school where we have lots of these old iMacs that are barely usable under OS 9.2. If I can get this working smoothly, it will be great.

---

