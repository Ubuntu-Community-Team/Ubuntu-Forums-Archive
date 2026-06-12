---
title: "Boot Loader Disappeared"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by hlgcis on 2006-03-02
Earlier this week I had successfully installed Ubuntu on my PowerMacG5 with yaboot as the boot loader to choose between Ubuntu and OSX. Now after a couple of reboots it yaboot has disappeared and it just boots straight to OSX without asking if I want Ubuntu. The partitions are still there but I don't know where the boot loader went.
Any ideas?

---

### Post by BoneKracker on 2006-03-02
I have no idea what caused it.  Perhaps you updated some OSX software that over-rode your yaboot/open-firmware configuration.  Here are a couple of things you might try:

1.  As root, from the console, run "ybin".  This will re-assert what's in the linux configuration files that pertain to yaboot and Open Firware.  Then reboot.

2.  If that doesn't work.  Try running "mkofboot".  This essentially formats the New World boot partition, preparing it for "ybin", and then runs "ybin".  As I'm sure you are aware, this is not the same as your Linux boot partition/directory.  If you really want to nuke it and start clean, you can use "mac-fdisk" to delete and re-create the partition, but I doubt that would solve anything that mkofboot won't.

3.  If that doesn't work, you might check the contents of your /etc/yaboot.conf file.  It should contain entries pointing to both MacOS X and your Linux kernel.  It should also have a line telling it to wait long enough for you to choose which one you want before it chooses the default.  You'll need to read the documentation if you haven't.

4.  There's also a third utility called "yabootconfig" that will give you a fresh default yaboot.conf file that you can edit.

5.  You can also boot into an Open Firmware prompt by holding down some key combination (ctrl+option/alt+o+f , I think).  From there, you can manually control the boot process (find OF documentation on the Web or Apple's site).

Post your result and what the actual solution was.

---

### Post by engla on 2006-03-02
Hold option when you start. You should be able to select your ubuntu partition and boot from that. 

When you're in ubuntu, run 'sudo ybin' to update the boot record. Or try the other things posted above.

---

### Post by Ptero-4 on 2006-03-02
There's a boot screen you can call pressing "option" right after you boot your Mac. It can boot Linux partitions too.

---

