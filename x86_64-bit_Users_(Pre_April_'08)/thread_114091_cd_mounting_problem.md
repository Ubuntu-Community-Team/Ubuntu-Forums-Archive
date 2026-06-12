---
title: "cd mounting problem"
date: 2006-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by penguain on 2006-01-07
i've run ```
mount /dev/hdc /cdrom
``` and that doesn't work is that wrong??? im running 5.10 on a G3 iMac 333Mhz 192RAM

Thanks In Advance

Penguain

---

### Post by super on 2006-01-08
could you post the contents of /etc/fstab so i can take a look?

maybe you don't have a filesystem type specified.

---

### Post by penguain on 2006-01-08
i can post it because my ubuntu doesn't have internet but i looked at it ran
```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```
and
```
sudo mount -t iso9660 /dev/hdc /cdrom
```

both gave me
```
mount: No medium found
```

---

### Post by super on 2006-01-08
make a back-up copy of /etc/fstab then try changing [FONT="Courier New"]iso9660[/FONT] to [FONT="Courier New"]auto[/FONT] in the fstab.

---

