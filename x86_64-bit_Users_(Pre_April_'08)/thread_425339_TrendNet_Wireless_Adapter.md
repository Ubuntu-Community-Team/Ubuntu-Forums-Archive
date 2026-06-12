---
title: "TrendNet Wireless Adapter"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by u-blunt-2 on 2007-04-27
Howdy Folks !

So the main thing holding me back from upgrading to amd64 Feisty is my wireless PCI card. I have a TEW-423pi card, which doesn't have proprietary linux drivers. 

I can get the card running using ndiswrapper on x86 Edgy. However, the amd64 build would not recognize the drivers. TrendNet does not have 64 bit drivers available for download. 

I recently noticed that their website has a Winblow$ Vista howto installation guide ; there is hope !

Has anyone been able to use this card (or something similar) on 64bit Feisty ?  I read somewhere that perhaps  my wifi card would be detected with restricted-modules... Is this plausible ?
Is there some way I connect to my wireless network without buying another adapter ?

I can't wait to get the most bang out of my buck...

---

### Post by go_beep_yourself on 2008-01-04
> **u-blunt-2 said:**
> Howdy Folks !

So the main thing holding me back from upgrading to amd64 Feisty is my wireless PCI card. I have a TEW-423pi card, which doesn't have proprietary linux drivers. 

I can get the card running using ndiswrapper on x86 Edgy. However, the amd64 build would not recognize the drivers. TrendNet does not have 64 bit drivers available for download. 

I recently noticed that their website has a Winblow$ Vista howto installation guide ; there is hope !

Has anyone been able to use this card (or something similar) on 64bit Feisty ?  I read somewhere that perhaps  my wifi card would be detected with restricted-modules... Is this plausible ?
Is there some way I connect to my wireless network without buying another adapter ?

I can't wait to get the most bang out of my buck...

I've also got a Trednet, but it is a model tew-424ub. With ndiswrapper, It works fine in 32 bit Backtrack 2 and Backtrack 3 beta Linux that boot off my usb stick, but it does not work with the 64 bit kernel I compiled in Ubuntu 7.10. I've done a lot of posting on different forums and mailing lists, and have not came up with any solutions yet except for a few of my own. Since my computer that I'm using wireless on isn't mobile, this will work just fine for me. Since you are using a wireless pci card, I assume that your computer is a desktop, and this will work for you too. I found a really old computer somewhere between 200~400 mhz. I'm going to install Linux on it without a gui. I'm considering CentOS, Debian, DSL, and some other non Linux systems for it such as Minix 3 and GNU FreeDOS, but those may not support my hardware and ndiswrapper. So I will use the wireless usb network adapter on the slow computer using a 32 bit Linux distribution probably, and I will also add a pci ethernet network adapter to it. Actually, now that I think about it, Shorewall or IPCops for a nice web interface and Firewall. Also I need this computer to be a print server because the printer is too far away from my computer, but it can be reached through an ethernet cable easily. On the slow computer, I will use this software to bridge the two network interfaces. [http://linux.about.com/cs/linux101/g/bridgeutils.htm](http://linux.about.com/cs/linux101/g/bridgeutils.htm) The wireless adapter will send and receive from and to the router, and everything passing through it will go to the pci ethernet network adapter and through a crossover cable to the second nic that is on my 64 bit Ubuntu desktop (may switch to Fedora 8 64 bit soon). I emailed to some emails I found at [www.linuxant.org](www.linuxant.org) to see if their software similar to ndiswrapper will work with 32 bit drivers in 64 bit Linux.

---

### Post by u-blunt-2 on 2008-01-14
Any news ?
Did you manage to get the driver working in 64-bit ?
The 423PI is a PCI card. I don't know if USB adapters are easier/harder to install..

---

### Post by go_beep_yourself on 2008-01-18
I've got a solution but I dont feel like writing it all here. Contact me through voice conferencing. I've got Ekiga and Skype in Linux, and I'll setup Linphone if that's what you'd like to use. If you are a Kubuntu user, then get a copy of Kphone and give me a call.

---

### Post by go_beep_yourself on 2008-05-11
Nope, not yet. I thought I could share the wireless internet from a computer using a 32 bit OS, but the wireless card makes that computer lock up, so the hardware is probably too old to handle a new wireless usb network adapter. That's my guess. What about you? Did you manage to get the wireless lan card working with a 64 bit os working yet?

---

