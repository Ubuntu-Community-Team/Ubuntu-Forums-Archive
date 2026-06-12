---
title: "G3 B&amp;W Error"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ilo on 2006-02-14
Hello everybody,
I'm new to Ubuntu and I was trying to install it on my old G3 B&W.
I searched and found a lot of threads on the subject but none helped me.
My problem is as follow:

1) I checked the CD is just fine [checked the MD5 and it works on other macs]
2) Insert the CD boot up [holding "c"]
and then I get this message:


[SIZE="1"][FONT="Courier New"]/pci@80000000/pci-bridge@d/mac-io@5/ata-3@20000/disk@0:2,yaboot.conf: Unable or corrupt filesystem
Can't open config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:[/FONT][/SIZE]

now I'm stuck!

Hope somebody can help me.

Cheers

PS. I get the same error trying to install Yellowdog

---

### Post by ottojschlosser on 2006-02-15
[QUOTE=ilo]Hello everybody,
I'm new to Ubuntu and I was trying to install it on my old G3 B&W.
I searched and found a lot of threads on the subject but none helped me.
My problem is as follow:

[SIZE="1"][FONT="Courier New"]/pci@80000000/pci-bridge@d/mac-io@5/ata-3@20000/disk@0:2,yaboot.conf: Unable or corrupt filesystem
Can't open config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:[/FONT][/SIZE][/QUOTE]

Hi. I'm posting this from a B & W running Breezy Badger. I had a similar problem with various distros (Fedora, YDL). What I did was change my hard disk setup - the B & W uses an early version of New World firmware and is very picky about its boot config. Try swapping drives if you're using more than one, or going to one drive. (Make sure drives are set for cable select.) Hope this helps - ojs

---

