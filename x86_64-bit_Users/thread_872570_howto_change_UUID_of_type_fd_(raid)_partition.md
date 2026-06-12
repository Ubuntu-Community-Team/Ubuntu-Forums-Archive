---
title: "howto change UUID of type fd (raid) partition?"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by Zelos1983 on 2008-07-28
Hi there,

I got Ubuntu 8.04 64Bit and I want to change the UUID of the RAID (type fd) partitions, how do I do that?
I found a method only for ext2/3, reiser and swap partitions, but not for raid partitions.

Would be nice if there is a generic way to change UUIDs ;-)

Thank you very much in advance,
David

---

### Post by shank15217 on 2008-07-28
Do you want to destroy the data or just change the uuid number? Considering the fact its a UUID what caused you to want to change it? Did you find a conflict?

---

### Post by shank15217 on 2008-07-28
[http://linux-raid.osdl.org/index.php/RAID_superblock_formats](http://linux-raid.osdl.org/index.php/RAID_superblock_formats)

The mdadm utility changes the uuid parameter of the raid superblock, you could probably modify the utility source code to set the uuid to a specific number. Have fun hacking :)

---

### Post by Zelos1983 on 2008-07-29
@shank
I do not want to destroy the data, I just want to change the UUID of the partitions containing the raid. The madm utility was successful in changing the UUID of the raid partition (/dev/md0), but right now I don't see how to change the UUID of the container?

The background is:
I have 2 computers running the same installation with heartbeat. One computer would replicate it's operating system and all data to the other one (exept for some config files, which exist on both machines but are linked differently). Therefore I initially cloned the system, and I got the RAID UUIDs right, but not the ones in the container (like that of /dev/sda1 e.g.), which causes Ubuntu to fail at boot time, jumping into busybox because it cannot assemble its array. I can then reassemble the array by hand in busybox easily by specifying the according devices and continue booting.
As Ubuntu relies heavily on UUIDs, I would like not to change everything back to devices by hand, because of the chance that this might get altered due to an upgrade process, instead, I plan to use same UUIDs on both machines.

Since one machine is already in production use and in a remote location, cloning the whole disc is not an option due to bandwidth limitations. I instead copied the content via rsync and build an array the same way.
Now everything works, except the boot mechanism of initrd.

---

