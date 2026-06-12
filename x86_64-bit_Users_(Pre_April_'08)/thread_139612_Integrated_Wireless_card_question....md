---
title: "Integrated Wireless card question..."
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by cyphrix on 2006-03-04
Ok, so, I don't want to be too redundant here but I just installed Ubuntu on my Powerbook G4 and I'm totally lost when it comes to getting online wirelessly.  I have absolutely no clue as to how I get my wireless adapter to work in Ubuntu.  I have to hardline to the router.  Anyone have any instructions for me?  Thanks in advance.

:confused:

---

### Post by illfilles on 2006-03-05
I am also having similar troubles. If someone could point us in the direction of a good FAQ or tutorial we would really appreciate it.

---

### Post by calum on 2006-03-05
[QUOTE=cyphrix]Ok, so, I don't want to be too redundant here but I just installed Ubuntu on my Powerbook G4 and I'm totally lost when it comes to getting online wirelessly.  I have absolutely no clue as to how I get my wireless adapter to work in Ubuntu.  I have to hardline to the router.  Anyone have any instructions for me?  Thanks in advance.

:confused:[/QUOTE]

Assuming your Powerbook has an Airport Express wireless card (rather than the older Airport card), it's going to be tough... Airport Express isn't really supported yet in Linux, but people are working on it and it's getting there.  If you're not comfortable with compiling and installing the [drivers](http://bcm43xx.berlios.de/) yourself, you can either (a) just put up with your cables for another few months until it's supported better, or (b) buy a cheap PCMCIA wireless card to tide you over for a while, which should pretty much "just work"-- I used a Netgear card in my Powerbook G4 with Ubuntu quite happily for many months.

---

### Post by ssam on 2006-03-05
if the powerbook is aluminium then it is airport extreme which will not be supported until the next release in april.

if it is a titanium powerbook then it should be the normal airport and you should be able to configure it from System -> Administation -> Networking.

if you decide to buy a cheap pcmcia card then make sure you look at [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) and note that sometimes the cards change chipset between minor revisions, so get exactly the right one.

---

