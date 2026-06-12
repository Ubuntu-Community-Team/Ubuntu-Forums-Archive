---
title: "HP dx5150 install of Breezy AMD64 broken"
date: 2006-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frank-Hamersley on 2006-05-25
G'day all,

I am building Breezy on a new HP dx5150 with a pair of 300G Barracudas in a RAID-1 config, standard vid, 1G RAM and the factory 16xDVD+R/+RW.

I have noticed however that the CD-ROM driver appears to be a bit flaky?!?

On my first attempt the install choked part way through installing the base packages and baulked at creating the standard user profiles.

On the second attempt it got further but again stalled when copying on the packages.  It aborted the install but has left enough on the drives to boot a shell (no X) and I now am trying to repair/upgrade/install the missing packages rather than starting again.

I used "linux noapic nolapic" as a boot string because there seemed to be interrupt problems otherwise.

Right now I am stuck on libxslt1.1 (a rather heavily used dependency it seems).  It appears /var/cache/apt/archives/libxslt1.1_1.1.15-0ubuntu1_amd64.deb got damaged because dpkg_deb script was whinging about a broken pipe when unpacking it.

Can anyone confirm the CD driver is problematic or suggest a better set of boot strings to avoid the generic support?  Otherwise I will continue trying to repair the broken stuff - which whilst I can prolly do it given enough time is my least prefered option.

Cheers, Frank.

---

