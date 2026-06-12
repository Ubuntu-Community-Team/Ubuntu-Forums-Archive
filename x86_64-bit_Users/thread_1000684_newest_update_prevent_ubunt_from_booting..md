---
title: "newest update prevent ubunt from booting."
date: 2008-12-03
forum: x86 64-bit Users
---

### Post by aboud on 2008-12-03
yesterday i install fresh ubuntu 8.10 64 that i downloaded week ago, right away i update it, we i reboot an error appeared after grub loader:

error 15 
file not found.

and this is the same for the 4 variants kernel. 
same thing happened when i tried 8.04 64. 
from this point windows is loading normally. 

I think it's beacuse of the update, because few days away we i did the same thing using the same CD every thing went fine.

could it be because of my boot partition is just 130 MB ? 

now i reinstall 8.10 64, but i'm not updating. 
_______________________________________________________________________
vaio T2D, 2GB.

---

### Post by Yellow Pasque on 2008-12-03
Can you pop in a LiveCD and post the /boot/grub/menu.lst file (assuming you get an internet connection with a LiveCD)? Also, if you have a /boot/grub/device.map, post that too.

---

### Post by aboud on 2008-12-03
device map
```
(hd0)	/dev/sda
```

menulist
```
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=24d0ba6a-69d5-4d7d-81ac-3b3b98f19a72 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=24d0ba6a-69d5-4d7d-81ac-3b3b98f19a72 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=24d0ba6a-69d5-4d7d-81ac-3b3b98f19a72 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=24d0ba6a-69d5-4d7d-81ac-3b3b98f19a72 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by aboud on 2008-12-03
those are the date you asked me for, but please don't bother your self to resovl my problem, because i returned to 8.04 32, and i have no plane in the near future to update again.

---

### Post by Yellow Pasque on 2008-12-03
Is your boot partition /dev/sda5? That's what hd0,4 points to.

---

### Post by aboud on 2008-12-03
excatly, that how it was. 

/dev/sda5      /boot
/dev/sda6      swap
/dev/sda7      /

but now i installed without separating boot.

---

### Post by aboud on 2008-12-03
all right back to 8.10 64.

another problem I think can help solve the first one. 

fsck on boot is tell me 
```

Log of fsck -C -R -A -a 
Thu Dec  4 08:57:22 2008

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=9378714f-f4f9-4494-9149-2332e8c8f87c'

fsck died with exit status 8

Thu Dec  4 08:57:22 2008
----------------

```

while vol_id --uuid /dev/sda7 shows 
```

5524dc3e-73e5-4f3c-a359-1fa5ad34c8fd

```

this time i have every thing on one partition, and it's working.

---

