---
title: "Triple booting Hardy 64-bit ..."
date: 2008-06-29
forum: x86 64-bit Users
---

### Post by orrorin on 2008-06-29
My dual-boot PC currently has Feisty 32-bit and Vista (pl. refer to hardware in my signature). I want to install Hardy 64-bit to use all my 4GB of RAM and make it triple-boot.

My questions are about disk partitioning; pl. refer to the attached jpeg for how I've partitioned my 250GB disk to do this.

sda1: (current) boot partition [has grub and loads Feisty and Vista today]
sda5: linux-swap (currently used by Feisty)
sda6: / for Feisty
sda7: /var for Feisty
sda8: swap for Hardy (but I'm not sure if I need it; I'd rather use sda5)
sda9: / for Hardy (currently shows ext2; but looks like I need to make it ext3)
sda2: ntfs for Vista

Now, my questions ...
1. can I use my existing /boot (which is ext2) for Hardy as well? When I try to do that while installing HArdy, it seems to indicate that the existing dirs and files will be deleted! How do I do this?
2. Can I use the existing linux-swap for Hardy or do I need a separate swap, given that my current swap is for a 32-bit system.
3. Will 64-bit Hardy work with ext2 for "/"?

---

### Post by kuja on 2008-06-29
I strongly recommend **[color=red]*against*!![/color]** sharing the /boot partition. It can cause problems. (not like a few 150MiB ext2 partitions are going to hurt you anyway)

You may be able to share the swap .... I've tried it before and I think it works ... IIRC knoppix will use it if it sees a swap partition on your disk.

It will work with ext2 for /, but it won't have as much fault tolerance (ie: no journal) as ext3.

---

### Post by orrorin on 2008-06-30
> **kuja said:**
> I strongly recommend **[color=red]*against*!![/color]** sharing the /boot partition. It can cause problems. (not like a few 150MiB ext2 partitions are going to hurt you anyway)

You may be able to share the swap .... I've tried it before and I think it works ... IIRC knoppix will use it if it sees a swap partition on your disk.

It will work with ext2 for /, but it won't have as much fault tolerance (ie: no journal) as ext3.

Thanks kuja. I ended up not sharing the /boot for Feisty and Hardy. So, Feisty gets to keep the stand-alone boot partition, though I wish there was some way to share it with Hardy (so all my kernels would be on the same partition). Hardy's /boot is co-resident with its "/" and I used the "configfile" directive in its menu.lst to point to Feisty.

The /swap can be (and is being) shared between Feisty and Hardy, though I hope I never really have to use it.

Hardy's "/" is using ext3.

I found the hermanzone website ([http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)) very useful.

---

