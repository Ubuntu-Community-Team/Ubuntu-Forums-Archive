---
title: "iBook sleep/wake up: network connection lost"
date: 2006-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by rudolf on 2006-02-17
I searched the forum and noticed quite a few issues with iBooks' sleep/wake up functionality, but did not come up with a solution to following:

My iBook sleeps and wakes up as it should, but the network connection seems to get lost. It can be brought back up with ifdown eth0 && ifup eth0, but I think it should do so automatically since Mac OS X can do that too. I guess this could have something to do with DHCP-leases, since short sleep periods don't cause this problem, but when it sleeps overnight or so the manual interface revitalization is required, but I'm not sure if that's the case.

So if you know the solution, please be kind and share. :)

---

### Post by rudolf on 2006-02-22
Since no one seemed to have a solution to my problem, I tried to get a better idea on what's going on, and it seems that problem really is the DHCP-lease as I guessed. A long sleep (longer than DHCP-lease) causes the loss of connection, but running dhclient brings it back up, so it should be clear what's causing it.

Am I really the only one with this problem, since I guess many others run Ubuntu on iBook G4 800 MHz? (And no - I don't think I have done anything myself to screw this up, it worked this way right after install)

As a solution, is some script ran when the computer wakes up, so invoking the dhclient could be done automatically?

---

### Post by pvz on 2006-02-23
I'm running the Debian/testing PowerPC 2.6.15.4 kernel from [http://ppckernel.org/specialized.php](http://ppckernel.org/specialized.php) on my iBook G4 1,2Ghz instead of the stock Ubuntu kernel, which has some issues with sleep/wake. It runs fine and wakes up with working network  connection via dhcp. It only fails  to bring up sound, but this is fixed by adjusting the volume in kmix.

---

