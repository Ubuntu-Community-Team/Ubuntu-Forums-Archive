---
title: "[SOLVED] Two CDs for Counter Strike Installation"
date: 2008-02-09
forum: Wine
---

### Post by ashmew2 on 2008-02-09
Hey People. I bought Counter Strike 1,6 recently and it has 2 Installation CD Roms.I use wine to start the installation after inserting CD 1 but mid way after installation it asks me to insert the second CD. But I fail to do so because I cannot Eject The Cdrom as it says that its busy. I have created .ISO files of both CDs if that can help.

Thanks

---

### Post by csat on 2008-02-09
> **ashmew2 said:**
> Hey People. I bought Counter Strike 1,6 recently and it has 2 Installation CD Roms.I use wine to start the installation after inserting CD 1 but mid way after installation it asks me to insert the second CD. But I fail to do so because I cannot Eject The Cdrom as it says that its busy. I have created .ISO files of both CDs if that can help.

Thanks

How about umount /media/cdrom  && mount /media/cdrom and try again?

---

### Post by ashmew2 on 2008-02-09
says the Device is Busy.

---

### Post by LinuxGamer on 2008-02-09
I have had good luck with creating a directory in my home directory and copying all the files from both cds into it, then just start the install from there.

---

### Post by ashmew2 on 2008-02-09
YAY ! Got it fixed. Merged Both the ISOs and mounted it and It didnt ask for the CD ROM. :D
If any1 wants to know in details , let me know.

---

### Post by ashmew2 on 2008-02-09
thx LinuxGamer , i did the same thing , I missed your post somehow.

---

