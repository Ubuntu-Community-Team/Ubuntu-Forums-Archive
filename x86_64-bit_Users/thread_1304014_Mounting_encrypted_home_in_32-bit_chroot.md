---
title: "Mounting encrypted home in 32-bit chroot"
date: 2009-10-28
forum: x86 64-bit Users
---

### Post by Tarao on 2009-10-28
I have a 64-bit Jaunty desktop, and inside it a 32-bit chroot (also Jaunty) for some 32-bit applications. The problem is that during installation of the 64-bit host, I chose to encrypt /home. Now, when I dchroot into the 32-bit chroot I don't see the content of my home directory, just this:

lrwxrwxrwx 1 root root 56 Oct  9 16:36 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 root root 52 Oct  9 16:36 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

Installing ecryptfs-utils in the 32-bit chroot does not help either, or at least I don't know how to use it

How could I access my encrypted home folder from the chroot?

Any help would be greatly appreciated!

---

