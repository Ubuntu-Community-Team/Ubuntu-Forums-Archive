---
title: "[SOLVED] Install Hardy on Sun x4500 (Thumper)"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by n6mod on 2008-12-01
Has anyone installed Hardy on a Thumper? Both GRUB and LILO installs fail, and I can't figure out what's making them unhappy.

I'm installing on /dev/sdy, which is what they suggest for SLES or RHEL, but the installation assistant won't run with anything other than their approved distros (Windows, Solaris, RHEL, SLES), and I can't find notes from anyone trying this.

Any suggestions would be appreciated... please save me from SuSE. :)

---

### Post by n6mod on 2008-12-11
Answering my own post:

When the grub installation fails drop to a shell.

Edit device.map to point (hd0) at /dev/sdy and (hd1) at /dev/sdac. These are the only two drives visible at boot time.

The grub installation will have failed badly enough that it didn't copy the stage* files, but you'll find them in /usr/lib/grub/[arch]. Copy the files you need (or all of them, that's what I did) over to /boot/grub

Now run grub and set things up as normal. In my case that was:

device (hd0) /dev/sdy
root (hd0,0)
setup (hd0)

I re-ran update-grub just in case.

Hope this helps the next person to try this. It's a *screamer* of a machine.

---

