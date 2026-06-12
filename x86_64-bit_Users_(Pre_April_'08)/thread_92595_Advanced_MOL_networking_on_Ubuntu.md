---
title: "Advanced MOL networking on Ubuntu"
date: 2005-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jshamlet on 2005-11-19
Guys & Gals,
I have an interesting (I hope) question about networking and Mac on Linux.

My network uses "static" DHCP. Each workstation is assigned an IP address via DHCP, but the dhcpd server uses static addresses for "known" MAC addresses. It gets this from a local caching DNS server running on the same machine (this makes changing the network configuration easy)

Although for some bizarre reason, the Asante' Fast 690 card is failing to get its CORRECT reserved address, however it is getting an address (still trying to figure out that one) - and Ubuntu is a full fledged client.

So, enter MOL. I followed the directions on the wiki, but the Mac OS install keeps getting some arbitrary (apparently) address of 192.168.40.1. The rest of the network is on 192.168.0.x (with the primary gateway & dhcp/dns server on 192.168.0.1)

Clearly, this isn't working.

Did I miss something, or is there more to the dhcpd configuration than in the wiki?

Also, the sheep driver either isn't loading, or doesn't work. I'm not sure if it's the unique subnet mask, or that, that is preventing appletalk from working. I have an appletalk server on 192.168.0.2 that works when I native boot into Mac OS, but not in MOL.

I'm almost there - Mac OS is actually running full screen. If I could just get the networking cleared up...

Thanks!

---

