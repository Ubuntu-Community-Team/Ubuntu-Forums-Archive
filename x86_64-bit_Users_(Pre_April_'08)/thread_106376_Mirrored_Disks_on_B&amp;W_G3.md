---
title: "Mirrored Disks on B&amp;W G3"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by m1nkman on 2005-12-20
I've got a B&W G3 with two 250gb IDE drives. I wanted to run it as a server, mirroring the drives. I can install 5.10 without a problem using just one disk. The question is how to set it up so the drives are mirrored. The hurdle I can't seem to get past mac-fdisk and how to partition it. Is what I want possible?

On x86 machine, I'd create matching /boot partitions and set them up with md as a raid1 set(/dev/md0). Then I use the rest of the disks to create matching partitions and set them up as a raid1 set(/dev/md1). md1 would then be a physical volume for lvm. From there it's just logical volumes. I'm shooting for something similar on the B&W.

Also, there will be no OSX on this box.

TIA,
Ken

---

