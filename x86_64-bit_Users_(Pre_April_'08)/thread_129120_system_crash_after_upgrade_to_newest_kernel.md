---
title: "system crash after upgrade to newest kernel"
date: 2006-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by jasonli on 2006-02-13
hello there. I upgraded just now to the newest ppc kernel(sorry i forgot the version number), and according to the post-upgrade message, I restarted the system as soon as upgrade was finished. but it crashed.

in start up, the following message was shown:
30.019495]aty128fb: invalid rom signature 8181 should be 0xaa55
40.156241]RAMDISK: ran out of compressed data
40.156467]invalid compressed format (err=1)
40.157525]kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
40.157806]

anyone has any idea about this? I am using a iMac G3 500, 128mb ram, ubuntu 5.10

---

### Post by ssam on 2006-02-13
if you press [tab] at the second yaboot screen you should be give a choice of kernels, including the previous one you had installed. hopefully that will work and you can boot.

then you should probably file a bug at [http://launchpad.net/malone](http://launchpad.net/malone)

---

