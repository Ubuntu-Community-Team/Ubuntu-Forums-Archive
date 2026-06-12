---
title: "Screen Unreadable In Xorg"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by megaman22 on 2005-11-18
I have a sempron 64 3000+ machine  with an ATI radeon 9550 256MB graphics card
and I am getting a serious problem with Xorg. When i start the window system nothing is being displayed, all i see are squares for the windows with no text and the cursor is a large green square even when i change the drivers from ati to vesa. 

Ive tried 64bit gentoo then 64 bit ubuntu and then the 32bit ubuntu all with the same results, a big white screen and a green block for the cursor


Is any one experiencing this problem? how do i begin to solve it?

---

### Post by casper_2095 on 2005-11-19
I had a problem with an ATI-9200se which displayed a crazy screen of vertical lines yet a neat little cursor.   The solution was to boot to the "recovery" option, edit the xorg.conf to not load various modules.  Turned out that the card barfed on the 'glx' module.  I just commented it out permantently. You might try a similar approach.

---

### Post by megaman22 on 2005-11-21
Thanks for the tip, 
but id didnt work,
but at least im seeing black squares now :confused: 
im thinking of flashing my bios to a radeon 9600 and see if linux will recog it....
were u able to get your device say radeon 9550? or does it stil say ATI unknown device?

---

