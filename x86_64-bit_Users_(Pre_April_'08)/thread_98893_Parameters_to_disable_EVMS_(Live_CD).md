---
title: "Parameters to disable EVMS? (Live CD)"
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by f1d094 on 2005-12-04
Two separate questions actually:

1) What flag can I pass the boot loader on the live CD so it will skip EVMS?

2) Does EVMS store any boot sector data? Anything that would be residual after the partition is re-purposed as a RAID segement?

I am in the process of rescuing my system after a multi drive failure in Raid5. I have finally reconstructed nearly all of the data, and am ready to reconstitute the raid...but the Live CD now seg-faults as soon as it attempts to load EVMS.

I was not using EVMS prior to the crash...so I do not understand what in the multiverse its trying to do.

If I remove either of the first two drives (both healthy, clean and sync'd), or change the drive order, the system boots/runs just fine.

The problem is, I need these drives EXACTLY where they are in order for the Raid to assemble.

Its a weird one. Anyone have any clever ideas? :???: 

Thanks!

---

