---
title: "kernel update broke suspend/hibernate"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by logos34 on 2008-05-26
why o why do I seem cursed when it comes to a simple thing like suspend?  It's almost never worked properly on x64 until Hardy.  Finally my problems are over, I thought.  But noooo...they had to go update (*improve* -yeah, sure) the kernel yesterday (i.e. -rt kernel) and now I'm back to square one.  I cannot resume from either state.

Must I fall back to -16-rt? Here's the line that's worked for me until now in menu.lst:

> kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=d77656b5-aa1c-4375-8bfa-b517cebff023 ro splash **resume=/dev/hda8**

Ideas anyone?
(by the way, changing it to sda8 doesn't work, nor does deleting it)

---

