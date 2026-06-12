---
title: "gutsy wireless locks up my computer"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by RocketRanger on 2007-10-25
I have installed gutsy and almost everything is running way better than feisty. 

My problem is that when I try to connect to my wireless network the computer completely locks up and I need to shut it off and reboot. 

in feisty there was a problem with wifi cards using the rtl8180 chipset which seems to have been fixed in gutsy. dmesg gives this output:

[  171.261170] rtl8180: Bringing up iface
[  171.471390] rtl8180: Card successfully reset
[  172.552036] rtl8180: Setting SW wep key

and it also finds and identifies the wireless network correctly. The problem occurs when I try to connect.

Any suggestions?

---

### Post by Xfact0r82 on 2007-11-08
I am actually having the same problem, except when i first inserted the wireless card it worked fine, i was using a non-encrypted wlan, I then was at work and tried connecting the wlan there and now when ever i try to connect to encrypted or non encrypted my laptop just freezes and i have to pull the power.

So if anyone knows a way to reset wireless settings, that could be of some help thanks.

---

### Post by RocketRanger on 2007-11-08
Thanks for the Bump.

I actually got a bit further with this problem. I switched gnome's network manager for wicd (or something like that) to discover that it freezes when it tries to configure WPA. Weird thing is though that the card is setup to connect using WEP instead, which as I posted above it configures correctly.

Any suggestions?

---

