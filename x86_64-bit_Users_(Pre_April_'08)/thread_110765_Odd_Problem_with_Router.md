---
title: "Odd Problem with Router"
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by sgithens on 2005-12-31
I have a 12" 1ghz iBook G4 with Ubuntu 5.10 and a cable modem.

When I plug into the cable modem with an ethernet cable, DHCP and all networking works fine.

Recently I've added a Netgear MR814 v1 router on top.  I have a WinXP desktop and notebook that both connect to it via ethernet, and fetch an address. 

However, the Ubuntu iBook just doens't seem to be able to connect to this router and get an address, or anything else.  I've tried switching ethernet cables, assigning it an address on the router setup and trying to connect with a static address... all to no avail. I also can't connect to the router's configuration url.

After being on for about 15 minutes the Ubuntu iBook as received 190 packets and sent 45 according to the Connection Properties.

I connect to lots of places using the Ethernet adapter, and can't figure out why it can't find this router.  Any ideas?

Thanks,
Steve

---

### Post by Swab on 2005-12-31
Is your cable modem also a router?  Does it assign internal IP addresses?  If so perhaps your problem is from double NATing... you could try disabling DHCP on the new router and plugging the modem into one of the numbered ports instead of the uplink port on the new router.... in effect using it as a switch instead of a router.

---

