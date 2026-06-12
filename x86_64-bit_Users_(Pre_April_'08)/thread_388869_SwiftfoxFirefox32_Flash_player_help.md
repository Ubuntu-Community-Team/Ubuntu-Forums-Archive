---
title: "Swiftfox/Firefox32 Flash player help"
date: 2007-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2007-03-20
Hi all I was following the intruction on a post in this forum to get flash to work in the x64 version of Firefox usig the nspluginwrapper. Well it worked fine but now in my Swiftfox and firefox32 installs are now using the npwrapper.libflashplayer.so instead of the plain old libflashplayer.so, and flash is not even working in those browser either now. Is there a way to revert back to standard flash players in these 32 bit browser? As I would like to habe a browser with all plugins working. 

I have so many browser in search of stability, flash seems to crash them all! Well any help would be greatly appreciated.

With regards,
Chris

---

### Post by chrism66 on 2007-03-20
Ok, sorry for the premature post. I figured iy out. I had to go into the ./mozzilla/plugins in my home directory and delete the npwrapper.libflashplayer.so. And all is well now.

Chris

---

