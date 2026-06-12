---
title: "Ubuntu freezes at login"
date: 2005-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Juri on 2005-06-13
Thank you for reading this
 
I get all to a login screen. But it seems like anytime I touch a key or the mouse I have 5 to 30 secounds before Ubuntu completly freezes.

I have found a way to get into Ubuntu, boot into the recovery mode add '/usr/X11R6/bin' to PATH and type 'gdm.' then I get the message 'failed to initalize hal' but Ubuntu doesn't freeze. (hal is the host name of my computer) 
I am using the AMD64 5.04 install cd burned form the iso from the United States official site. I have an AMD Athlon 64 processor 3200+, and a Gigabyte K8N Pro Mobo.

I have found and installed the Nvidia drivers, but this seems to have changed nouthing (except I now see a big Nvidia logo before my login screen). Any advice on how I could go about tracing the problem myself. Or on how to get helpful information so that I can give more informed posts.

if you need more info, please tell me.
Thanks again

---

### Post by diebels on 2005-06-14
'failed to initalize hal' means failed to initalize Hardware Abstraction Layer. Not sure why your system is freezing, check some logs.

I had a freezing problem with hoary nvidia drivers. It's gone with kernel-2.6.11 and 7664 nvidia drivers.

---

