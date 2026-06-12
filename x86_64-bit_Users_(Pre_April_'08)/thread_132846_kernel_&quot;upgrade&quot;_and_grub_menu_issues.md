---
title: "kernel &quot;upgrade&quot; and grub menu issues"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tink on 2006-02-19
Hi,

I'm running a customised 2.6.15 kernel ... how do I stop ubuntu
from "ugrading" to older versions (I don't really want that 2.6.12
kernel) and butchering my grub menu in the process?


Cheers,
Tink

---

### Post by wjp.reg on 2006-02-19
[QUOTE=Tink]Hi,

I'm running a customised 2.6.15 kernel ... how do I stop ubuntu
from "ugrading" to older versions (I don't really want that 2.6.12
kernel) and butchering my grub menu in the process?


Cheers,
Tink[/QUOTE]

Tink;

Normally a kernel upgrade through apt-get or synaptic will cause menu.lst to be rewritten to include the old and new kernels, and you can edit the list if you don't want both to appear.

---

### Post by Tink on 2006-02-19
I realise that, that's why I'm asking how to stop apt from
getting the kernel in the first place.  It clobbers the layout,
and stuffs up the map lines that I require for dual-booting
eXPeriment (it strips the space between the two sets of
parenthesis which makes the map commands fail).  I don't
feel that I should have to re-edit my menu.lst just because
ubuntu thinks it knows better than me which kernel is good
for me (which it doesn't - the MoBo won't work with any kernel
older than 2.6.15 in the first place!!!)... 

I want to not have to download older kernels and fix a config
file as an extra penalty for receiving old carp. :}


Cheers,
Tink

---

### Post by Daggett on 2006-02-20
I'm not sure this would work in Kubuntu, but what I did in Debian was to uninstall ALL kernel image packages.  Once they're gone, apt doesn't see anything to update, so it doesn't download the "latest" versions ever again.

---

