---
title: "Wireless issues with AMD64 - Please help!!"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jamie565 on 2006-08-02
I am trying to get my Netgear WG511 (v.3) working with Dapper 64bit.  I have tried using the drivers on the netgear CD and using ndiswrapper to load them.  But it reports an error that the drivers are not 64-bit ](*,).

Has anyone had any joy with this? Or got any ideas? Should I just install the x86 version?

Thanks in advance...

---

### Post by John Jason Jordan on 2006-08-02
> **Jamie565 said:**
> I am trying to get my Netgear WG511 (v.3) working with Dapper 64bit.  I have tried using the drivers on the netgear CD and using ndiswrapper to load them.  But it reports an error that the drivers are not 64-bit ](*,).

Has anyone had any joy with this? Or got any ideas? Should I just install the x86 version?

Thanks in advance...

As far as I know, Ndiswrapper needs the 64-bit Windows driver. I have a Broadcom and found a 64-bit Windows driver on linuxant.com. They have Windows drivers for most chips, and usually a 64-bit version as well.

---

### Post by Jamie565 on 2006-08-02
Thanks for the reply...

I checked out linuxant, saw the WG511 listed, followed the link and was taken to the netgear website.  A 'WG511 64-bit' search revealed:

"Since there is a limited market for 64-bit drivers, and creating them is expensive, NETGEAR has no immediate plans to release 64 bit drivers for NETGEAR products. This would raise the cost of the products for all other customers. If you install the 64-bit operating system, all NETGEAR drivers and utilities on that computer may stop working!"

Surely this is possible...

---

### Post by a-musing amazon on 2006-08-02
I had a similar issue with my Netgear WG311 v2 (TI chipset), which I had previously had working fine with nsdiswrapper on a 32-bit Knoppix distro.

When Dapper came out I installed 64-bit Dapper which tried to run it with the native linux driver (acx100) but I never managed to get this to working properly and I then found, like you, that you can't use ndiswrapper because there is no Nettgear 64-bit Windows driver.

It would be nice if there was a way of running the 32-bit Windows drivers (as you can run 32-bit Firefox plugins using nspluginwrapper) but AFAIK no one has attempted to modify nsdiswrapper to allow this.

In the end I got myself an external WGE111 wireless bridge, since all Ubuntu 'sees' is the ethernet connection. You can then configure the Bridge using your browser. This is a bit like the difference between having an external dial-up model modem vs. having a winmodem.

The alteratives are:

1) As you suggest, use a 32-bit Dapper kernel and ndiswrapper.

2) Get a different wireless card with a compatible chipset and a native linux driver (e.g. atheros). I didn't try this myself because of the way that manufacturers tend to change their internal chipset on the fly and retailers are often unable to keep track of such changes (so, with the WG311, each of the 3 versions has a different chipset), and I could still end up with a new card that wouldn't work.

---

### Post by tymek666 on 2006-08-03
All acx100 based cards are supported since  ubuntu 5.04. I've never had problems using them. So what it your problem? Ubuntu didn't detect you card? What is iwconfig listing result?

---

### Post by a-musing amazon on 2006-08-03
It was some time ago (start of June when Dapper came out) - having then sorted things out by getting the bridge it was not something I've been concerned about since. As I recall the problem was with the WEP handshake with the Netgear Router (DG824).

Of course none of this helps the poster with the WG511, since there is no native driver for his card.

---

### Post by Jamie565 on 2006-08-03
My problem is that after blacklisting the prism54 (as per HowTos) and then ndiswrapping the XP drivers - ndiswrapper -l shows 'driver present, hardware present'.  But dmesg lists the non 64-bit issue with the driver and the system only lists a wired connection option.

Looks like it might be a new card...

Thanks for all responses...

---

### Post by tymek666 on 2006-08-03
So you used ndiswrapped to winxp drivers under 64 bit linux?

---

### Post by Jamie565 on 2006-08-06
Yes...with no success...

---

### Post by tymek666 on 2006-08-07
Well, if You think You can use 32bit winxp drivers under 64-bit winxp, You are wrong....THe same is with linux
Under 64bit linux we have native drivers for all acx100/axc111 based card that works.

---

### Post by a-musing amazon on 2006-08-07
Jamie can you please clarify which WG511 card you have?

According to the Netgear site there is no WG511 v3, just version 1 and 2, and of course the WG511T
(see [http://kbserver.netgear.com/products/WG511.asp)](http://kbserver.netgear.com/products/WG511.asp)).

According to "A survey of Linux and WiFi" ([http://users.linpro.no/janl/hardware/wifi.html](http://users.linpro.no/janl/hardware/wifi.html)) last updated 24-Apr-2006:

The WG511 (v1) uses a prism54 chip and is unsupported.

The WG511 v2 uses a Marvell 88w8335 "Libertas" chip and can be run using ndiswrapper (on 32-bit).

The WG511T uses a Atheros 5002G chip and can use the native madfi driver.

Only the last ofd these will run on a 64-bit Kernel.

---

### Post by c21367 on 2008-05-11
[http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

is a 64-bit driver.

---

