---
title: "Networking issues wired and wireless"
date: 2008-04-23
forum: x86 64-bit Users
---

### Post by nray on 2008-04-23
So I had been running 32-bit Ubuntu/Mythbuntu 7.10 without any problems, and recently upgraded the memory in my machine to 8GB.  First I tried the server kernel with PAE so I could use all the RAM in 32-bit mode, but discovered there are no restricted drivers available for the server kernel, so I decided to try Mythbuntu 7.10 AMD64.

Wired networking is on-board Marvell 88E8056 gigabit ethernet, and wireless is an Abit Airpace (Atheros AR5007EG) 802.11g.  Both worked great in 32-bit, though I had to download and compile the source to ndiswrapper to get the AR5007EG working with the WHQL XP driver 5.3.0.56 (the open-source Atheros driver currently has a bug detecting the AR5007EG properly because it re-uses the same PCI identifier the AR5006 series uses, and the ndiswrapper in the gutsy package system is version 1.3, which also has bugs with the AR5007EG, which were fixed in later versions of ndiswrapper).

In many weeks of use, neither wired (Marvell 88E8056) or wireless (Atheros AR5007EG) gave me a moment of trouble in 32-bit.

In 64-bit, it's another story.  It first appeared there was a dhcp issue with the Atheros AR5007EG using ndiswrapper (1.52) and the WHQL XP 64-bit 5.3.0.56 drivers, because it had no trouble seeing other wireless networks, it would just timeout during dhcp request.  So I manually set all the IP and wireless network information, yet that made no difference (pings to the gateway IP would time out).

Then I tried an ASUS WL-167G USB 802.11g adapter (RaLink RT2500USB), which I'd read should just work out of the box with 7.10, and it was recognized, but nothing I did could get it to connect to my wireless network in 64-bit Mythbuntu 7.10, apparently the same symptoms I saw on the AR5007EG!  I removed it and rebooted.

During this 64-bit testing, most of the time the wired connection was fine, however sometimes it would drop and not come back while I was trying different wireless settings in the Network control panel (but if I rebooted it would come back).  Annoyed with that, I changed the wired connection from auto-roam to dhcp, and the wired connection just stopped working even across reboots, which I find just bizarre.

Anyone have any idea what is going on?  Something seems seriously fubar.  I've never had this much trouble with any linux distro.

---

### Post by nray on 2008-04-24
Ok, since I haven't gotten any replies, I decided to start trying the non-intuitive things.

Leaving my wired connection set up with roaming mode off and dhcp on, and wireless set up manually with a static IP and manual connection settings to my wireless router, I UNCHECKED the wireless connection in the Network Settings GUI panel and closed it, and guess what?  Wireless works, and wired works too.

Could someone now explain what is going on?  This behavior seems the near exact opposite of what it should be doing.

---

### Post by kutjara on 2008-04-25
I feel your pain. I had similar problems trying to get a Broadcom BCM4328 wireless card working with NDISWrapper in 64 bit hardy. In the end, I got the card working, but couldn't for the life of me make WPA work (which pretty much made the card useless).

I have an Atheros AR5007EG on my Acer Aspire standby laptop. I'm running 32 bit Hardy on it, but the card works beautifully with the prepatched driver you can download from here:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

This fixed the problem Madwifi had with this card (at least it did for me).

When I couldn't get the Broadcom card in my primary laptop to work in 64 bit Hardy, I bought a Belkin F5D5070 (which uses the Ralink rt73 chipset). I installed the Serialmonkey drivers ([www.serialmonkey.com](www.serialmonkey.com)), and they worked perfectly (with WPA and everything). You should also use the RutilT GUI network manager, which can be downloaded from the same site, and works nicely with the driver.

If you haven't already, give these solutions a try, and let me know how it goes.

---

### Post by nray on 2008-04-27
> **kutjara said:**
> I have an Atheros AR5007EG on my Acer Aspire standby laptop. I'm running 32 bit Hardy on it, but the card works beautifully with the prepatched driver you can download from here:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)


That is not an option for me in 64-bit:

[http://madwifi.org/wiki/Releases/0.9.4]("http://madwifi.org/wiki/Releases/0.9.4")

"An experimental patch that adds AR5007 support at least for i386 (32bit) is attached to ticket #1679"

ndiswrapper is my *only* option in 64-bit, and it definitely does not work in 7.10, and I just tested 8.04, and while 8.04 solved the wired networking total wackiness and includes the usable ndiswrapper 1.50 instead of the older buggy 1.43, ndiswrapper still doesn't work.

And a word of warning to anyone trying the 7.4.2.75 with ndiswrapper from the [http://www.atheros.cz/]("http://www.atheros.cz/") website - don't.  I did a ndiswrapper -i netathwx.inf and it appeared to work, but on reboot 7.10 and 8.04 *will* hang, 8.04 throwing the error "udevd-event[3179]: run_program: 'sbin/modprobe' abnormal exit".

So if anyone is going to try ndiswrapper in 64-bit with the AR5007EG, stick with the 5.3.0.56 drivers (not that I've gotten them to work, but at least ndiswrapper doesn't lock the computer up on boot with them).

---

### Post by nray on 2008-04-29
Found a solution -

In at least 64-bit Ubuntu 8.04, with the ndiswrapper package (version 1.50 at the time of this writing), using the XP x64 5.3.0.56 driver, it is absolutely necessary to put this line into /etc/network/interfaces under iface wlan0 with your AR5007EG's hardware ethernet address where 00:00:00:00:00:00 is:

pre-up /sbin/ifconfig wlan0 hw ether 00:00:00:00:00:00

With that line in place, things worked they way they should in 64-bit.  I didn't need that line in 32-bit Ubuntu 7.10 with ndiswrapper, but I needed it in 64-bit.

---

### Post by Sockerdrickan on 2008-05-11
Didn't work for me I have 5006EG
locks up at login, gonna have to reinstall Ubuntu because revert the changes doesn't help.

---

### Post by Sockerdrickan on 2008-05-11
may ndiswrapper burn in hell, this is not the first time it ruins Ubuntu for me.

---

### Post by Yellow Pasque on 2008-05-11
Hey now, ndiswrapper does a good job for me. It all depends on the quality of the Windows drivers you're using it with.

---

