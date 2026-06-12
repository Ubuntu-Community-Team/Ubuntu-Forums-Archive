---
title: "Xeon Kernel on Edgy"
date: 2007-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by koara on 2007-03-17
Hello all,

i tried to upgrade my kernel from generic (2.6.17-11-generic on Edgy x86_64 core2duo) to xeon and failed. 

First i tried to download, configure and build my own (2.6.20 plus some patches). All went fine but then fails at boot time:
```

Waiting for root file system...

```

waits for a couple of minutes and then..
```

ALERT! /dev/sda6 does not exist. Dropping to a shell!

```

Fortunatelly booting with the old kernel still works without any problems.

I searched countless threads and how-tos and tried many proposed solutions (using yaird instead of initramfs-tools, reinstalling udev..) none of which helped.

Then i gave up and tried apt-getting linux-amd64-xeon from repositories. Nothing happened and the package details show that only two documents got installed, both into /usr/share/doc... Why is that?

As of now i am fairly frustrated, can someone with a similar setup please explain how they got their kernel upgraded?

Cheers

---

### Post by vnbuddy2002 on 2007-03-17
It seems to me that the kernel that you tried to compile did not include the sata driver . Did you try to login into the old kernel and try to issue the following command before you do the compiling?


sudo make oldconfig

---

### Post by kleeman on 2007-03-17
> **koara said:**
> Hello all,

i tried to upgrade my kernel from generic (2.6.17-11-generic on Edgy x86_64 core2duo) to xeon and failed. 

First i tried to download, configure and build my own (2.6.20 plus some patches). All went fine but then fails at boot time:
```

Waiting for root file system...

```

waits for a couple of minutes and then..
```

ALERT! /dev/sda6 does not exist. Dropping to a shell!

```

Fortunatelly booting with the old kernel still works without any problems.

I searched countless threads and how-tos and tried many proposed solutions (using yaird instead of initramfs-tools, reinstalling udev..) none of which helped.

Then i gave up and tried apt-getting linux-amd64-xeon from repositories. Nothing happened and the package details show that only two documents got installed, both into /usr/share/doc... Why is that?

As of now i am fairly frustrated, can someone with a similar setup please explain how they got their kernel upgraded?

Cheers
The xeon kernel has been dropped because the devs claim it adds no performance over the generic kernel. The package you got is just a dummy one from earlier days when there really was a xeon kernel (Dapper).

---

### Post by koara on 2007-03-17
Hello folks, an update on the issue:

Thank you kleenex for the info, i wish someone had bothered to put that simple sentence into the linux-amd64-xeon package description (instead of the confusing "Obsoleted by linux-generic. Used only for upgrades."). The performance difference is no big  issue for me --  all i wanted is basically a newer kernel.

vnbuddy2002: Yes i copied all the defaults from the old (functional) config. However after reading your reply i went back and set SATA support manually (selecting AHCI and IntelPIIX SATA), as it was deselected. Built, installed and it seems to work now. Issue solved.

Cheers everyone!

---

