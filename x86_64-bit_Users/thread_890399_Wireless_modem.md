---
title: "Wireless modem"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by TrentB on 2008-08-15
Hello! I recently bought a laptop, and I want to dual boot the 64 bit version of Ubuntu on here eventually. I was running the CD live, and everything seemed fine... I just can't connect to the internet.

I looked around for a while but I couldn't find anything for the built in modem. The light that tells me whether the modem is on or off says that it is off, but I have it set for on.

What do I do? Am I going to have to connect to the internet using an Ethernet cable?

And just one more simple question, how do I change the screen resolution? the default makes everything look stretched and weird on my laptop... 

Thanks for taking time to read this, I really appreciate it!:)

---

### Post by Jouke74 on 2008-08-15
The screen resolution can probably be chenged by navigating to :
System > preferences > screen resolution.

I related problem might be that you need to install the restricted video drivers found under:
System > administration > hardware drivers.

In this same place you can check if the driver for your wireless card is also not mentioned. If this is the case install and activate this one as well and see if you have wireless. This may require a reboot.

If this is not the case than please post back and try to figure out which wireless card is in your laptop. To do this you can open a terminal under:
Applications > Accessories > Terminal

Then in the terminal type the command: "lspci" and give the output here.

---

