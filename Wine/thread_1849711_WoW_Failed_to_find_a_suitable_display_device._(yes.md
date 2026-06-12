---
title: "WoW: Failed to find a suitable display device. (yes, another one)"
date: 2011-09-25
forum: Wine
---

### Post by ptn107 on 2011-09-25
I'm getting the classic error "Failed to find a suitable display device. Exiting program." from Wow.exe.

More detailed error here: _[http://paste.ubuntu.com/696534/]("http://paste.ubuntu.com/696534/")_ It just repeats over and over.  Launcher runs fine.

I'm running wine 1.3 (1.3.28-0ubuntu1) and am using the latest version of the Nvidia display driver provided by Ubuntu (280.13-0ubuntu3) in Ubuntu 11.10 x64.  The nvidia display driver is installed, configured correctly, and shows it's being used (see attached screenshot):
```

           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7800 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: **driver=nvidia** latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:ce000000-ceffffff memory:b0000000-bfffffff memory:cd000000-cdffffff memory:cfee0000-cfefffff
```

nouveau is blacklisted.

Tried wine1.2 and 1.3 both do the same thing.

---

### Post by ptn107 on 2011-09-26
bump

---

### Post by Tweak42 on 2011-09-27
I found a work around here:
[http://ubuntuforums.org/showpost.php?p=11288794&postcount=3](http://ubuntuforums.org/showpost.php?p=11288794&postcount=3)

> **xethm55 said:**
> As a temporary work around, you can prefix your wine command with the following:
```
LD_PRELOAD=/usr/lib32/nvidia-current/libGL.so
```
If you have an NVidia card, something similar should exist for AMD/ATI cards

---

### Post by ergo-proxy on 2011-09-29
Great! Please mark the topic as solved, thank you.

---

