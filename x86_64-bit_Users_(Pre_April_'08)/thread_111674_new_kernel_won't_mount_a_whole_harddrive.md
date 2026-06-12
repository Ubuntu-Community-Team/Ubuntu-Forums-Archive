---
title: "new kernel won't mount a whole harddrive"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by grajea01 on 2006-01-02
Hello,

I'm trying to compile my own kernel instead of using the distro-provided one. This is not the first time I install my own kernel, but since I switched to Ubuntu I haven't done so in a long time.

The main reasons I want to install my own kernel are that I wan't to rev kernels as fast as I want, not to wait for a distro-provided one, and second I want to get rid of initrd.

My linux system is installed on /dev/hdb. With my own 2.6.14.5 kernel somehow it won't mount _any_ partitions coming from /dev/hda (I have Solaris-X86 and WinXP installed on it; I need my vfat partitions).

There's no big difference between my configs of 2.6.12-10 and 2.6.14.5, besides removing a lot of modules and getting rid of initrd. I can't see why it won't mount /dev/hda* . I provided my configs in attachments.

If I try to manually mount the filesystems (mount -t vfat /dev/hda5 /mnt/temp-part), I get a "device already mounted or busy" message.

Before you ask about the vfat module, some fat32 partitions are present on /dev/hdb and mount just fine. 

The hard drive (/dev/hda) is known by the system: fdisk /dev/hda shows the the drive and its partitions.

So here it is, I can't see what I am missing. I tried using 2.6.12-10's config file in my /usr/src/linux-2.6.14.5 source tree, make menuconfig, exit & save, and make menuconfig again (so that 2.6.14.5 would use 2.6.12-10's config as a base config to be modified as it suits me), no go...

I'm stuck here, any help is appreciated :)


-- Jeff

---

### Post by niallb on 2006-01-20
I'm having the same problem, but in reverse. System on hda, can't mount hdb.
I only found your post now after realising all the partitions
I was having difficulty with were on hdb.
Have you made any progress?

I originally thought the problem was with ext3 as my only 
ext3 filesystems were all on hdb. I even removed the journals and reverted them to ext2 thinking that was bound to fix it.

I also failed to resolve the problem by disabling selinux.

The problem still exists with 2.6.15 in my builds at least.,
with both vanilla source and patched for mISDN.

My latest .config is below.

If I find anything I'll post here.

NiallB

---

### Post by morphodone on 2006-01-20
[QUOTE=grajea01] I get a "device already mounted or busy" message.[/QUOTE]

Have you checked to see if the partition is indeed mounted?

type "mount" into a console and look at the output...
if hda is there, then it is already mounted

---

### Post by niallb on 2006-02-15
Got it sorted!

The evms "Enterprise Volume Management System"
was installed and grabbed all the unmounted partitions
at boot making them unavailable to the kernel.

The root partition and the drive it was on had already been claimed by the kernel driver, so I could see those fine.
I disabled the evms service and the second drive came back online with my own kernel.

Hope it works for you too.
NiallB

---

