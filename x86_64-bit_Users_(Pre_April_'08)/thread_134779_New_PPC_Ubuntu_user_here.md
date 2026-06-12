---
title: "New PPC Ubuntu user here"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by jdcope on 2006-02-22
Hi all, I have a 400mhz Powerbook "Firewire". I bought it second hand for $180. It has 320mb ram, dvd, and an Airport card. Well, had an Airport card. I took it out because it isnt supported. 

Is there a good 3rd-party pc-card wireless adapter that is supported by Linux for this platform? Or am I stuck tethered to my router? I havent had a chance to search the forums yet...

Thanks for the great site!
Jon

---

### Post by DrFunkenstein on 2006-02-22
[QUOTE=jdcope]Hi all, I have a 400mhz Powerbook "Firewire". I bought it second hand for $180. It has 320mb ram, dvd, and an Airport card. Well, had an Airport card. I took it out because it isnt supported. 

Is there a good 3rd-party pc-card wireless adapter that is supported by Linux for this platform? Or am I stuck tethered to my router? I havent had a chance to search the forums yet...

Thanks for the great site!
Jon[/QUOTE]
Hm, your airport card is supported, as far as I know.
The ones that made problems were the airport extreme cards, but even this is getting better now.

---

### Post by jdp on 2006-02-22
Ubuntu found and works with the AP card in my iBook just fine.  Original non-Extreme AP works very well in Ubuntu.

---

### Post by jdcope on 2006-02-22
Hmm, when I first installed I had the Airport card in there and I couldnt get it to see my router. Maybe I will put it back in and see if I can get it to work.

Thanks
Jon

---

### Post by jdcope on 2006-02-22
On another note, what are my options for Wireless "G"?
Can I use any PC-card type adapter?

Jon

---

### Post by ssam on 2006-02-23
you airport card should work fine. are you still having problems configuring it? are you using WEP or WPA?

airport extreme card should work in dapper.

if you want to buy a pcmcia 802.11 g card there is quite a bit of choice, but be carefull because sometimes manufactures change the chipsets without changing the model number. have a look at [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28PCMCIA%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28PCMCIA%29)

update:
beware of any card that need ndiswrapper to work. ndiswrapper lets you use windows drivers, but only works on x86.

---

