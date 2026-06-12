---
title: "Breezy64-bit refused to install"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by babyLemon on 2005-10-18
I am in a deep pinch... I need to use linux at work, and basically decided on breezy. 32-bit version installed fine on my machine (amd athlon 64), but it refused to go past the ubuntu logo right after logging in. 64-bit version refused to install right out. It freezes right when it is checking for my keyboard. Nothing I do, short of turning off the computer, will help in this case. 

I have read in some other thread that the video card might be to blame for the problem with the 32-bit version. I have an ATI RADEON XPRESS 200. 

Please advise. I am about to go chop off some people's head...

---

### Post by mlomker on 2005-10-18
On the 32-bit you can Ctrl-Alt-F2 to another terminal and run **sudo dpkg-reconfigure xserver-xorg** to try another video driver.  'vesa' is very likely to work and once you're in you can look into installing the fglrx driver or experiment with the ati driver, which should be the default for your card.

---

### Post by babyLemon on 2005-10-18
Well, got that working. Now am on Breezy. Quite cute as a distro :) Shall personalize it now, so that I feel a bit more at home at work.

Thanks so much for the tip :)

---

