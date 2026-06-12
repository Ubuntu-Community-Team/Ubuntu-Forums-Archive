---
title: "Networkmanager and Wireless"
date: 2007-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by woopud on 2007-01-19
I'm running Edgy 64bit on my AMD 64 HP laptop with no problems, installed fwcutter and gnome-Network-Manager and my Broadcom 4306 works perfect.  Everytime I boot into Edgy it picks up my wireless network with no problem including my WEP.  But i can't connect to another network, network manager only shows wired network ?

Bert

---

### Post by onesojourner on 2007-01-19
check out connection manager.

[http://ubuntuforums.org/showthread.php?t=299462&highlight=wireless+manager](http://ubuntuforums.org/showthread.php?t=299462&highlight=wireless+manager)

---

### Post by rudefyet on 2007-01-20
I'm curious as to how you got it working period, as far as I know most of the 64bit HP laptops have issues with the broadcom 4306 and 64 bit kernels.

I've been trying for ages, and once I extract the firmware, I get a kernel panic whenever the bcm43xx module is loaded.

---

### Post by woopud on 2007-01-20
The solution for me is in the following thread, works perfect now.

[http://www.ubuntuforums.org/showthread.php?t=341920](http://www.ubuntuforums.org/showthread.php?t=341920)

Bert

---

### Post by wncben on 2007-01-24
THe clouds part, and the voice of god says unto thee, "ltet there be Wi-Fi, and there was, and it was good"


After much putzing around, following compwiz's great howto and fwcutter, I finally got a spark of life from my wifi card, but it was the post to comment out the stuff in /etc/nework whatever...

  Now, the only problem i am having is that the cure seems to have broken my touchpad, (I have found a few posts that imply that the bcm43xx conflict witht he touchpad drivers)

Anyhow, it works, except for scrolling, and touch to drag, but I can live with that for the time being as I am ONLINE!!!!  YAYAYAYAYAYAYAYA!

---

