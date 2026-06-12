---
title: "New to AMD64 and unable to install anything!"
date: 2006-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Findeton on 2006-05-30
I've just bought a new motherboard and CPU because a high peak of tension end with the one I had. My machine is:
[LIST]
[*] CPU: AMD64 Sempron 3100+
[*] Motherboard: Asrock K8 Upgrade NF3 nforce3 250 single chip
[*] 768MB DDR Kingston
[*] Seagate 120Gb HD
[/LIST]

I'm unable to boot the kernel that comes with Ubuntu Dapper Drake RC 32 bits (it hangs up after showing 'loading the kernel'. For the official 5.10 version, I'm able to boot the kernel (:mrgreen: ) but, for both 64 and 32 bits, when it finnishes installing all the packages, the installation frozes showing the following error:

CPU 0: Machine Check Exception: 4 Bank 4: b200000000070f0f
TSC 3eb4f7a737
Kernel Panic - not syncing: Machine check
_

I've run memtest for a whole night without errors, and a tool from seagate without finding any error (just to make sure it's not because of the peak of tension). Googling this i've come to the conclusion that is a ubuntu -  amd64 problem. I've tried to boot the kernels with the 'nomce' and 'acpi=off' options but it doesn't solve the problem at all.

I've only been able to boot Ubuntu 5.10 Live (and without problems at all), in fact I'm writing to you from the live cd on this messy AMD64 machine.

Any help is welcome! Anyone having this kind of problems? Did anyone manage to

---

### Post by bruce89 on 2006-05-30
Yes, i'm using AMD64 Dapper.

---

### Post by Findeton on 2006-05-30
[QUOTE=bruce89]Yes, i'm using AMD64 Dapper.[/QUOTE]

So... did you have any problem? how did you manage to overcome it ? etc

---

### Post by kingcharles1666 on 2006-05-30
I think you are using 3 memory banks?
try with 2 banks, check the mobo manual to see if there are paired slots.

---

### Post by Findeton on 2006-05-30
No, I'm using 2 memory banks only (512+256). Btw now i've been able to boot the Dapper instalation with the 'ide=nodma' option, but it hangs up when installing the packages. Fortunately, it looks like it's just a problem of the cd or the CD drive. Now i'm burning again the CD...

---

### Post by Findeton on 2006-05-31
Good News! I finally was able to install Ubuntu Dapper Drake into my system, just needed to add the option 'ide=nodma' to the kernel. I know this can slow down my system a little bit, but unless you have other workaround...

**EDIT: ** Using hdparm, I confirm the damage to the speed of the system:

#hdparm -Tt /dev/hda
/dev/hda:
 Timing cached reads:   1380 MB in  2.00 seconds = 688.73 MB/sec
 Timing buffered disk reads:   16 MB in  3.28 seconds =   4.87 MB/sec

Using parsemce, I obtain some interesting info about the Kernel Panic.
[B]
Error:[/B]
CPU 0: Machine Check Exception: 4 Bank 4: b200000000070f0f
TSC 3eb4f7a737
Kernel Panic - not syncing: Machine check

**Parsemce info:**
./parsemce -e 4 -b 4 -s b200000000070f0f -a 3eb4f7a737
Status: (4) Machine Check in progress.
Restart IP invalid.
parsebank(4): b200000000070f0f @ 3eb4f7a737
        External tag parity error
        CPU state corrupt. Restart not possible
        Error enabled in control register
        Error not corrected.
        Bus and interconnect error
        Participation: Generic
        Timeout:
        Request: Generic error
        Transaction type : Invalid
        Memory/IO : Other

---

