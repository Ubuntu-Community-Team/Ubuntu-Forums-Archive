---
title: "UPS support"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by hvacr on 2008-04-26
I have tried to get apcupsd to work on both gutsy and heron, with no luck. I see in the power management section of heron, that I only have a tab for on A/C power. When I ran gutsy I also had a battery tab. I am running a desk top system with a ups. 

Why is there no built in support for ups units, I get a lot of power failures here.

I really need to have a system that supports a ups.

Never mind, looks like I will be going back to gutsy, heron is not ready yet. My system has black screened 5 times since I installed heron 2 hours ago, sheeesh.

---

### Post by milosz.galazka on 2008-04-27
Hello,

I use Hardy, I just connected APC Smart-UPS 420 to serial port, installed apcupsd and got (*apctest*):

```
Simulating UPSlinkCheck ...
Wrote: Y Got: SM
Attempting to use smart_poll() ...
Sent: Y Got: SM  Good -- smart_poll() works!.

Going to ask for valid commands...
Protocol version is: 3
Alert characters are: !$%+?=#|
Command characters are: ^A^N^Z')+-89@ABDEFGKLMNOPQRSUVWXYZabcdefgjklmnopqrsuxyz~^M

Now running through apcupsd get_UPS capabilities().
NA  indicates that the feature is Not Available

UPS Status: 08
Line quality: FF
Reason for last transfer to batteries: R
Self-Test Status: NO
Line Voltage: 221.7
Line Voltage Max: 221.7
Line Voltage Min: 221.7
Output Voltage: 221.7
Batt level percent: 100.0
Batt voltage: 13.77
UPS Load: 062.4
Line freq: 49.75
Runtime left: 0013
UPS Internal temp: NA
Dip switch settings: NA
Register 1: 00
Register 2: 00
Register 3: 00
Sensitivity: H
Wakeup delay: 000
Sleep delay: 020
Low transfer voltage: 208
High transfer voltage: 253
Batt charge for return: 00
Alarm status: 0
Low battery shutdown level: 02
UPS Name: UPS_IDEN
UPS Self test interval: 336
UPS manufacture date: 05/22/02
UPS serial number: QS0221240847
Date battery replaced: 05/22/02
Output voltage when on batteries: 230
Nominal battery voltage: 012
Percent humidity: NA
Ambient temperature: NA
Firmware revision: 21.6.I
Number of external batteries installed: NA
Number of bad batteries installed: NA
UPS model as defined by UPS: DWI
UPS EPROM capabilities string: uD43127130133136uA43108110112114uI43253257261265lD43106103100097lA43092090088086lI43208204200196e44200155090oD13115oA13100oI13230s441HMLLq44202050710p443020180300600k4410TLNr443000060180300E443336168ON OFF
The EPROM string is 205 characters long!
Hours since last self test: 010.7
```

So it seems that it is working for me. Add some more informations so maybe someone could help you :)

---

