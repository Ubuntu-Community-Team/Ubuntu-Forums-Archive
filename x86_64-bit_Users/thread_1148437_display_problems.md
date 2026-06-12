---
title: "display problems"
date: 2009-05-04
forum: x86 64-bit Users
---

### Post by spoolingti on 2009-05-04
Let me preface this by first mentioning that I am a complete linux/ubuntu newb. With that being said, here is my problem...


I recently put together a computer and I figure I'll list the components to help diagnose my problem:

MSI k9a2 platinum AM2+ mobo
AMD Phenom II X4 940
4 GIG ram
150gb WD velciraptor 10k SATA II
300 gig WD SATA II 
ATI Radeon 3450HD

I just installed ubuntu 9.04 64-bit and everything worked fine. I saw that when i clicked on display properties it showed that there were restricted ATI drivers for my vid card, so i activated them and restarted. It recognized my monitor's native resolution (1900x1080) and everything displayed fine. This past weekend I hooked up the analog video out of my card to my tv, since i wanted to watch some hulu videos. It seemed like when i opened up the display properties under Admin, the property window never came up and slowed down my pc a good deal. I was still able to have video on my tv, but decided to unhook the cable and restart. After the restart all that was hooked to my video card was my monitor and I still had the flakiness of the display properties window. Any ideas? Did i confuse y'al :). I realize that I might have screwed myself by using the 64 bit version of ubuntu as opposed to the 32bit mainly from a driver support stand point.

---

### Post by Kareeser on 2009-05-04
"Flakiness"?

A screenshot might help :)

---

### Post by spoolingti on 2009-05-04
> **Kareeser said:**
> "Flakiness"?

A screenshot might help :)

I can provide a screenshot but all its going to show is the outline of a dialog box with no words in it. The display properties never fully loads up.

---

### Post by kemorc on 2009-05-04
This also happens to me whenever I click display properties on any of my 9.04 installed computers in the house.  I don't dare click it anymore... cuz I know the bug has yet to be fixed.  Basically what happens is, one of my cores gets 100% consumed and the puter becomes pretty much locked up.  Even if i shut down the display properties process, it STILL is hogging my CPU.

All I can come up with is that it is either:
A: ATI drivers and problems... CCC absolutely sucks, leaves me with 25 Hz for a freq...
or
B: 9.04 has a serious flaw/problem with "Display Properties".

---

### Post by spoolingti on 2009-05-04
> **kemorc said:**
> This also happens to me whenever I click display properties on any of my 9.04 installed computers in the house.  I don't dare click it anymore... cuz I know the bug has yet to be fixed.  Basically what happens is, one of my cores gets 100% consumed and the puter becomes pretty much locked up.  Even if i shut down the display properties process, it STILL is hogging my CPU.

All I can come up with is that it is either:
A: ATI drivers and problems... CCC absolutely sucks, leaves me with 25 Hz for a freq...
or
B: 9.04 has a serious flaw/problem with "Display Properties".

All i can say is that before i tried to hook up my tv the display properties window worked just fine, the minute i hooked it up something broke. I at one point got some sort of error message when i tried to change the resolution on my monitor back to its native resolution. It pointed me to some file location that got corrupt somehow.

---

### Post by kemorc on 2009-05-04
thats odd... because the same exact problem (your resources gettin hogged) is the same exact thing I'm feeling on EVERY ubuntu installed PC in my class and at home.  We will not even touch it now.

---

### Post by spoolingti on 2009-05-04
> **kemorc said:**
> thats odd... because the same exact problem (your resources gettin hogged) is the same exact thing I'm feeling on EVERY ubuntu installed PC in my class and at home.  We will not even touch it now.

My only other idea could be that maybe its some update that caused a conflict somewhere.

---

### Post by prat on 2009-05-04
You may try to install the driver from AMD/ATI website...me too got this problem before.

Now everything is fast & display preference works fine as well. :)

---

### Post by Bloemetjesgordijn on 2009-05-05
Ati works for me in Jaunty

---

### Post by spoolingti on 2009-05-05
> **prat said:**
> You may try to install the driver from AMD/ATI website...me too got this problem before.

Now everything is fast & display preference works fine as well. :)

ATI has 64bit linux drivers available to download? I'll have to take a look....i looked everywhere for drivers but the source, go figure.

---

