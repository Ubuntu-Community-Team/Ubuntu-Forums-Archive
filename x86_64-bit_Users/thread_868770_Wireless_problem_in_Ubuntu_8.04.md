---
title: "Wireless problem in Ubuntu 8.04"
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by samoo90 on 2008-07-24
Hey folks!
I've been wondering and trying to find this solution for weeks now.
Ever since i installed Ubuntu 8.04 (hardy) i haven't been able to get my wireless network card to work. Funny though that it says, that it's enabled/in use... I've also tried re-install Ubuntu 8.04, for checking if that would work - didn't help either. Even if I install all the updates i can find it doesn't help. Installing af software (like "WiFi-Radar" etc.) for managing wireless network, **doesn't help either!**

So now I've been wondering, if it's a missing software or driver of some kind I'm missing? I were really looking forwared to enjoy wireless in Ubuntu 8.04 (hardy).

Of course, here's my system specs.:

[B]Product: Acer Aspire 5520G
Default OS: Windows Vista (replaced by Windows XP Pro + Ubuntu 8.04)
Processor: AMD Athlon-64 x2 Dual-Core Processor, 
Video: nVidia GeForce 8400M G 128mb (RAM-usage: 896mb)
Wireless: Atheros 802.11 Wireless LAN (802.11b/g WLAN)[/B]

Help greatly appreciated!
Note: My understanding for Ubuntu is still pretty low, so detailed help would be great! :)

---

### Post by Melk79 on 2008-07-24
It doesn't seem like you're [alone]("http://ubuntuforums.org/showthread.php?t=863876&highlight=Atheros").

However, this [post]("http://ubuntuforums.org/showthread.php?p=5238628") appears to have a solution.

---

### Post by match002001 on 2008-07-25
Oh Athero cards.... If you have looked at my previous posts, I'm not a big fan of them but I have one and I have it working. 

Try this:

First load ndiswrapper from Synaptics.

Find the windows driver for your card(really all you need is the 8.inf file)

open terminal and type in:

```
ndiswrapper -i /PATH_TO_*.INF FILE/
```

then type:

```
modprobe wlan0
``` 

then type:

```
iwconfig
```

after that see if wlan0 shows up. if so then you're installed.

Then it's a matter of taking the thing off of roaming mode and configuring your wireless connection in System > Administration > Network

hope this helps

-Match

---

