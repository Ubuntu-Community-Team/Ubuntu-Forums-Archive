---
title: "Incomprehensible Machine Check Exception"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tarkus on 2006-04-15
In the last few days, my machine has gone quite unstable.  Used to get along just fine, but now I'm having all sorts of issues.

It started off with messages like this:
> [   85.202757] hdb: CHECK for good STATUS

[   85.448231] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }

[   85.546244] ide: failed opcode was: 0xe3

[   85.596830] hdb: drive not ready for command

[   85.661999] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }

[   85.760735] ide: failed opcode was: 0xea

[   85.811744] hdb: drive not ready for command

[   85.907057] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }

[   86.006800] ide: failed opcode was: unknown

[   86.062905] hdb: drive not ready for command

[   86.220629] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00

[   86.295303] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40

[   86.471974] hda: CHECK for good STATUS

on both hda and hdb

A few times I've had a SOFT LOCKUP message appear on my terminal, but it does seem to recover from that.  Unfortunatly I don't have the backtrace from that, but if it happens again I'll post it here.

Then, I eventually tossed a MCE:
> HARDWARE ERROR
CPU 0: Machine Check Exception:                4 Bank 4: b200000000070f0f
TSC 232c6110788
This is not a software problem!

It's semi-repeatable: it happens every once in a while, but I don't have a way to cause it to happen.  I decoded the MCE to this:
> Status: (4) Machine Check in progress.
Restart IP invalid.
parsebank(4): b200000000070f0f @ 232c6110788
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

Unfortunately, a Generic error in bank 4 doesn't help me much.  Any ideas as to what's going on?  Dead hard drive?  Hard drive controller?  CPU or RAM?  Something's gone wrong...


Thanks for any pointers!
Steven

---

### Post by John.Michael.Kane on 2006-04-15
This is a shot in the dark. but do these errors happen on a clean install. reading those msg would lead one to think your having a hardware problem, however it could just be the os needing a clean install. ie maybe theres a croupt file of some sort. I would be hard pressed to think you mem and cpu is toast however i could be worng. it just looks like the OS is the issue. if you can try reinstalling the os, and just the needed items drivers internet ect nothing special. run it for a few day like that, and see if the errors happen. this will help weed out the os as the issue.

---

### Post by tarkus on 2006-04-15
Would a clean kernel/modules build be enough?  Nothing else should be able to cause ATA failures, MCEs, and soft lockups, right?  Doing a clean install would be a pain, I've got stuff spread over seven hard drives with multiple RAID arrays set up...

I'll try it with a new kernel and maybe run memtest for good measure.  If you think reinstalling the _entire_ system is necessary, I might run a livecd or something instead...  does that work?

---

