---
title: "Slow typing in LTSP client - bad responsiveness"
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by nagylzs on 2009-02-11
Server hardware: Intel i7, 8GB DDR3 ram, three gigabit cards
Server OS: Unbuntu 8.1 desktop, 64 bit

There are two subnets with LTSP clients. Both of them have 6 diskless clients (12 clients total).

Diskless hardware: Intel P3 733 MHz (and some 1GHz), 128MB memory, Intel video card
Diskless OS: 32 bit Ubuntu 8.1, booted with LTSP (TFTP,DHCP, squashfs etc.)

X environment: the default Gnome installation

My problem: everything is fast, we can even play videos on the diskless clients. However, when we open an editor and start typing characters, they appear WAY SLOW. Some typed characters are missing like if they where not pressed at all.

Another problem: <select> type inputs work VERY SLOW in firefox. It takes 2 seconds to drop down the list, even if it contains two items.

The above problem comes out when only one diskless client is powered on!

We measured network speed with system monitor - it is NOT the problem because network speed was under 2 MB/sec (16 megabit) total while testing with a text editor. Also I think we can say that the processor power of the diskless clients is more than enough to decode X over ssh. (I also tried to start a Core2Duo diskless client with gigabit card and 2GB RAM. It also had the same problem!)

Before this server, we had a FreeBSD 7.1 terminal server, using the same diskless clients and the same network. It was working fine with the same clients (regarding application responsiveness). We wanted to replace that server because it hadn't got enough processing power and RAM for 12 clients. However, right now I can say that the old server was much better.

What can I do? Please help me! I have paid a fortune to buy this server, and now we can hardly use it.

---

### Post by nagylzs on 2009-02-11
I just found this:

[https://bugzilla.mozilla.org/show_bug.cgi?id=475713](https://bugzilla.mozilla.org/show_bug.cgi?id=475713)

They say it is NOT a firefox bug. Should I try compile firefox from sources? Will it help? Can I just download a tarball and configure, make , install ?

---

