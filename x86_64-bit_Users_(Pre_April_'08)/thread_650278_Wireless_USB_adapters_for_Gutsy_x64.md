---
title: "Wireless USB adapters for Gutsy x64?"
date: 2007-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingkoopa on 2007-12-26
Hello there everyone. I've spent the last 10 days trying out live CDs of Ubuntu 7.10, Kubuntu, PCLinuxOS, and OpenSUSE and reading these and other Linux forums. Today I was about to install the i386 version of Ubuntu 7.10 when I realized, "hey wait a minute, doesn't this PC have a 64-bit CPU?" It has a Sempron 3400+. So I stopped the install process and considered downloading Gutsy x86-64. Immediately I thought that a major hurdle would be that my DWL-G122 Rev D1 wireless USB adapter wouldn't work in x86-64 since there are no 64-bit drivers available for it. I downloaded Gutsy x64 anyway and tried using ndiswrapper with the 32-bit WinXP drivers for the adapter but of course no dice. Also there was no boot splash like another thread mentioned.

So does anyone know of some wireless USB adapters for which there exist x86-64 Linux drivers? Or of a resource where I might find out for myself? I only have a wireless network in my house, no ethernet, and the router and DSL modem are in another room. Once you're able to connect to the net all the other pieces seem to fall into place, right?

Should I even bother throwing money at this? I could just install Gutsy i386. I'll be using this PC mostly for surfing the net, doing schoolwork (reports and presentations in OpenOffice), and programming (I'm a comp. sci. major 8-[ ). I thought that I read that Sun had already put out a 64-bit JRE...

---

### Post by dcstar on 2007-12-27
> **kingkoopa said:**
> 
...........
So does anyone know of some wireless USB adapters for which there exist x86-64 Linux drivers? Or of a resource where I might find out for myself? I only have a wireless network in my house, no ethernet, and the router and DSL modem are in another room. Once you're able to connect to the net all the other pieces seem to fall into place, right?
............

My Netgear WG111v2 works in 64bit Gutsy "straight out of the box", you probably need to look through the various Wikis for support for these devices.

---

### Post by kingkoopa on 2007-12-28
Thanks for the help, dcstar. I've looked at some [wikis]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") already and it seems that none of them indicate whether a wireless card or adapter works out of the box in 64-bit Ubuntu. So if an adapter is listed as working straight out of the box in one of the wikis, does that mean that it works straight out of the box in both 32 and 64 bit Ubuntu?

Also, by following kilz's 32-bit app howto, I was trying to get myself a 32-bit ndiswrapper in Gutsy x64 so that it might work with my WinXP32 drivers. Would that even be feasible? I think I was able to force the architecture of the utils package to x86, but the common package is suffixed with "-all" so I think that comes out to x64 anyway.

---

