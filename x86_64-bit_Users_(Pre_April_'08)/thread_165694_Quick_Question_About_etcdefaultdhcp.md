---
title: "Quick Question About /etc/default/dhcp"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-04-25
Can someone tell me what they have listed for INTERFACES in their /etc/default/dhcp?  I think I may have found my answer to the other post below.

My Airport is eth1 and my ethernet port is eth0.  I cannot recall if there was anything there prior to adding tun0 (installing and configuring MOL).

This is what my /etc/default/dhcp looks like right now:

```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="tun0"

```

---

### Post by AlphaMack on 2006-04-25
Never mind...I'm just blathering to myself here.  Carry on.

---

