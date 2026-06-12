---
title: "Need help installing DWL-G122  driver"
date: 2006-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by SpoonMan on 2006-04-19
Hi,

I have a stock 1st generation Mac Mini (1.25ghz G4, 256Mb RAM, 40Gb HDD) running OS X and Ubuntu 5.10, and I need to install my DWL-G122 USB Dongle.... It works OK in OS X, but Ubuntu doesn't seem to recognise it. I tried to install ndiswrapper (though I don't think it works on PowerPC systems) but I get an error saying ndiswrapper has no installation candidate ](*,) . I installed the open source driver too but that didn't help....

Can someone give me some pointers?? I'm very new to PowerPC Linux.. 

Thanks In Advance

Martin

---

### Post by SpoonMan on 2006-04-20
OK, I managed to get the open source drive compiled and installed ok. But when I try iwconfig I get :

```

lo        no wireless extensions.

eth0    no wireless extensions.

sit0      no wireless extensions.

```

Wifi-radar doesn't pick up anything. No lights display on the adapter. 

Where am I going wrong? If it doesn't start working soon I'm going to give up on Ubuntu, which sucks because it works flawlessly on my x86 PC....

Please Help!

:confused:

---

### Post by ssam on 2006-04-22
did you read [https://wiki.ubuntu.com/WifiDocs/Device/DWL-G122_%28Rev_B%29](https://wiki.ubuntu.com/WifiDocs/Device/DWL-G122_%28Rev_B%29)

it looks like it might take a bit of effort to make this work. you may have more luck in dapper than breezy.

ndiswrapper only works on x86.

maybe check [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) before buying your next wireless card.

---

