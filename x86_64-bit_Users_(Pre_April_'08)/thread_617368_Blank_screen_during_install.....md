---
title: "Blank screen during install...."
date: 2007-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Heather06 on 2007-11-19
Hi fellas...

I'm installing a 64-bit 6.06 server on a Xeon server. After entering English keyboard and English region the scrren goes blank. Tried it twice and got the same so at least its consistent?!?

Help!

---

### Post by John.Michael.Kane on 2007-11-19
> **Heather06 said:**
> Hi fellas...

I'm installing a 64-bit 6.06 server on a Xeon server. After entering English keyboard and English region the scrren goes blank. Tried it twice and got the same so at least its consistent?!?

Help!
First it would help if you listed your complete system spec's.

Second you can try the commands below.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

To pass all the commands in one go. At the boot/install prompt (make sure to hit F6 first),and add the command below to the boot parameter.
```
nosplash noapic nolapic pci=irqroute irqpoll framebuffer=false pci=acpi acpi=off pci=noacpi
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.


Hope this helps.

---

### Post by Heather06 on 2007-11-19
Well. I went back to the server and the next screen finally appeared. I guess it jsut needed more time?

I got as far as the network setup and it appears that it cannot detect the NICs. I'm going to try 7.10 to see if it does a better job as I imaging 6.06 is pretty dated as far as driver support is concerned, no?

At any rate I will keep the advise you sent. I appreciate it!

Ht

---

