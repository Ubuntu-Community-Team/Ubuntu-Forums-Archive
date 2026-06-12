---
title: "Many harddisk access"
date: 2009-05-19
forum: x86 64-bit Users
---

### Post by eliudhr on 2009-05-19
Hi guys!

Yesterday install  x86 -64bits version. The install ok, work very smooth only, now I can see that my hard disk led is always in ON. 

I dont know why my ubuntu version has many access to hard disk, is it normal ? or I need to configure, kill o uninstall any packages to have less access at the hard disk.

Any idea?

Thanks in advance :)

Eliud

---

### Post by Fir3chi3f on 2009-05-19
to lower my disk usage I add the option noatime to all my partitions except swap in my /etc/fstab. It really seems to help and I have never had problems with it that I could tell.

Here is an example in my fstab after running the command ```
sudo gedit /etc/fstab
```

Example entry
```
#media partition
/dev/sda3       /media/media    vfat       users,rw,uid=1000,gid=100,utf8,dmask=027,noatime,fmask=137 0 0
```

---

### Post by eliudhr on 2009-05-19
Thanks ! I change the configuration in fstab, restart and the hard disk led is always in ON.

Eliud

---

