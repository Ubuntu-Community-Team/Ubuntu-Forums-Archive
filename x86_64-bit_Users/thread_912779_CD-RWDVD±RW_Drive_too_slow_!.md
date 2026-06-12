---
title: "CD-RW/DVD±RW Drive too slow !"
date: 2008-09-07
forum: x86 64-bit Users
---

### Post by x_error on 2008-09-07
hey there i have a sony CD-RW/DVD±RW Drive but it is running too slow and when i click properties it says that the drive is unknown type so how can i configure it as sony CD-RW/DVD±RW and will it be faster if i do that and here is a screen shot

---

### Post by x_error on 2008-09-07
here's the screen shot

---

### Post by insane_alien on 2008-09-07
that won't make it faster, mine says the same thing and runs at full speed. 

look in your BIOS see if there is a power option for your drive (mine has, silent, normal, performance) that usually affects the speed of the motor.

edit, just experimented and it has all those unknowns because you don't have a disc in it. those unknowns reffer to the media rather than the drive.

lshw will show you the details of the drive.

---

### Post by x_error on 2008-09-07
how can i see my BIOS ?!!

---

### Post by insane_alien on 2008-09-07
depends on the computer, F1 or F10 or F11 or F12 or escape upon boot are usually the ways to access it though i have seen other methods but not as much as those.

---

### Post by nikgare on 2008-09-10
What makes you think it's running too slow?

---

### Post by x_error on 2008-09-10
because some cds and dvds work normally on windows while on ubuntu they are too slow and same happens with writing cds and erasing them

---

### Post by nikgare on 2008-09-10
Are these SATA, IDE or SCSI attatched drives?
What does the output of ths say:

```
sudo hdparm path_to_your_drive
```

---

