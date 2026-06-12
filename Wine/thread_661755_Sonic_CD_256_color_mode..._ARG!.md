---
title: "Sonic CD 256 color mode... ARG!"
date: 2008-01-08
forum: Wine
---

### Post by lunarcloud on 2008-01-08
SO I've installed Sonic CD for PC (win95) and applied the WinXP patches. Now I've got the classic problem of the required 256 color mode. It never liked being more or less than 256 colors. It wont play unless I can set this. 
Any Ideas? I've got it running under cedega, but wine will do just fine.

---

### Post by sauronsmatrix on 2008-01-18
try running winecfg and tweak options in there

or use this program call xnest. im not sure how that one works, but i've heard thats the other option.

---

### Post by lha on 2008-01-19
> **zarquad said:**
> SO I've installed Sonic CD for PC (win95) and applied the WinXP patches. Now I've got the classic problem of the required 256 color mode. It never liked being more or less than 256 colors. It wont play unless I can set this. 
Any Ideas? I've got it running under cedega, but wine will do just fine.

A simple workaround that helped me was to change color depth from 24 bpp to 16 bpp in xorg.conf. There's also a more advanced way, see [http://wiki.winehq.org/256ColorsWorkarounds]("http://wiki.winehq.org/256ColorsWorkarounds").

---

