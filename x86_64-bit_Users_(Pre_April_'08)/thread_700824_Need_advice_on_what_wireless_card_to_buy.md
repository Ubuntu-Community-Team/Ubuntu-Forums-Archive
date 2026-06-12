---
title: "Need advice on what wireless card to buy"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by zenten on 2008-02-18
Ok, so I just moved, and now my 64 bit ubuntu edgy system is in a completely different floor from my router, and needs a wireless card.

What is one that should work with the least amount of headache, that I can buy new from a store like Futureshop (as I have a bunch of gift cards for there)?

---

### Post by arkara on 2008-02-18
you can see which cards play seamlessly on the debian hcl or ubuntu hcl
you can also ask the shop if they know anything about linux compatibility
and the last one is to go to the shop with a live cd and test the card on site.

---

### Post by Yellow Pasque on 2008-02-18
You can also use ndiswrapper if the card has good Windows 64-bit drivers. I'm currently using ndiswrapper with a D-Link DWL-520(?) which has a Realtek 8180L chipset and it works great. Just let us know if you need help and we'll get you up and running.

---

### Post by zenten on 2008-02-18
> **Temüjin said:**
> You can also use ndiswrapper if the card has good Windows 64-bit drivers. I'm currently using ndiswrapper with a D-Link DWL-520(?) which has a Realtek 8180L chipset and it works great. Just let us know if you need help and we'll get you up and running.

My big concern is that I'll go out and buy something that isn't possible to get up and running.  I'm not sure how to avoid that, as it seems like what appears to be two of the exact same cards can easily have different chipsets.

---

### Post by John Jason Jordan on 2008-02-18
> **Temüjin said:**
> You can also use ndiswrapper if the card has good Windows 64-bit drivers. I'm currently using ndiswrapper with a D-Link DWL-520(?) which has a Realtek 8180L chipset and it works great. Just let us know if you need help and we'll get you up and running.
There is a problem with ndiswrapper and power management. I have a Netgear 511b which works fine but only with ndiswrapper. When using it I get about one hour battery life on my Thinkpad T61. I paid very little for it, so I bought a Netgear 511T ($17 on eBay) which uses the Atheros chip and "just works" on my 64-bit Gutsy. Now I get battery life of 2-2.5 hours. The point is that ndiswrapper is fine, but may not play nice with power management with some cards. 

I do recommend the Netgear 511T, but do NOT get the plain 511. Make sure it has the "T" on it.

---

### Post by zenten on 2008-04-19
I forgot to mention that it's a desktop system.  I suppose that would change things a bit.

---

### Post by Gary Heinl on 2008-04-20
I am currenly running a linksys model number wmp54g. It has worked flawless out of the box. The only problem I had was the initial wep input. The log in screen kept defaulting to 128bit encryption when I was using 64 bit so I had to change it before I was able to log in. Good Luck.

---

