---
title: "Changing partitioning scheme"
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by wantilles on 2006-07-19
I recently changed my partitioning scheme adding a "/boot" partition as it better fits my needs.

In every other Linux distribution I have tried so far (Gentoo, Debian) I know that only the 3 following steps are necessary to "inform" the system for the change:

1. Change menu.lst so that it points to the boot partition (previously it pointed to the "/" as there was no "/boot") and change the root partition in the "kernel" lines.

2. Re-install grub via its command-line interface in the "/boot" partition (previously it was in the "/") - I never put it in the MBR.

3. Add an entry to fstab for the newly added "/boot" partition (ext2) and change all the other entries for the same physical disk as they are different now.

By doing all the above, Ubuntu boots normally, however it never loads X or Gnome. Instead, it logs my regular user (that's expected -> I have set up auto-login) in a full-screen console.

Boot-up process stop-point -> "Checking all filesystems" step is never completed.

What else does it need altered to function correctly?

Version -> Ubuntu 6.06 amd64

---

