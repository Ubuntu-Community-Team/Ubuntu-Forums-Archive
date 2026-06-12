---
title: "Memory Leakage, proftpd upload"
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by tommy_m on 2009-10-01
Hi,

Dont know if this is the correct place for this post but here goes:

Im running ubuntu 9.04 x86_64

kernel:
Linux echelon 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

My friend was downloading large amounts of data from my proftpd server. About 10GB of data at a rate about 1.4Mbytes/Sec. I saw in my system monitoring applet that the cache size was increasing fast and cleared the cache by typing:

**# sync; echo 3 > /proc/sys/vm/drop_caches**

anyway, it started to rise again when I went away from my computer. About ten minutes later my friend then called me asking why I had shutdown my ftp server. I got to the computer and just saw a blackscreen. X server was dead I though so I tried to get a TTy open by pressing ctrl+alt+f2 and so on. The computer did not respond so I had cold boot it. 

I tried looking through some logs but found nothing. I guess the cache go to big and crashed the system?

Can I tell my friend to download again and monitor what happends in some way?

/tommy_m

---

### Post by thesmurf on 2009-10-09
I have had a very similar experience with my memory cache climbing at a high rate. 

I am running the same x64 version of Ubuntu, 9.04. The major difference is that when mine climbs it is usually when I am in the middle of a fast (fios speed) download using transmission. It happens only when using transmission and is accelerated by an accelerated connection. I am constantly having to clear the cache or I won't be able to reboot or even operate the machine when it reaches 100%. 

So I am reaching out to the experts out there in search of a solution... I will gladly post what is needed to diagnose the problem. Thanks..

---

