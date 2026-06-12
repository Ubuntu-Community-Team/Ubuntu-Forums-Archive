---
title: "upgrade from 32bit to 64bit with 9.10??"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by jlh68 on 2009-10-29
I have my destop partitioned so that it has a separate Home partition (ext3 file system).  I also have about 180-GB of *unpartitioned* Hard Drive space.  I would like to install 9.10 in 64 bit and get the ext4 file system and GRUB2.  I don't care to retain 9.04 in 32 bit, ext3 file system.

What is the best approach to make this upgrade? I want to retain my Home partition (either in ext3 or ext4)  which ever will work with the new system in 64 bit and ext4 file system. 

Any suggestions:

---

### Post by philinux on 2009-10-29
Backup Backup Backup.

During the install choose manual partition. Just dont format your home partition and dont change it to ext4 as it will screw it up leave it ext3.

Unless you choose to reinstall the lot and then put your data back.

If you are unsure then on the live cd choose "try ubuntu". That way if you get stuck you can use Firefox to access these forums during the install to ask questions. Make sure you have an internet connection that works too during install.

---

### Post by jlh68 on 2009-10-29
**philinux** On your Backup comment, are you saying I should back up on media other than the hard drive, correct?  Also what size should my root partition be? It is about 9GB now and I am using about 7.5GB with the current install.

---

