---
title: "could 'dhcdbd: Unrequested down ?:3' be related to system crashes?"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by nfriedly on 2008-01-26
My ubuntu system will crash once or twice a day with seemingly random circumstances. Today it was with only minesweeper open, other days it has been while browsing with firefox.

Today I rebooted and made a copy of everything in /var/log that had been modified recently, can you guys help me dig through and narrow down what the cuplrit is?

My house was also having some networking issues this morning, but that has not been the case during other crashes.

Here's a list of the files I have coppied (they're in the attached .tar.gz also):
acpid
auth.log
cups/access_log
cups/access_log.1.gz
daemon.log
debug
dmesg
dmesg.0
gdm/:0.log
gdm/:0.log.1
kern.log
messages
syslog
syslog.0
udev
user.log
wtmp
Xorg.0.log
Xorg.0.log.old

Here's the last couple of minutes from syslog.0: (What is --MARK-- ?)

```
Jan 26 13:30:29 nathan-desktop -- MARK --
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth0 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan 26 13:35:49 nathan-desktop avahi-daemon[4823]: Withdrawing address record for 169.254.3.110 on eth0.
Jan 26 13:35:49 nathan-desktop avahi-daemon[4823]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.3.110.
Jan 26 13:35:49 nathan-desktop avahi-daemon[4823]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 26 13:35:49 nathan-desktop avahi-daemon[4823]: Withdrawing address record for fe80::211:9ff:fe1b:1885 on eth0.
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) started... 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 26 13:35:49 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 26 13:35:51 nathan-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jan 26 13:35:51 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 26 13:35:51 nathan-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jan 26 13:35:51 nathan-desktop avahi-autoipd(eth0)[5240]: Got SIGTERM, quitting.
Jan 26 13:35:51 nathan-desktop avahi-autoipd(eth0)[5240]: Callout STOP, address 169.254.3.110 on interface eth0
Jan 26 13:35:51 nathan-desktop avahi-autoipd(eth0)[5241]: client: RTNETLINK answers: Cannot assign requested address
Jan 26 13:35:51 nathan-desktop avahi-autoipd(eth0)[5241]: Script execution failed with return value 2
Jan 26 13:35:52 nathan-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jan 26 13:35:54 nathan-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:35:57 nathan-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 26 13:36:01 nathan-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 26 13:36:09 nathan-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jan 26 13:36:22 nathan-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 26 13:36:25 nathan-desktop dhclient: No DHCPOFFERS received.
Jan 26 13:36:25 nathan-desktop avahi-autoipd(eth0)[5558]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jan 26 13:36:25 nathan-desktop avahi-autoipd(eth0)[5558]: Successfully called chroot().
Jan 26 13:36:25 nathan-desktop avahi-autoipd(eth0)[5558]: Successfully dropped root privileges.
Jan 26 13:36:25 nathan-desktop avahi-autoipd(eth0)[5558]: Starting with address 169.254.3.110
Jan 26 13:36:30 nathan-desktop avahi-autoipd(eth0)[5558]: Callout BIND, address 169.254.3.110 on interface eth0
Jan 26 13:36:30 nathan-desktop avahi-daemon[4823]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.3.110.
Jan 26 13:36:30 nathan-desktop avahi-daemon[4823]: New relevant interface eth0.IPv4 for mDNS.
Jan 26 13:36:30 nathan-desktop avahi-daemon[4823]: Registering new address record for 169.254.3.110 on eth0.IPv4.
Jan 26 13:36:34 nathan-desktop avahi-autoipd(eth0)[5558]: Successfully claimed IP address 169.254.3.110
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth0 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  avahi-autoipd running on eth0, assuming IPv4LL address 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  not touching eth0 configuration, was configured externally 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jan 26 13:36:34 nathan-desktop dhcdbd: Unrequested down ?:3
Jan 26 13:36:34 nathan-desktop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
```

this is from messages around that same time frame:
```
Jan 26 13:30:29 nathan-desktop -- MARK --
Jan 26 13:36:34 nathan-desktop dhcdbd: Unrequested down ?:3
Jan 26 13:36:50 nathan-desktop syslogd 1.4.1#21ubuntu3: restart.
Jan 26 13:41:01 nathan-desktop syslogd 1.4.1#21ubuntu3: restart.
```

Anybody have any ideas on what the problem could be?

---

### Post by EnkiduinNZ on 2008-01-26
I've no answer to your other questions but 'MARK' is just that, a mark to break up the log into chunks. It means nothing.

Cheers,

Cliff

---

### Post by TylerRick on 2008-05-07
> **nfriedly said:**
> My ubuntu system will crash once or twice a day with seemingly random circumstances. Today it was with only minesweeper open, other days it has been while browsing with firefox.

I'm having very similar problems as you. Mine system doesn't always crash every day, but it has been crashing 1-2 times/week for the last several months, and today it has crashed twice.

To clarify: By "crashes", I mean it either:
(1) suddenly stops giving any signal to my screens (the more common case by far)
(2) still shows the screens, but the mouse pointer is frozen

In both of those cases, nothing I did would cause it to wake up or respond. Even Ctrl-Alt-F1 and Ctrl-Alt-Backspace had no effect. It simply STOPS RESPONDING. And I'm preeeeeeeeetty darn tired of it.

I was hoping that upgrading to Hardy would fix all my stability problems but it has not.

```
> uname -a
Linux tyler-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

> tail -n1 /etc/lsb-release
DISTRIB_DESCRIPTION="Ubuntu 8.04"
```


> **nfriedly said:**
> 
this is from messages around that same time frame:
```
Jan 26 13:30:29 nathan-desktop -- MARK --
Jan 26 13:36:34 nathan-desktop dhcdbd: Unrequested down ?:3
Jan 26 13:36:50 nathan-desktop syslogd 1.4.1#21ubuntu3: restart.
Jan 26 13:41:01 nathan-desktop syslogd 1.4.1#21ubuntu3: restart.
```

Anybody have any ideas on what the problem could be?

Funny, I wondered that same thing when I was checking my logs today ("An _unrequested_ SHUT_down_, perhaps?!") and your post happened to be the first hit in Google for "Unrequested down"!

To answer your question, I don't think the "Unrequested down" message is related to our system crashes.

I think we simply got the error when our systems tried to acquire an IP lease via DHCP...

That error seems to be in proximity (in /var/log/syslog) to other DHCP messages, but **not** really in proximity to my system shutdown/crash...

```

...
May  7 15:06:25 tyler-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May  7 15:06:29 tyler-desktop kernel: [  125.049927] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/h
May  7 15:06:30 tyler-desktop kernel: [  126.052911] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/h
May  7 15:06:32 tyler-desktop dhclient: No DHCPOFFERS received.
May  7 15:06:32 tyler-desktop avahi-autoipd(eth0)[7624]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
May  7 15:06:32 tyler-desktop avahi-autoipd(eth0)[7624]: Successfully called chroot().
May  7 15:06:32 tyler-desktop avahi-autoipd(eth0)[7624]: Successfully dropped root privileges.
May  7 15:06:32 tyler-desktop avahi-autoipd(eth0)[7624]: Starting with address 169.254.9.74
May  7 15:06:33 tyler-desktop hcid[6772]: Default passkey agent (:1.19, /org/bluez/passkey) registered
May  7 15:06:33 tyler-desktop hcid[6772]: Default authorization agent (:1.19, /org/bluez/auth) registered
May  7 15:06:34 tyler-desktop NetworkManager: <info>  Updating allowed wireless network lists.
May  7 15:06:34 tyler-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no
May  7 15:06:37 tyler-desktop avahi-autoipd(eth0)[7624]: Callout BIND, address 169.254.9.74 on interface eth0
May  7 15:06:37 tyler-desktop avahi-daemon[6015]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.74.
May  7 15:06:37 tyler-desktop avahi-daemon[6015]: New relevant interface eth0.IPv4 for mDNS.
May  7 15:06:37 tyler-desktop avahi-daemon[6015]: Registering new address record for 169.254.9.74 on eth0.IPv4.
May  7 15:06:41 tyler-desktop avahi-autoipd(eth0)[7624]: Successfully claimed IP address 169.254.9.74
May  7 15:06:41 tyler-desktop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth0
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
May  7 15:06:41 tyler-desktop NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf.
May  7 15:06:41 tyler-desktop NetworkManager: <info>  avahi-autoipd running on eth0, assuming IPv4LL address
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
May  7 15:06:41 tyler-desktop NetworkManager: <info>  not touching eth0 configuration, was configured externally
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
May  7 15:06:41 tyler-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
May  7 15:06:41 tyler-desktop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0
May  7 15:06:41 tyler-desktop dhcdbd: Unrequested down ?:3
...

```

That's where the DHCP message was, but its timestamp was hours away from when my computer restarted...

```

May  7 17:22:58 tyler-desktop syslogd 1.5.0#1ubuntu1: restart.
May  7 17:22:59 tyler-desktop kernel: Inspecting /boot/System.map-2.6.24-16-generic
May  7 17:22:59 tyler-desktop kernel: Loaded 28313 symbols from /boot/System.map-2.6.24-16-generic.
May  7 17:22:59 tyler-desktop kernel: Symbols match kernel version 2.6.24.
May  7 17:22:59 tyler-desktop kernel: Loaded 36199 symbols from 102 modules.
May  7 17:22:59 tyler-desktop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu A
May  7 17:22:59 tyler-desktop kernel: [    0.000000] Command line: root=UUID=d0de4a55-6c22-41bc-bc4d-17b609f74a8d ro quiet splash
May  7 17:22:59 tyler-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
...
```

... so no relation to the crash, I'm afraid...

Let me know if you ever find a solution (or if you have already)!

---

