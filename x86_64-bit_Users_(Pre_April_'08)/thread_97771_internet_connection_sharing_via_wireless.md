---
title: "internet connection sharing via wireless"
date: 2005-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomislavmedak on 2005-12-01
i use a ibook G4 with a d-link DWL-122 wireless usb card (prism2 chipset). i would like to share the internet connection coming through the ethernet cable via my wireless card. how do i do that?

tnx in advance

---

### Post by kairu0 on 2005-12-01
Sharing a wireless connection is just like sharing a wired connection. There is nothing special about your situation, so just follow this HOWTO and substitute the "ethX" for the name of your wireless interface ("wlan0", etc.) 

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

This assumes that the other computer that you'll be sharing with already has a static address assigned to it or is getting one from a dhcp server (your ibook or a router.)

---

### Post by Rxke on 2005-12-02
I found it far mor easier to just apt-get install firestarter (the firewal,)
and go to the firestarter website, and in their documentation section look up internetsharing, it works flawlessly and is well laid out.

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)


BTW, you do need a crossover cable, but if you google around a bit, and are not afraid to hack up an existing ethernetcable, you can easily build one yourself by simply swapping some connections.

---

### Post by ssam on 2005-12-02
you may not not need a cross over cable. my powerbook (1ghz ti 15") can auto switch, so it is happy with crossover or normal in any situation.

if you dont have an auto switching netword card, then:
cross-over between two computers
normal for computer to anything else.

---

### Post by Rxke on 2005-12-03
Oh, yes, that's right, I forgot. Me and my old hardware, tsk tsk stsk.

---

