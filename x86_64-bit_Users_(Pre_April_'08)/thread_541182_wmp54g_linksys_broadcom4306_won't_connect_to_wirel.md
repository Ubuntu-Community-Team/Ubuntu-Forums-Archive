---
title: "wmp54g linksys broadcom4306 won't connect to wireless networks"
date: 2007-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by gfunk87 on 2007-09-02
I'm using the beta version of Gutsy Gibbon, Ubuntu 7.10 however I don't think this has any relation to my problem.  My system is a 64 bit system which made it a pain to find a 64 bit driver but after 2 days of searching the internet I found one.  I've made linksys cards work before using the same technique I used this time, but my problem is my Desktop (with wireless card) can see the wireless networks, but it will not connect.  I have tried on my home network using wpa, and my neighbors network which is an open network, the system will simply not connect to them though.
to install my driver i simply followed these instructions:

bcm43xx-fwcutter bcmwl564.sys
 cp *.fw /lib/firmware
 ndiswrapper -i bcmwl5.inf

like i said, i've done this before (on a 32 bit system though) and it worked like a charm.  this time however i can't connect to any networks, but i can see them:)

I should also mention that i know next to nothing when it comes to working with Ubuntu

---

