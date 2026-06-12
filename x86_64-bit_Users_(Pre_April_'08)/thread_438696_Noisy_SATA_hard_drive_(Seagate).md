---
title: "Noisy SATA hard drive (Seagate?)"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Baldwin on 2007-05-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109781](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109781) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just wondering if others out there are suffering from abnormally loud hard drives after upgrading from edgy to feisty. I know of one other user who has said it's happening to them too, we're both using Seagate drives on amd64s kernels.

If anyone else has this problem, please comment as such on my bug report so the developers will hopefully take note. If anyone's had the problem and fixed it, a quick explanation would be even better.

Thanks.


PS. I posted this in General Help about a week ago, but all has gone quiet in that thread with no real improvement to my situation, so I hope people don't mind me cross-posting here.
[http://ubuntuforums.org/showthread.php?t=432472](http://ubuntuforums.org/showthread.php?t=432472)

---

### Post by kuja on 2007-05-10
I've got three SATA seagate hard drives in right now, and they each sound like sweet blissful silence :) (granted, I'm running Debian Etch right now, but Feisty didn't give them any problems either).

Odd thing related to my drives is though, with Feisty's kernel(Yes, I installed it in Debian ... having some issues with 2.6.18 regarding one of my IDE drives), I get some really strange errors leading up to a kernel panic regarding SATA. I'm pretty sure they are dmcrypt related though, as I didn't have any problems with Feisty's kernel  when I wasn't using dmcrypt ... Oh well.

Oh, with regards to that bug report you linked to, my hardware is scarily similar to his.
I've got an nforce 4 MoBo (Asus A8N-SLI Premium), and though I'd have to look it up to be sure, I swear that hard drive is the exact same model number as one of mine.

---

### Post by jamescox84 on 2007-05-10
I have two seagate harddrives (sata) and I am currently using ubuntu 7.04 (amd64). I can here them when they are accessing data, but I don't think they got any louder with the upgrade from edgy, but then I never realy listend out for it.

What sort of bug could make harddrives loader? Now I am intrigued!

---

### Post by Baldwin on 2007-05-10
> **kuja said:**
> Oh, with regards to that bug report you linked to, my hardware is scarily similar to his.
I've got an nforce 4 MoBo (Asus A8N-SLI Premium), and though I'd have to look it up to be sure, I swear that hard drive is the exact same model number as one of mine.

That was my bug report :)

Now this really is strange if you're not getting the same problem.
Are you using the nvidia SATA controller or another one ?
(My mobo has 2, I'm not sure which I'm using, will have to check once I get home)

Any chance you could post your output from "hdparm -I" ?
("sudo hdparm -I /dev/sda", or something along those lines)

If there's anything set differently I might be able to change it on mine.

---

### Post by Baldwin on 2007-05-10
> **jamescox84 said:**
> I don't think they got any louder with the upgrade from edgy, but then I never realy listend out for it.
You'd notice. Its a completely different sound to the normal "hard drive access" sound, and much louder. Ever hear an old 286 hard drive ? It sounds worse.

> **jamescox84 said:**
> What sort of bug could make harddrives loader? Now I am intrigued!
I've no idea either :(
Only thing I can think of is that it's making the hard drive seek all over the place in rapid succession. But even that wouldn't explain the horrible noise.

---

### Post by kuja on 2007-05-10
Erm, yeah, I'm using the nforce 4 controller, not the SIS or VIA controller ... whichever it was.

Here's what my hdparm has to say:

> dustin@terra:~$ sudo hdparm -I /dev/sd?

/dev/sda:

ATA device, with non-removable media
        Model Number:       ST3250824AS
        Serial Number:      4ND1GKM6
        Firmware Revision:  3.AAD
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  488397168
        device size with M = 1024*1024:      238475 MBytes
        device size with M = 1000*1000:      250059 MBytes (250 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    Software settings preservation
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

/dev/sdb:

ATA device, with non-removable media
        Model Number:       ST3400633AS
        Serial Number:      3PM0DSE9
        Firmware Revision:  3.AAD
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  781422768
        device size with M = 1024*1024:      381554 MBytes
        device size with M = 1000*1000:      400088 MBytes (400 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    Software settings preservation
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

/dev/sdc:

ATA device, with non-removable media
        Model Number:       ST3250823AS
        Serial Number:      5ND0FJPZ
        Firmware Revision:  3.03
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  488397168
        device size with M = 1024*1024:      238475 MBytes
        device size with M = 1000*1000:      250059 MBytes (250 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    Software settings preservation
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct
dustin@terra:~$                            

---

### Post by Baldwin on 2007-05-13
Thanks, looks pretty much the same as mine except you've got SMART on and I don't.
(And I can't figure out how to turn it on, smartctl won't do it)

Guess I'm not using ubuntu until at least the next kernel version comes out (which I hope will fix it...)

---

### Post by kuja on 2007-05-13
erm, about smart, I think I had to turn it on in BIOS.

---

### Post by JustGuest on 2007-05-19
Hi Baldwin. Well let say first that i'm not an Linux/Ubuntu user. I just needed to post, because i got similar "problem" with my new Seagate SATA drive. It got much louder acces sound, than my other SATA and ATA drive (also Seagate drives). It's as silent than my other drives, when it's idle. SMART info says that drive is OK and i even ran Seatool for Dos (short test) and it PASSED. So i think that drive should be ok..

That drive is ST3250624AS. (250Gb).

---

### Post by zmigliozzi on 2007-05-20
I've never really heard my hard drives before. I've always ran WD hard drives.

---

### Post by ian dobson on 2007-05-20
Hi,

Could this be related to the AAM MODE (Peformance/Silent)?

I know on a windows box then I set my seagate to performance it sounds like a washing full of bolts and in quiet I don't really hear it.

Regards
Ian Dobson

---

### Post by Sockerdrickan on 2007-05-20
My Seagate 7200rpm is not very noisy

---

