---
title: "nvidia drivers cuase trouble to atheros wireless card"
date: 2008-08-07
forum: x86 64-bit Users
---

### Post by yogi4yu on 2008-08-07
Hi all,
        This is what i have


Problem : 
               The wireless net goes down after some random  time ( this time goes generally  decreasing every time ) . Everything is ok after reboot/shutdown. Nothing else works.


Configuration :
        Motherboard     : ASSUS A8V-VM SE
        Processor       : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
        RAM             : 2 GB
        cpu MHz	        : 1997.649
        cache size	: 512 KB
        graphics card   : nVidia Corporation G70[GeForce 7600 GS] 
        wireless card   : Atheros  AR5212/AR5213 Multiprotocol MAC/baseband processor 


Solution :
            uninstall nvidia ( EnvyNG ) drivers , and things start working.

Things tried before : 
            Upgraded kubuntu to hardy, manual madwifi driver complilation, ndiswrapper + INF drivers, rmmod+ modprobe , /etc/init.d/networking restart, shutting down PC for 2-3 days, resetting cmos by jumper setting etc etc.( tried every solution  seen in google search ) 
            2 times fresh install on another partition form hardy dvd + all above things. ( in fresh install wifi card driver works out of the box, but same problem is there when nvidia drivers are installed ).

Problem is that i have to choose either one of them. Is there any solution by which i can have both nvidia and atheros drivers together without any issues?

---

