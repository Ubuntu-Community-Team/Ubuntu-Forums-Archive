---
title: "Can't boot openSUSE TW 32 bit"
date: 2024-05-22
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-05-22
Probably caused by

```
zypper dup

```

```
dracut-initqueue: Warning not all disks have been found
You may want to regenerate initramfs

```

I've booted latest TW iso, selected *Rescue system* menu command, chrooted using recommended script/application (?)


I've run ```
zypper dup

```

and

```

dracut -v
dracut[F] Cannot find module directory /lib/modules/6.8.9-1-default
dracut[F] and --no-kernel was not specified

```


```
# ls /lib/modules
#

```

TW has disappeared from TW grub


Any idea please ?

---

### Post by Xian on 2024-05-22
This happened to me recently.
To fix I believe I did a chroot then issued command:

dracut --regenerate-all --force

---

### Post by maketopsite on 2024-05-24
> **Xian said:**
> This happened to me recently.
To fix I believe I did a chroot then issued command:

dracut --regenerate-all --force

I'm sorry it does not work:
```
dracut -v
dracut[F] Cannot find module directory /lib/modules/6.8.9-1-default
dracut[F] and --no-kernel was not specified
```

---

