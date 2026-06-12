---
title: "Edgy freeze at startup"
date: 2006-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by skurpi on 2006-10-28
Ok here is the deal
I have a Acer Aspire 5024 with the Edgy release that was released on its official date (26th). So I install it, it seems to work fine, I update to kernel 2.6.17-17 and reboot. Now at the loading screen it freezes, around the second bar. I try to reboot a bunch of times, same thing. I try to boot trough single-user mode and it ommits this error:

[  122.110338] <0>Kernel panic - not syncing: Aiee, killing interrupt handler!

From there nothing happens, except that the fan is going to maximum speed (sounds like its working hard).

Anyone have any experience on this issue?

P.S. Before the update to the newer kernel it had the same problem, except that it actually booted on a random occasion.

---

### Post by dhughes on 2006-10-28
I experienced it too, plus a whole crapload of other errors. On my test (junk) AMD Sempron 64-bit system.

```
[ 47.624970] <0>Kernel panic - not syncing: Failed attempted to kill to intit!
```

---

### Post by annuzzer on 2006-10-28
I had the problem too after the installation of Edgy to my laptop. In my case the solution was very simple just add
> noapic
as a boot option to GRUB's menu.list in /boot/grub and you should get ahead...

Ann

---

### Post by skurpi on 2006-10-29
> **annuzzer said:**
> I had the problem too after the installation of Edgy to my laptop. In my case the solution was very simple just add

as a boot option to GRUB's menu.list in /boot/grub and you should get ahead...

Ann
well I cant seem to get that to work, i trye it in in a new line but when I try to boot its not saved. can you tell me the steps?

---

### Post by dhughes on 2006-10-29
I tried noapic and every boot option I could think of and it all ended in the same error. I even tried the "normal" 32-bit version and it failed too

 All install disks I used had their MD5 hash checked and verified to be good before I used them.

 It's no surprise even 6.06 won't work correctly on this same system that I tried to install Ubuntu on before. Actually the older version installed but was buggy, network OK but then suddenly no network, and after a reinstall, after wiping with DBAN, seemed to get worse? Weird.

 The system I want to use it on is just too odd, Ubuntu just isn't able to run on it, Debian works fine on it. It's an AMD 64-bit Sempron system, not sure about the chipset, the manual is around somewhere.

 The quest continues.

---

