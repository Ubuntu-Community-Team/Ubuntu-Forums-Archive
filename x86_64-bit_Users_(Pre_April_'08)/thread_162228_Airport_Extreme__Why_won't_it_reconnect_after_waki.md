---
title: "Airport Extreme:  Why won't it reconnect after waking up from sleep?"
date: 2006-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-04-18
I'm pretty sure this is a common issue and hopefully someone has a workaround, but whenever I wake my PowerBook from sleep I cannot reconnect to the base station I was originally using.  Wifi-Radar/iwconfig can't grab an IP address.  Networking won't see it either.  The problem is solved with a reboot, but I don't want to have to keep rebooting just to have Ubuntu see the base station and connect.

For those who are about to go "How the hell did you get it working," please see my reply in the "Exact steps..." thread.

PS my Airport extreme card is eth1.

---

### Post by NickDanger on 2006-04-19
I have the same problem on my iBook G4. Is there anyone that doesn't have this problem?

---

### Post by aimislame15 on 2006-04-19
go to terminal as root and type

dhclient eth1 (or whatever interface)

---

### Post by NickDanger on 2006-04-20
If I try this dhclient doesn't get any connection to the dhcp server (and times out after a while). Nothing helpful in /var/log/messages. Restarting the network (/etc/init.d/networking restart) doesn't help. Unloading and reloading the bcm43xx module does not help. However, I can see my access point and associate to it just fine.

Actually, my (and others, by the sound if it) initial failure of getting wireless to work was probably because the ibook had been sleeping before I experimented with the network.

If anyone has airport extreme working after suspend to ram, could you please report you hardware and kernel version. Maybe the problem is fixed upstreams?

---

### Post by bluemonki on 2006-05-11
I've got the same problem, though only since a major update a couple of days ago (Kernel, xorg etc).

*** UPDATE ***

Ok so doing:


#sudo modprobe -r bcm43xx

then

#sudo modprobe bcm43xx

Fixes it.  But I thought all the modules got removed from the kernel on sleep and re-inserted on resume.  Is there a list of them somewhere??   Or is it done by some magic tool?

---

