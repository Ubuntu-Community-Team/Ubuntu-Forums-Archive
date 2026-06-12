---
title: "USB wifi dongle gets REALLY slow after awhile"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by gdanko on 2008-12-01
I have a Shuttle K48 Cube. My network is wireless so I just put a wifi dongle in there and it seems to work great. After awhile though, performance degrades and pings to the router are long as 10000msec. If I restart networking the problem goes away for awhile but it returns.

Other computers aren't seeing this problem.

One thing I will note, I used this USB adapter using Ubuntu Hardy 32 bit and never saw this problem. I am now using Ubuntu Intrepid 64 bit.

---

### Post by gdanko on 2008-12-01
It's happening now. Here is a ping to my router from the Ubuntu host:

gdanko@shuttle:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3911 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=3347 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2714 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2871 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2243 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1749 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=2082 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=3436 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=3459 ms

And from my MacBook Pro

gdanko-mac:~ gdanko$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
64 bytes from 192.168.1.1: icmp_seq=0 ttl=64 time=2.461 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.284 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.280 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.580 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.296 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.348 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2.342 ms

I really can't figure out what's going on. :(

---

