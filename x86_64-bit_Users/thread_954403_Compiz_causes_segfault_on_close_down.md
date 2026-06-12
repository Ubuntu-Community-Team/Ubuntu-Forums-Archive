---
title: "Compiz causes segfault on close down"
date: 2008-10-21
forum: x86 64-bit Users
---

### Post by tachum on 2008-10-21
I posted this a week or two before but I wasn't able to provide much info. The laptop (ASUS W7S) runs 100% except on shut down when the progress bar gets about half way and crashes, with a 'white screen of death'.

I have run off the dmesg etc and the problem appears to be a compiz crash, as per kern.og

Oct 21 21:22:13 garry-laptop-64 kernel: [ 1310.321632] __ratelimit: 3 callbacks suppressed

[B]Oct 21 21:22:13 garry-laptop-64 kernel: [ 1310.321639] compiz.real[6500]: segfault at 19 ip 000000000041024e sp 00007fff07864e00 error 4 in compiz.real[400000+3b000]
[/B]
Oct 21 21:22:22 garry-laptop-64 kernel: [ 1319.418167] ip6_tables: (C) 2000-2006 Netfilter Core Team

Oct 21 21:40:05 garry-laptop-64 kernel: Inspecting /boot/System.map-2.6.27-7-generic

Oct 21 21:40:05 garry-laptop-64 kernel: Cannot find map file.

Oct 21 21:40:05 garry-laptop-64 kernel: Loaded 72999 symbols from 105 modules.

Oct 21 21:40:05 garry-laptop-64 kernel: [    0.000000] Initializing cgroup subsys cpuset

Any ideas on how to fix this???
Many thanks

---

