---
title: "[SOLVED] Network fluctuations"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by Porpoise on 2008-06-12
I'm having a really weird network issue. I've checked the router setup and other installations on the same machine and other machines on the network and they're all managing approx. 1763Kbps download speed and 327Kbps upload speed on a 2Gbps DSL line, so the issue is specific to this installation:

[IMG]http://srenterprises.co.uk/system.png[/IMG]

The issue is this:

the connection fluctuates between no throughput and slow throughput so the internet connection is very intermittent and is a real pain when browsing or trying to download/upload data as it stops and starts at very short intervals. I just can't get to the bottom of this, so any help would be greatly appreciated. The system was working fine up until very recently, so I suspect it may have been something that went awry during/because of some update(s) or other - except I have no idea which update(s) may have been the culprit.

I have recently installed myth and several other TV applications in an attempt to get my TV tuner working (without success) so that could be a possibly suspect area...

---

### Post by Porpoise on 2008-06-13
Problem solved! It seems that the network device (eth0) got reset at some point to dhcp. It seems it only functions correctly if set to roaming?!?

---

