---
title: "HD issues..."
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdownie on 2006-01-02
I have a new AMD64 system with two SATA disk drives. I installed 64-bit ubuntu to one drive (partitioned as ex3 and swap) and I have the other drive formatted as xfs. I'm trying to use this second drive as storage for rather large media files.

My problem has to do with access permissions on the second (xfs) drive. First of all, I can't access it at all on boot up. However, I have been able to access it by going into the Disks Manager, giving it an access path from my home directory, and enabling access. The problem with this method is that it gives folder ownership to the root and prevents my user account from writing to it.

How can I configure the system to use this HD like a normal read/write drive?


Thanks,
Chris

---

### Post by dna on 2006-01-02
Wow, didn't even know there was a disk manager.
Try this:

sudo mount -t xfs /dev/sda? /mnt
<replace ? with drive #>
sudo chmod 777 /mnt

Also look in your /etc/fstab to see if it's there, you might just need to change it so it automounts.

man fstab

---

### Post by FluffyElmo on 2006-01-02
EDIT: Sorry, didn't notice that the chmod line was also in the post above. Ignore.

You can change the permissions on the drive using *chmod* and the recusive flag (-R). ***sudo chmod -R 777 /path/to/mountpoint*** should give full access to the entire drive for all users.

---

