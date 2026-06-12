---
title: "CPU usage really high on idle system"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tritan on 2006-09-08
Hello,

O`m having trouble running my Ubuntu install smoothly on my 64-bit machine. I installed it yesterday and I could work just fine on it. Today however the CPU goes up to 100% load constantly, making working on it impossible :( 

When I run `dmesg` in a terminal I get to see alot of these messages:

```
"[ 1046.087753] APIC error on CPU0: 08(08)" and so on...
```

I`ve been looking for a solution on Google and these forums, but I haven`t found anything usefull. 

The last thing I did yesterday before my machine got slow was updating my software using the update manager which went without a problem. Before the problem started I installed ndiswrapper which works just fine now. 

Since I am sort of new to Ubuntu (and I would love to use it as a replacement for Windows XP) I don`t know what to pay attention to for the troubleshoot. Some of the caracteristics of my PC:

AMD64 3200+ (CnC enabled)
Asrock 939dual-sata
1GB PC3200 dual channel (will do memtest after this post just to make sure)
2 x 74GB 10K RPM Raptors in software raid
nvidia 7800 GTX 

As you can see there are some factors which can might the problem (chipset of the motherboard? Raptors in Raid? Videocard drivers? BIOS settings?)

xorg, dd and metacity are currently processes which according to the system monitor are using alot of CPU (especially `dd` is really high).

Please help me with fighting this problem - don`t make me switch back to Windows again :p 

Thanks in advance,

Tritan

---

### Post by Tritan on 2006-09-08
What I forgot to mention is that I run Ubuntu x64, I installed using the alternate installation CD because of raid.

---

### Post by professor_b on 2006-09-08
hmmm. maybe try booting with the noapic option? It is worth a shot, I guess.

---

### Post by kuja on 2006-09-08
Worth a shot to kill the processes. Try changing video drivers as that could *potentially* cause a problem such that Xorg would be unstable or use massive amounts of cpu power. (note: nv is rather buggy, go for vesa or the proprietary drivers.

One question, Have you done anything "special" to your setup?

---

