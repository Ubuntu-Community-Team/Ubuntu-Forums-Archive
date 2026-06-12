---
title: "strange problem"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by Somenoob on 2008-05-02
I just upgraded to 8.04 and on the first 3 days it has been working perfectly but recently for some reason it has been crashing shortly after booting. I'm sure it has something to do with my external usb wi-fi adapter, the only way to prevent it is to plug it into a another USB slot each time I turn on the computer.  

I tried reinstalling Hardy Heron but the problem remains.

Thanks in advance.

---

### Post by tech9 on 2008-05-02
did you install Hardy - "clean" or upgrade?

---

### Post by Somenoob on 2008-05-02
> **tech9 said:**
> did you install Hardy - "clean" or upgrade?

Clean.

---

### Post by tech9 on 2008-05-02
> **Somenoob said:**
> Clean.

strange...


take a look at your fstab file - post your output

---

### Post by Somenoob on 2008-05-02
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=05821154-30fa-488e-8a53-565e90dceb58 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=1a177fd1-3b5d-48e5-aeeb-915e907043ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Somenoob on 2008-05-02
The machine also behaves undesirably when I connected my digital camera, the F-Spot Photo program fails to launch after the first time it worked well. Also the wireless LAN isn't working very well if compared to how it works on 7.10.

What could be wrong? I want to stay with 8.04

---

### Post by tech9 on 2008-05-05
your fstab looks ok... your booting from liveCD?

What happens when you try booting without your usb wi-fi?

---

