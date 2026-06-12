---
title: "How do I access the wine directories?"
date: 2008-10-03
forum: Wine
---

### Post by askyourpc.com on 2008-10-03
How do I access the wine directories as I would access the C drive in windows and look at the files and folders?
Thanks

---

### Post by david_kt on 2008-10-03
> **askyourpc.com said:**
> How do I access the wine directories as I would access the C drive in windows and look at the files and folders?
Thanks

At least there are three easy ways:

1. Application > Wine > Browse drive C
2. Places > Home folder > press <ctrl> <H> > .wine > drive_c
3. Application > accesories > terminal > type "winefile" <enter>

DK

---

### Post by alynx on 2008-10-03
yes or in terminal go to your home directory and type cd .wine

there you have drive_c and contents under that

---

### Post by david_kt on 2008-10-03
> **alynx said:**
> yes or in terminal go to your home directory and type cd .wine

there you have drive_c and contents under that

No, that would browse drive_c using command line, not what the askyourpc.dom ask: "as I would access the C drive in windows"

Unless he access C drive in windows using :
Start > run > cmd <enter>  :D

DK

---

### Post by alynx on 2008-10-03
but but , console ...... 

hehe ok i get it.  the point is that the wine folder under your home directory is hidden , hence the .wine 

So if you browse your home folder /home/username/ 

Just add .wine after

```
/home/username/.wine/c_drive/ 
```

---

