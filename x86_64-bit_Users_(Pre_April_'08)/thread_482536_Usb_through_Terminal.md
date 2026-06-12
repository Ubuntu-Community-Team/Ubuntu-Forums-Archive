---
title: "Usb through Terminal"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aidan1234 on 2007-06-23
i have a nvidia driver on a usb drive.

How do i navigate to the drive from the terminal?

so far i taught myself:

fdisk -l

fdisk /dev/sdb1

then what?

or is that wrong?

---

### Post by thelinuxguy on 2007-06-23
You should see your drive mounted under /media.

If it is not mounted for any reason, try mounting it manually:
```

mkdir /media/usb
sudo mount /dev/sbd1 /media/usb

```

---

### Post by BobCFC on 2007-06-23
Just to be clear mkdir means make directory and you only need to do this once.

---

### Post by thelinuxguy on 2007-06-24
> **BobCFC said:**
> Just to be clear mkdir means make directory and you only need to do this once.

Yeah! I should have thought about mentioning that. Thanks for the correction.

---

