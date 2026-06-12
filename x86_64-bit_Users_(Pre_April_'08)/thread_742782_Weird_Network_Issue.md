---
title: "Weird Network Issue"
date: 2008-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by arbeck on 2008-04-02
I just installed gusty, and everytime I reboot, my network stops functioning.  I can get it to work again by changing it to DHCP, saving, coming back in, and restoring it to what it was.  Has anyone seen this before?

---

### Post by felker2 on 2008-04-02
Have you search dmesg and /var/log/syslog for eth/network related messages?

---

### Post by arbeck on 2008-04-02
When I first boot, this is the last message in dmesg:

eth0: no IPv6 routers present

When I switch to DHCP, I get this message:

NET: Registered protocol family 17

Then when I switch back to the standard config I get this in dmesg:

r8169: eth0: link up
eth0: no IPv6 routers present

---

