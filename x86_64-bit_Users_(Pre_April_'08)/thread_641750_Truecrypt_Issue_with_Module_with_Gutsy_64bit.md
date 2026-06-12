---
title: "Truecrypt Issue with Module with Gutsy 64bit?"
date: 2007-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by trmentry on 2007-12-15
I'm getting the following after installing the truecrypt deb package on Gutsy 64bit.

```

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.22.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module

```


```

root@hoth:~# modinfo /usr/share/truecrypt/kernel/truecrypt-2.6.22.ko
filename:       /usr/share/truecrypt/kernel/truecrypt-2.6.22.ko
license:        GPL and additional rights
description:    device-mapper target for encryption and decryption of TrueCrypt volumes
author:         TrueCrypt Foundation
srcversion:     37BE0E2FDE167BC5F918687
depends:        dm-mod
vermagic:       2.6.22-14-generic SMP mod_unload
parm:           trace:Trace level (int)
root@hoth:~#
root@hoth:~# uname -a
Linux hoth 2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x86_64 GNU/Linux
root@hoth:~#

```

I'm guessing there is an issue with the 'vermagic' and what my system is reporting.

Is this a case of having to compile from hand?

---

### Post by trmentry on 2007-12-15
Ok.. installed the deb on my 64bit workstation that is just the desktop version of Gutsy and works fine.

The only I noticed is that I can't mount a TC volume if its on an NFS mount.  I have to copy it to the local machine.   PITA.

---

### Post by trmentry on 2007-12-15
Ok... compiled Truecrypt on my server.  All working now.

```

filename:       truecrypt-2.6.22.ko
license:        GPL and additional rights
description:    device-mapper target for encryption and decryption of TrueCrypt volumes
author:         TrueCrypt Foundation
srcversion:     37BE0E2FDE167BC5F918687
depends:        dm-mod
vermagic:       2.6.22-14-server SMP mod_unload
parm:           trace:Trace level (int)

```


I just downloaded the linux kernel source.  And did the following as root.  (or sudo)

uname -r

apt-get install linux-source-2.6.22  (make sure this matches what you have in uname -r)

apt-get install build-essential

tar jvxf truecrypt-4.3a-source-code.tar.gz

cd truecrypt-4.3a-source-code

cd Linux

./build.sh

./install.sh

---

### Post by skralljt on 2008-01-21
quote

I just downloaded the linux kernel source. And did the following as root. (or sudo)

uname -r

apt-get install linux-source-2.6.22 (make sure this matches what you have in uname -r)

apt-get install build-essential

tar jvxf truecrypt-4.3a-source-code.tar.gz

cd truecrypt-4.3a-source-code

cd Linux

./build.sh

./install.sh
/quote


I did this very thing but am still getting the unknown symbol in the kernel module issue...

---

