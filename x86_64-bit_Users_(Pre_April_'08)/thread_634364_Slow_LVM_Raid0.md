---
title: "Slow LVM Raid0"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by zeroflag on 2007-12-07
[http://zeroflag.de/zeroflag/HddResults_2007-12-07_20-57-45_1.xml]("http://zeroflag.de/zeroflag/HddResults_2007-12-07_20-57-45_1.xml")
these benchmarks were done on a LVM raid0 (at least that's what I think it is. how do I check?) using two raptor hdds.

when I do the benchmark on a single hdd (raptor or a common 7200rpm drive) I get almost the same values for throughput(around 50-70MiB/s).

any idea why the raid is so "slow"(/not any faster than a single drive)?

regards

---

### Post by fjgaude on 2007-12-07
Well, I have four Raptors, all 36 G, about the earliest ones. One does 44 MB/sec seq read using hdparm -tT /dev/sd[nn]. Two of them in mdadm raid0 got 80 MB/sec, three 114, four 104. I concluded the PCI bus was the limiting factor. I use a three-drive modern Seagate and get 114 MB/sec in raid5. A single Seagate gets 77 MB/sec. I'm about to get another MB that uses the PCI-E bus. <smile>

I can't say why you are getting what you get. The faster write than read is puzzling.

---

### Post by saru411 on 2007-12-08
> **zeroflag said:**
> [http://zeroflag.de/zeroflag/HddResults_2007-12-07_20-57-45_1.xml]("http://zeroflag.de/zeroflag/HddResults_2007-12-07_20-57-45_1.xml")
these benchmarks were done on a LVM raid0 (at least that's what I think it is. how do I check?) using two raptor hdds.

when I do the benchmark on a single hdd (raptor or a common 7200rpm drive) I get almost the same values for throughput(around 50-70MiB/s).

any idea why the raid is so "slow"(/not any faster than a single drive)?

regards

have you somehow managed to set up your drives in lvm and then from thos partitions make a raid0? if so tat could be the issue. you make a raid setup and once the raid partition is set up you can then use lvm on them.......maybe im wrong but this sounds like it might be where you are messing up.

hope i can help =)

---

### Post by zeroflag on 2007-12-08
> **saru411 said:**
> have you somehow managed to set up your drives in lvm and then from thos partitions make a raid0? if so tat could be the issue. you make a raid setup and once the raid partition is set up you can then use lvm on them.......maybe im wrong but this sounds like it might be where you are messing up.

hope i can help =)

iirc I used LVM from the alternate install cd (7.10 xubuntu). I first created 2 devices for lvm (one on each hdd), created a group for both (called it 'sysg') and then created a raid0/stripe device from that group... or at least I think that's how I did it.

anyway, the raptors have a individual sequential read speed of around 60-70MiB/s (tested it with my tool and with hdparm), my seagates get 55-65MiB/s but the raid0 device only gets 55-65MiB/s which is not any faster/even slower than the individual raptors...

any idea how to optimize/check/correct my stripe setup?

regards

---

### Post by saru411 on 2007-12-08
the way that i always set up my raid configuration is like this. first i make the hdds into the raid artions i would like(in your case 1 partition per hdd using the entire drive for each hdd.) from here i make my raid setup(your case using 2 raptors in raid0) once i have set up the raid device i then turn that raid partition into an lvm(your case 2 xxGB raptors in raid0 giving me xx+xx gb of hdd space to use as lvm).

---

### Post by Toet on 2007-12-09
Have a look at this:

[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/129488]("https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/129488")

The offered solution works:

sudo blockdev --setra 8192 /dev/vg/lv

I made a script to adjust the readahead setting of every logical volume in the volume group.

---

### Post by fjgaude on 2007-12-09
Wow, what a bug. Trust that it is soon fixed.

I guess we need more testers with more kind of machines and setups before releases, huh?

---

### Post by Toet on 2007-12-09
The bug is known since July, so it's not testing, it's priority it needs imho.

---

### Post by Toet on 2008-04-04
[[IMG]http://brainstorm.ubuntu.com/idea/2098/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/2098/)

---

