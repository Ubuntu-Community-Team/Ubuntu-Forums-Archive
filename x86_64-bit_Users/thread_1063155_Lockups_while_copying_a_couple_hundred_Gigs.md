---
title: "Lockups while copying a couple hundred Gigs"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by u-slayer on 2009-02-07
I'm trying to copy a few hundred gigs from one hard drive to another. Every few minutes, the cpu usage for nautilus spikes up to 100% for a few minutes and firefox grays out and becomes unusable. Also, my transfer rate is only 16MB/s when I know both hard drives should be capable of 70-90+ MB/s. What is going on?

---

### Post by Yellow Pasque on 2009-02-07
I've always had problems moving large amounts of data with nautilus (though I admit I haven't tried lately).

I would suggest using the command line copy verbose mode (cp -v) so you can monitor the copy operation.

> when I know both hard drives should be capable of 70-90+ MB/s
Have you confirmed this with hdparm?

---

### Post by u-slayer on 2009-02-07
I would suggest using the command line copy verbose mode (cp -v) so you can monitor the copy operation.


Have you confirmed this with hdparm?[/QUOTE]

```
/dev/sdg1:
 Timing buffered disk reads:  272 MB in  3.01 seconds =  90.30 MB/sec

/dev/sda6:
 Timing buffered disk reads:  292 MB in  3.01 seconds =  96.95 MB/sec

```

dd has has the same problem for me.

However, when I use direct I/O from /dev/zero
```
dd if=/dev/zero bs=1M count=1000 oflag=direct of=test
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 13.2765 s, 79.0 MB/s

```

It behaves, normally.

---

### Post by dcstar on 2009-02-07
> **u-slayer said:**
> I'm trying to copy a few hundred gigs from one hard drive to another. Every few minutes, the cpu usage for nautilus spikes up to 100% for a few minutes and firefox grays out and becomes unusable. Also, my transfer rate is only 16MB/s when I know both hard drives should be capable of 70-90+ MB/s. What is going on?

Copying data at the filesystem level involves reads, writes, directory read updates, directory write updates and constant cache flushing to ensure data integrity - you will not get near the raw disk I/O transfer rate.

If you want faster EXT3 transfers then put things like this in your /etc/fstab options:
```

nodiratime,noatime
```

Add in performance suckers like the Tracker subsystem which constantly try to index stuff (I delete it on my systems) and it is no wonder things are slow.

---

