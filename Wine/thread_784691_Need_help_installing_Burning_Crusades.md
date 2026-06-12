---
title: "Need help installing Burning Crusades"
date: 2008-05-06
forum: Wine
---

### Post by malfist on 2008-05-06
A friend loaned me their Burning Crusades CD's and I ripped them to an iso using dd.

But when I try to install it, anything past the first CD it just tells me, please insert X CD. I don't know what to do. I mount the second image where the first CD's is but it just can't find it.

Anyone have any suggestions?

---

### Post by original_jamingrit on 2008-05-06
is this a wine game?  Check your winecfg, it should be able to change the location where wine looks for the disc.

---

### Post by rywibr on 2008-05-06
hmmm.... I think I have a craving for WoW again, it's been like 5 months. Maybe I'll install it :)

Thanks for getting me thinking about the worlds most addicting game again :P
-ryan

---

### Post by schtufbox on 2008-05-06
> **malfist said:**
> A friend loaned me their Burning Crusades CD's and I ripped them to an iso using dd.

But when I try to install it, anything past the first CD it just tells me, please insert X CD. I don't know what to do. I mount the second image where the first CD's is but it just can't find it.

Anyone have any suggestions?

Just copy the files to a folder and install from there.

---

### Post by malfist on 2008-05-06
nevermind, extracted all the mpq's to one directory and ran the installer from there.

edit: that sounds harsh, sorry. I forgot to refresh and didn't see that anyone had helped me, sorry.

---

### Post by pedro_orange on 2008-05-07
If you're installing it from the CDs you can just tell Wine to let go of the CD Drive via the command:

```
wine eject d:
```

Where d: is the label that represents the drive letter for your CD drive.

Happy WoWing!

---

