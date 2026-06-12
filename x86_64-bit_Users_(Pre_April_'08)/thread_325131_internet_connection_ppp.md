---
title: "internet connection ppp"
date: 2006-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by encikraju on 2006-12-25
i have setup pppoeconf and everything went well but after reboot, it seems doesn't automatically connect to the internet.i'm using broaband with username and password and i already  config pppoe to connect automatically when startup.any ideas?:-k

---

### Post by NeoLithium on 2006-12-25
```
sudo gedit /etc/network/interfaces
```

The lines near the bottom, move them around so it looks like this:
```

[COLOR="Red"]pre-up /sbin/ifconfig eth0 up #line maintained by pppoeconf[/COLOR]

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

```
Make sure the red line of text, is above the DSL provider information.

---

