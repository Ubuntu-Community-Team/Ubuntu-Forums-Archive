---
title: "SunFire v40z kernel panic on startup"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by dhpeterson on 2005-10-27
Hi All,

I have installed the linux-image-2.6.12-9-amd64-k8-smp kernel on a new SunFire v40z. When I boot, on some occasions I am experiencing a kernel panic right after the grub bootloader selects the boot image and begins to boot it.

This is a semi-repeatable problem. Is it a known issue? (I didn't come across anything in my search for this). I would be happy to help with stack traces etc if someone can point the way.

Just a few things I should note regarding my setup:

* I installed using the breezy installer. The initial kernel, linux-image-amd64-generic, showed no problems.

* I have run memtest on the RAM to exclude faulty low-mem as the issue (the kernel uses an initramfs which gets unpacked into memory)

* My system is setup across three mdadm raid arrays (/dev/md0 as root, /dev/md1 as swap, and /dev/md2 as /var). All are RAID 1 in 2+1 (active/spare) configuration. They are 73GB SCSI 320 drives.

* I have inspected the initrd.img by gunzipping and using "cpio -t < image" to check that mptscsih, mptbase and sd_mod .ko modules are all preset. (Apparently they were missing from a previous initramfs release, see [1]).

* I have attempted to boot the kernel with acpi=off and nofb options, to no effect. I have seen the kernel panic under both of these circumstances.

The final point to note is that the panic is pretty much immediate after grub loads the kernel. I see "Loading ..." then followed by scolling page after page of errors, which normally stops after a few pages. I have not written down the messages but I can if this is needed. Is there a simple way to capture this kernel error data? (I have checked /var/log/messages but no messages at all are recorded for the panic boots).

Any help or pointers greatly appreciated.

Dave

[1] [http://ubuntuforums.org/archive/index.php/t-65495.html](http://ubuntuforums.org/archive/index.php/t-65495.html)

---

### Post by dhpeterson on 2005-11-23
Just a follow-up on this ... I ended up installing Debian Sarge AMD64 (which uses the 2.6.8 kernel), which boots without any problem.

I did some digging around the error messages that kept looping on the console screen when the panic was triggered (it was not always triggered, which to me suggests some kind of a race condition). The culprit looked like some problem within the binutils implementation, but I cannot be sure.

---

