---
title: "Setting the nameservers in Breezy"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jon_gunnar on 2005-12-16
How is the nameservers set in  /etc/resolv.conf. I would like to set up a spesific pair, and have tried to change everything I can find, but they are changed back almost as fast.
Even changed /etc/resolvconf/resolv.conf.d/original

Anyone got a clue, I would be very happy.

---

### Post by Zimmer on 2005-12-16
Have you tried
System>Administration>Networking....?
to alter the DNS settings?

Zimmer

---

### Post by Gandalf on 2005-12-16
resolv.conf is changed automatically in case you have a DHCP connection, if you want to fix them you have to make it static , try to do this:

edit /etc/network/interfaces
Change
```

iface eth0 inet dhcp

```
(suppose eth0 is your interface)

to
```

iface eth0 inet static
       address 192.168.X.X
       netmask 255.X.X.X
       network 192.168.X.0
       broadcast 192.168.X.255
       gateway 192.168.X.X
       dns-nameservers XXX.XXX.XXX.XXX XXX.XXX.XXX.XXX

```

the addresses after dns-nameservers will be in ur resolv.conf, and of course change the XXX to suit ur needs

---

### Post by jon_gunnar on 2005-12-16
[QUOTE=Zimmer]Have you tried
System>Administration>Networking....?
to alter the DNS settings?

Zimmer[/QUOTE]

Yes, but that makes no difference at all.

---

