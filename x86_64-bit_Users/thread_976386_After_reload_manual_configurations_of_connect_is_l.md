---
title: "After reload manual configurations of connect is lost"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by Helix_Nebula on 2008-11-09
I've got some problem with NetworkManager Applet 0.7.0 - it doesn't save manual configuratons of connect(IPv4) after reboot.

I want to NetworkManager don't do that and save configuration.

---

### Post by cariboo on 2008-11-09
See this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/283233](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/283233)

I had the problem on my server where all of a sudden the ip address would change to an dhcp assigned address. I just disabled dhcp3-client and have had no problems since. To disable dhcp3-client

```
sudo apt-get purge dhdcp3-client
```

If that causes problem you can always reinstall the dhcp3-client

Jim

---

