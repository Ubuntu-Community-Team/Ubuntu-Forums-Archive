---
title: "Fed up of wireless problems recomend your cards please"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by backtrackme on 2008-01-07
I recently installed 64bit ubuntu on a seperate Partition with windows after istallation i realised that my usb wireless dongle would not work.
its a nintendo wifi dongle (in windows it uses custom drivers) its based on the buffalo WLI-U2-KG54-AI or WLI-U2-KG54-YB i tried a few different things but gave up.

now i'm looking for a new usb dongle that will work on the 64bit edition after searching the forums i could not find any please suggest some easy to install devices.

Is it worth buying a new one preferabley under £40 or should i downgrade to the 32bit edition.

Many Thanks

---

### Post by Joe Jarvis on 2008-01-07
The Ralink 801.22g chipsets have community-authored GPL drivers based on a GPL driver released by the manufacturer.  See the [rt2x00 project]("http://rt2x00.serialmonkey.com/") for details.  As best I can tell, that code is maintained [here]("http://git.kernel.org/?p=linux/kernel/git/ivd/rt2x00.git;a=summary"), primarily by Ivo van Doorn.

I'm waiting to make any wifi purchases until the project has drivers for the 802.11n draft 2.0 rt2800 chipsets.  Ralink recently released a GPL driver for it, and Ivo [announced]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=27923#27923") last week that he has started work on integrating it into the community's code.

---

### Post by u-blunt-2 on 2008-01-16
Eureka !
So can I speculate that any ralink-based wireless adapter will be supported by the AMD64 distro?

---

### Post by cubicsilver on 2008-01-16
I have a Broadcom chipset and its rock solid with ndiswrapper.

---

### Post by John Jason Jordan on 2008-01-17
> **cubicsilver said:**
> I have a Broadcom chipset and its rock solid with ndiswrapper.
The problem is that ndiswrapper may not recognize power management. I have a Netgear WG511 v2 that I use with ndiswrapper on my Thinkpad. When it is active I get about 1 hour battery life. A friend gave me a Netgear WG511 v1 that uses the Atheros chipset and is plug and play with Linux (no ndiswrapper required). When I use it I get about 2.5 hours battery life.

---

### Post by shad0w_walker on 2008-01-17
I can't speak for ralink and 64 bit specifically, but to my knowledge ralink drivers and the Ubuntu network manager don't work together well. It may have changed but the only way i get mine working is using either the Rutil tool, which is rather clunky (Good program but requires running as root so can't be setup to easily run at login) and allows me to use WPA or using WICD which works as long as you don't have encryption enabled.

I really hope this state of things changes because it's annoying to have GPLed drivers that don't work with any decent network managers.

---

### Post by Toffeeapple on 2008-01-17
[http://www.edimax.com/en/produce_detail.php?pd_id=1&pl1_id=1&pl2_id=44](http://www.edimax.com/en/produce_detail.php?pd_id=1&pl1_id=1&pl2_id=44)

That one works for me, out of the box without problem... on 32bit, I was assured though via email that it would also work on 64bit.. from here..

[http://www.linuxemporium.co.uk/products/wireless/#pid88170](http://www.linuxemporium.co.uk/products/wireless/#pid88170)

where I got it from..

:)

---

### Post by phekdra on 2008-01-20
> **u-blunt-2 said:**
> Eureka !
So can I speculate that any ralink-based wireless adapter will be supported by the AMD64 distro?

I wouldn't recommend it. I have a ralink rt61-based card and the rt61 drivers included with Gutsy stink and consistently drop the connection. They're now integrated with kernel 2.6.24 and in their latest incarnation they're a lot more reliable, but Ubuntu networking doesn't seem to like them. In order to get the network up I have to start wireless networking, stop it, remove the rt61pci module, modprobe it again and then bring up the network again. Don't ask me why this works, and nobody else seems to know either! :confused:

Phekdra

---

### Post by OttoDestruct on 2008-01-20
I don't know if theres a 64 bit build of Virtualbox that supports USB, but this is how I got the Nintendo dongle to work:

[http://ubuntuforums.org/showthread.php?t=640083](http://ubuntuforums.org/showthread.php?t=640083)

---

### Post by Bearraich on 2008-01-20
If you are still looking for a cheap USB adapter Tesco are selling a Phillips SNU5600 for about £20. I got one with a router about 18 months ago and have since bought another for emergencies. It works without ndiswrapper on 32 and 64 bit since 6.10. 

As far as I remember it is based on an atheros chipset. My network manager tells me the driver being used is zd1211rw. No problems using WPA2 although the connection is flaky using Deluge torrent client but not the Gnome bittorrent client.

---

### Post by u-blunt-2 on 2008-01-23
So what specific broadcom chipset is it ? 

Can anyone with properly working wireless PCI cards on AMD64 distro PLEASE state which brand/chipset they are using  ??? [-o<

I've given up on my marvell8335 chipset and am ready to dish out 40$ for an 'out-of-box' card...

---

### Post by gruss on 2008-01-23
WICD works for me on my wpa network at home?  no issues, broadcom on the dell works well with ndiswrapper.
Cisco Aironet abg pc card works out of the box in 64 bit as well as my D-Link PCI wireless card in my desktop, but thats 32 bit.

---

### Post by John Jason Jordan on 2008-01-23
> **u-blunt-2 said:**
> So what specific broadcom chipset is it ? 

Can anyone with properly working wireless PCI cards on AMD64 distro PLEASE state which brand/chipset they are using  ??? [-o<

I've given up on my marvell8335 chipset and am ready to dish out 40$ for an 'out-of-box' card...
I have a Netgear WG511 v2 card that uses the Marvel 8335. I got it working perfectly in Gutsy x86_64 with ndiswrapper. However, when I use it I find that I have only about one hour battery life. I attribute this to the possibility that ndiswrapper is not implementing power saving.

I also have a Netgear WG511T borrowed from a friend. This card uses (I believe) the Atheros chipset. It "just works." And my battery life is two and a half hours.

I also understand that the WG511 v1 cards "just work," but I don't have any direct knowledge of that. All I know is that you'd be best to stick with the WG511T. I bought my WG511 v2 card on eBay for $17, including shipping, so I'd suggest trying there first for the WG511T.

---

### Post by Melcar on 2008-01-23
I have [this one]("http://www.airlink101.com/products/awll3055.html") that I picked up at Fry's (they are the only ones that seem to carry this brand).  It works out of the box, with full WEP and WPA encryption.  Works with ndiswrapper too (extremely easy to set up compared to other chips).

---

### Post by kuja on 2008-01-24
Probably a bit more difficult to install, but I've found the Intel 3945 quite solid.

---

### Post by u-blunt-2 on 2008-01-26
> I have a Netgear WG511 v2 card that uses the Marvel 8335. I got it working perfectly in Gutsy x86_64 with ndiswrapper.

What drivers are you using, 64-bit windows ones ? Did you have any problems with modprobe ? 
Spent soo many hours on this card...?

Onyone getting a Desktop PCI card working ?

---

### Post by John Jason Jordan on 2008-01-26
> **u-blunt-2 said:**
> What drivers are you using, 64-bit windows ones ? Did you have any problems with modprobe ? 
Spent soo many hours on this card...?
Onyone getting a Desktop PCI card working ?
I forgot to mention that I had a helluva time finding 64-bit Windows drivers to use with ndiswrapper. I finally found them on a German site. Unfortunately I did not bookmark the page, so I can't give you the URL. Once you have the 64-bit windows drivers, ndiswrapper works as it is supposed to.

---

