---
title: "Slow USB transfer rate"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jgl75 on 2007-04-20
Hello everybody !

I'm new to Ubuntu.

I've installed Ubuntu server 6.10 without any problem.
This computer will act as a vmware host for my test environment.

Everything went fine until I copied my virtual computers from my external HDD to the freshly installed Ubuntu...
I only have 1000Kbytes per second of transfer speed :(.

- The computer is a Dell Dimension E520 with Core2Duo 6600.
- I'm sure that I have USB 2.0 (it was working fine under Windows XP).
- The hdd is detected as connected to 480mbps USB.
- I already tried to mount it with the async option.
- The HDD is formatted in NTFS

I have more than 100Gig of file to copy so PLEASE help :)

Thanks in advance.

Jgl75

---

### Post by MaestroMaus on 2008-07-22
I had the same problem. I found out it's a known bug.
Until it is permanently fixed, I did this to make it work:

In the console, type:
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd

This idea came from someone else on the internet. His method didn't work for me so I changed it until it did. If this doesn't work for you, you could take a look at his method:
[https://bugs.launchpad.net/ubuntu/+bug/177235]("https://bugs.launchpad.net/ubuntu/+bug/177235")

---

