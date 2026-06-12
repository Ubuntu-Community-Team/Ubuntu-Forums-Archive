---
title: "boot log"
date: 2006-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by blew on 2006-11-19
Hi all.

I'm using Ubuntu 6.10 64 and I've just compiled the latest vanilla kernel. I did a lot of tweaking on configuration this time and successfully messed things up. :)

When I boot into the new kernel, I get a kernel panic. I'm trying to figure out what's exactly the problem, since I'm just getting the "Attempted to kill init!" message.

I'd like to be able to read the entire boot log, as I can't page up/down once the kernel panics. Is there a way to log the verbose boot output into a file? When I login to the working kernel there are no messages from the previous (failed) boot in the logs.

By the way, don't know if this can be the cause for the kernel panic, but I'm getting the following error just before it:
```

Begin: Running /scripts/init-bottom ...
mount: Mounting /dev on /root/dev failed: Invalid argument
Done.
run-init: nuking initramfs contents: Directory not empty
```

There are some warning/error messages before this one, but I can't read them as they scroll too fast - hence my need for a boot log.

Can anyone help? Thanks a lot!

---

