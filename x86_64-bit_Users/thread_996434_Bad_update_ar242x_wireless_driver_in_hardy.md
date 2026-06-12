---
title: "Bad update: ar242x wireless driver in hardy"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by wangjiajun on 2008-11-28
Dear friends,

I have a AR242X wireless card in my laptop Toshiba L355D-S7815. 

I managed to get the wireless working for me following this page's instructions:
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

However, each time I update some key components of my Hardy (items like Linux-Header, usually requires reboot after updating), the wireless card goes down. I have to redo the instructions to revive it. I think this is stupid and I want to figure out 

1. Are there any ways to avoid updating caused trouble?

2. Any other driver I should try to avoid the updating problem?

Thanks for any clue.

---

### Post by IanW on 2008-11-29
The instructions have you compiling the driver to work with your _current_ kernel (package name something like linux-image-2.xx.yy).
If the kernel changes, the driver must too.

You can lock packages using Synaptic so they won't be updated.

---

