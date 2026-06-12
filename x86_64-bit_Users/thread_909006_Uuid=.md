---
title: "Uuid="
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by C. Wizard on 2008-09-03
What are these UUID= numbers in the fstab file?
I never saw anything like that in the fstab file when I was running Slackware.
Thanks.

---

### Post by cdtech on 2008-09-03
UUIDs are unique identifiers generated when the file system is created. If you change how the hard drives are connected to your system (for example primary/secondary) the UUID doesn't change, whereas the device (/dev/sda) can change.

---

### Post by C. Wizard on 2008-09-03
> **cdtech said:**
> UUIDs are unique identifiers generated when the file system is created. If you change how the hard drives are connected to your system (for example primary/secondary) the UUID doesn't change, whereas the device (/dev/sda) can change.

Thank you for the reply.
Identifiers of what to whom? They are certainly not necessary for the system to run correctly so what purpose do they serve?
Thanks, again.

---

### Post by Jouke74 on 2008-09-03
Read his post again, they Identify the hardware uniquely, although not essential to run linux, it can make life a lot easier if you have to identical drives. You can swap disks more easily on your controller. It seems b.t.w. a typical thing for Ubuntu, and in case you mess up your fstab it can make life a bit more more difficult. E.g. when you do a reinstall you cannot use your old fstab because new uuids are generated.

---

### Post by fballem on 2008-09-03
> **Jouke74 said:**
> Read his post again, they Identify the hardware uniquely, although not essential to run linux, it can make life a lot easier if you have to identical drives. You can swap disks more easily on your controller. It seems b.t.w. a typical thing for Ubuntu, and in case you mess up your fstab it can make life a bit more more difficult. E.g. when you do a reinstall you cannot use your old fstab because new uuids are generated.

I'm attaching a snapshot of my /etc/fstab file. Am I correct in assuming that I could remove the actual UUID and uncomment the /dev/sda1 and /dev/sda5 lines and it would work?

If that is 'yes', then it strikes me that an appropriate strategy would be to do that and make a copy of it. If you have to reinstall ubuntu, then use the copy to replace the new /etc/fstab file that is created during the re-install.

Just a thought,

---

### Post by cdtech on 2008-09-03
Yes, you are correct.......

---

### Post by soxs on 2008-09-03
Thy can be obtained by ```
sudo blkid
``` or ```
ls -l /dev/disk/by-uuid|cut -f 8-10 -d " "
```

---

