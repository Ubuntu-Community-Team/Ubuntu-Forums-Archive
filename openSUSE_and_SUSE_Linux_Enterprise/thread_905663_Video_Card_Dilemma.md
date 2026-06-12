---
title: "Video Card Dilemma"
date: 2008-08-30
forum: openSUSE and SUSE Linux Enterprise
---

### Post by homerj742 on 2008-08-30
I have a Shuttle PC (SG31G2) using built in intel GMA 3100 video.

This is setup in a dualboot configuration.

Boot 1: OpenSUSE 11.0 - The driver shows that it is installed (G33), however, I cannot get the proper resolution (1680x1050). 

Boot 2: 64 Studio (Debian etch) - Uses the generic VESA driver!! There are lines all over the screen. I don't understand this. 

Any suggestions on how to resolve this issue?

If I have to get another video card, can I have any reccommendations? (ie - which NVidia chipset to purchase)

Any help would be greatly appreciated. Thank you!

---

### Post by milton1 on 2008-08-30
for debian, the xserver-xorg-video-intel package should give you the 'intel' driver. I have had that one working well with a 3100 card.

---

### Post by homerj742 on 2008-08-31
Thank you for that suggestion, I will certainly try that! Heck, atleast it will take care of one part. After installing the intel driver, do I have to adjust the xorg.conf file at all?

---

### Post by milton1 on 2008-09-01
you may need to set your driver to 'intel' within the xorg.conf file.

---

### Post by homerj742 on 2008-09-02
> **milton1 said:**
> you may need to set your driver to 'intel' within the xorg.conf file.

That didn't seem to work out too well, I actually broke down and ordered an NVidia 7300GS card. it should do the trick :)

---

