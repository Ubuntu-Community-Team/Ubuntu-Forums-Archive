---
title: "fstab or lilo.conf"
date: 2005-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-01-25
I am using a gnoppix liveCd to fix my grub not loading problem by installing lilo, but when i run liloconifg it figures out that i am running from a live cd and that fstab is not  what i need, so if i need a lilo,conf or someones fstab, i am trying to install    array-3 on an  emachines M6805

---

### Post by runenes on 2005-01-25
Have you tried chrooting in and running "grub-instal install_device", for example
```

$ mkdir /mnt/ubuntu
$ mount UBUNTU-ROOT-PARTITION /mnt/ubuntu
$ chroot /mnt/ubuntu /bin/bash
$ source /etc/profile
$ grub-install UBUNTU-ROOT-PARTITION

```
If what you want is to install grub from the ubuntu distro on the MBR of the ubuntu root partition. 
WARNING destructive commands if this is not what you want!

---

### Post by blinksilver on 2005-01-25
where would i do this from?/

---

