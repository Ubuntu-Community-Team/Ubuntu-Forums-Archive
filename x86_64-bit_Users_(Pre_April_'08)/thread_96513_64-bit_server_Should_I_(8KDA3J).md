---
title: "64-bit server? Should I? (8KDA3J)"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by zilla1126 on 2005-11-29
I'm a little new to Ubuntu (long time Mandr* user), so forgive me if this is a simple question...

Basically I am looking to put in a new server for my home that will replace two seperate Mandr* servers. This new server will basically be used for postfix, samba, squirrelmail, clamav, amavisd-new, imap, pop3, etc...

What I am thinking about using is a Epox 8kda3j (rev 1.x) motherboard with a Athlon 64 3400 (not dual-core).
[http://www.epox.com.tw/eng/products_content.php?ps=223](http://www.epox.com.tw/eng/products_content.php?ps=223)

My questions are:

1. Should I use the 64 bit version of Ubuntu?

2. Can I expect problems in the future because I am using a 64 bit OS (not including proprietary binary support)

3. Will my onboard GigE (VITESSE VSC8201RX)be *completely* supported by the default install?

My interest in using this motherboard (which will be complete overkill processor-wise) is that I want to utilize the onboard GigE for my fileserver so as to have the fastest GigE connection possible (this is the chipset where the GigE is directly plugged into the chipset).

I have a old 64 bit PCI GigE card in a Dual PIII file server that I think was not really giving the throughput one would suppose it would.

Anyway, I figured I would ask the experts here - Thanks for your time and expertise.

---

### Post by FluffyElmo on 2005-12-01
For what it's worth, I don't think you'll have any problems running a 64bit server. All the apps I know of with issues are desktop centric. I run a 64bit server (basically just Apache/J2EE and Samba) and performance has been great. No compatability issues to report yet.

I also have an onboard GigE card which worked right out of the box, but it's a Marvell chipset so your mileage may vary. Wouldn't take all that long to install and try it out though:)

---

