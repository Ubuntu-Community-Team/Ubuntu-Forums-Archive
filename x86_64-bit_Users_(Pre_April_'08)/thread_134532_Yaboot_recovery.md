---
title: "Yaboot recovery"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicodds on 2006-02-22
Due to some brain damage, I wrote a wrong image name on the yaboot.conf file. 
The bootloader, so, fails to boot my system. 

I know I could pass directly the image to boot on the prompt and, after some
tries, I was able to find the right string to boot the correct linux image. 

The problem now is the root partition that I'm not able to set correctly; at the
prompt, I give the following string:

```
/pci..../bhla.../bhla...,/image-path root=/dev/hda3
```

but the kernel goes in a panic, giving me the following message:

```
VFS: Cannot open root device "hda3" or unknown-block(0,0)
Please append a correct "root=" boot option
...
```

I'm making mistakes on the syntax to use? Could someone tell me the right one?

Thanks, 
Nico

---

### Post by khc on 2006-02-23
What I usually do is just take the LiveCD and edit the file.

---

### Post by jdp on 2006-02-24
But are you sure its HDA3?  On a MAc it'll usually be around hda5, 6 or 7.

---

### Post by nicodds on 2006-02-26
Thanks, the problem was in the initrd directive... at the time of the writing, I couldn't get a powerpc live cd :-(

Nico

---

