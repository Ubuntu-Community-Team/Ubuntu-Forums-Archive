---
title: "Install from Boot CD locks up before install begins"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by victayback on 2005-11-22
This is my first PPC Linux install (and first Ubuntu forum post).  Here is what I am trying to do:

Install Ubuntu 5.10 from the Boot CD on an Aluminum Powerbook G4 (purchased May 2005, if it matters)

I partitioned with the Disk Utility from Mac OSX (Tiger) CD.
    First partition (60gb) is OSX Journaled, but not case-sensitive.
    Second (15gb) was designated as "Empty Space" or something like that (the Disk Utility option that does nothing to it)
Then I installed OS X Tiger on the OSX partition.

When I boot from the Ubuntu CD, I press ENTER at the opening screen, and:
1. it loads kernel and ramdisk
2. goes to white screen with black text for a brief moment
3. switches back to a black screen and locks up with screen that shows this:
----------------------------------------
Welcome......kernel 2.6.12-9-powerpc
linked at....
tracing buffer...
klimit...
MSR...
HID0...

pmac_init(): exit
id mac(): done
MMU: enter
MMU: hwinit
hash: enter
hash: find piece
hash: patch
hash: done
MMU: map in
MMU: set io
MMU: exit
----------------------------------------
and then it freezes every time.

IMPORTANT NOTES:
This exact same thing happens with the Ubuntu LiveCD, the Gentoo Install CD, and the Debian Netboot CD, all of which use YABOOT.
Also, the Ubuntu LiveCD booted and ran perfectly in the iMac G3 (Panther) and iMac G4 (Tiger) I tried it in.

I also tried putting the empty space partition at the beginning, and tried doing the Ubuntu install before the Tiger install.

My conclusion:
It sounds like YaBoot doesn't like my hardware.  But I'm hardly an expert.

Of course, I appreciate all comments that enlighten me or (what I really want) get my PB to be a dual-boot system.

fyi, I've never used manual disk partitioning before, so if that's part of the solution, a quick reference as to where I could find some good new user info on that would be a plus.

Thanks.

---

