---
title: "Wireless Network Discovery"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by farruinn on 2006-05-12
This is one of greatest features I find lacking in Ubuntu, the ability to recognize wireless networks automatically. I've installed kismet and changed the source line in /etc/kismet/kismet.conf to
```
source=orinoco,eth0,airport
``` for my 900Mhz iBook G3. Now when I run kismet I get this error:
```
Source 0 (airport): Enabling monitor mode for orinoco source interface eth0 channel 6...
FATAL: channel get ioctl failed 95:Operation not supported
``` I take it this means I need the kernel patch for the orinoco driver (grrr). I really don't want to have to mess with kernel patches. Are there any other solutions? Kismet looks to be very powerful but it also seems to be rather complex when all I want is a gnome applet with a list of available networks. :-k

---

### Post by david.cab on 2006-05-12
[QUOTE=farruinn]This is one of greatest features I find lacking in Ubuntu, the ability to recognize wireless networks automatically. I've installed kismet and changed the source line in /etc/kismet/kismet.conf to
```
source=orinoco,eth0,airport
``` for my 900Mhz iBook G3. Now when I run kismet I get this error:
```
Source 0 (airport): Enabling monitor mode for orinoco source interface eth0 channel 6...
FATAL: channel get ioctl failed 95:Operation not supported
``` I take it this means I need the kernel patch for the orinoco driver (grrr). I really don't want to have to mess with kernel patches. Are there any other solutions? Kismet looks to be very powerful but it also seems to be rather complex when all I want is a gnome applet with a list of available networks. :-k[/QUOTE]
Did you run kismet as super user, "sudo kismet"?

"iwlist eth0 scanning" also gives you a list of available wireless networks, try it and see if it works.

---

### Post by farruinn on 2006-05-12
Yes, I ran it as sudo. I just realized I had eth0 in kismet.conf, not eth1. I fixed it and now it does indeed tell me explicity to patch my orinoco driver :/

Using iwlist also says scanning isn't supported, but maybe patching the driver will fix that too.

*bracing himself for kernel patching, yuck*

---

### Post by ssam on 2006-05-14
the driver in dapper supports scanning.

---

### Post by farruinn on 2006-05-14
I'll just wait for dapper then :)

---

### Post by aimislame15 on 2006-05-14
Why don't you just update now? I find that it is very stable on my iBook G4 and about 80% on my G5.

```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

