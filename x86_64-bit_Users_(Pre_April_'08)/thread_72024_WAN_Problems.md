---
title: "WAN Problems"
date: 2005-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by pan9397 on 2005-10-05
I'm new to Ubuntu and I am trying to install my wireless card.

I'm using Ubuntu the 64 bit edition, and perform the following.

ndiswrapper -i netbc564.inf
    Installing netbc564
    Forcing parameter IBSSGMode|0 to IBSSGMode|2
    Forcing parameter IBSSGMode|0 to IBSSGMode|2
    Forcing parameter IBSSGMode|0 to IBSSGMode|2
    Forcing parameter IBSSGMode|0 to IBSSGMode|2
    Forcing parameter IBSSGMode|0 to IBSSGMode|2
    Forcing parameter IBSSGMode|0 to IBSSGMode|2
    Forcing parameter IBSSGMode|0 to IBSSGMode|2

ndiswrapper -m

modprobe ndiswrapper

    FATAL: Error inserting ndiswrapper         (/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko):     Unknown symbol in module, or unknown parameter (see dmesg)

Does anyone know what i'm doing wrong, and/or how I can fix it.  I don't believe it is anything serious just something that i'm missing.

Thanks a lot,
Paul Nicolucci

---

