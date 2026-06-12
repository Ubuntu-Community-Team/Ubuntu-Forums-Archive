---
title: "Ethernet on powerbook G4"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by yg17 on 2006-02-06
I just installed Ubuntu on my PBG4 (it's the 2nd to last revision of 15" powerbooks). Everything went great, except its not detecting any network interface. ifconfig has absolutley no output at all. My PB is connected via an ethernet cable and it works fine in OSX.

---

### Post by calum on 2006-02-07
[QUOTE=yg17]I just installed Ubuntu on my PBG4 (it's the 2nd to last revision of 15" powerbooks). Everything went great, except its not detecting any network interface. ifconfig has absolutley no output at all. My PB is connected via an ethernet cable and it works fine in OSX.[/QUOTE]

Strange... I have the same model of PB, and it works fine.  Have you tried a "sudo ifconfig eth0 up"? Any relevant error messages in /var/log/messages?

---

### Post by ssam on 2006-02-07
does
```
sudo lshw
```
list it?

is there anything that looks relivent in
```
dmesg
```

---

### Post by dombleu on 2006-02-08
what do you have in /etc/network/interfaces?

Your network adapter should be configured in there.

Here's my working interfaces file to use a reference maybe:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0
```


Or try ifconfig -a, it will show up even interfaces that are knwon but down at the moment.....

---

