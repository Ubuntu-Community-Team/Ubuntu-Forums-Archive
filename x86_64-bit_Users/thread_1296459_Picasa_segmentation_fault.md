---
title: "Picasa segmentation fault"
date: 2009-10-20
forum: x86 64-bit Users
---

### Post by Jellyffs on 2009-10-20
Hi,

I run Jaunty 64Bits. Seems like I can't use Google's applications. Neither Picasa or Google Earth start.
[B]
_Picasa give, as a user or root_ (version 3.0.5744-02):[/B]

```
jelly@superdupont:~$ picasa
Segmentation fault
Segmentation fault
Segmentation fault
jelly@superdupont:~$ sudo picasa
[sudo] password for jelly: 
Segmentation fault
Segmentation fault
Segmentation fault
```**_Google Earth gives_ (Version 5.0.11337.1968-0medibuntu10):**

```
jelly@superdupont:~$ googleearth 
/usr/lib32/googleearth/googleearth-bin: /lib/i686/cmov/libc.so.6: version `GLIBC_2.8' not found (required by /usr/lib32/libglib-2.0.so.0)
jelly@superdupont:~$ sudo googleearth 
[sudo] password for jelly: 
/usr/lib32/googleearth/googleearth-bin: /lib/i686/cmov/libc.so.6: version `GLIBC_2.8' not found (required by /usr/lib32/libglib-2.0.so.0)
jelly@superdupont:~$ 
```**And guess what... I have no idea why :(**

What should I do?

Thanks,

Alex.

---

### Post by emma48 on 2009-10-25
Hello, same here.

picasa does not start. I have removed the application, add the google repo to the repository list and installed the last stable version 2.7. through apt-get.

---

### Post by Jellyffs on 2009-10-28
Well... moving to Karmic solved the problem. For now...

---

### Post by CrazyMike on 2009-11-02
I thought I had the answer here by going to the /usr/lib32/googleearth directory and adding the libGL.so.1 symbolic link I found in other disucssions on this topic.  Google Earth finally opened!  Posted here that it was a fix but I must say DONT DO IT!  As soon as I went to play with GE, i noticed there was no earth in the viewer, just a black screen.  To make matters worse, it f'd up my clean install of Karmic.  Now I have to figure out why the file manager and gnome-panels have 60+ second lags and other problems.  Looks like a reinstall unless someone has any other ideas...

---

### Post by kellerf on 2009-11-03
> **Jellyffs said:**
> Well... moving to Karmic solved the problem. For now...

Hi,
moving to Karmic worked oposite with me. What worked in 9.04 does not work in 9.10 as far as picasa is concerned.
I can run picasa as root, but not as user. It sends this message:

/usr/bin/picasa: &#345;ádek 139: 11932 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: &#345;ádek 175: 12031 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

Any advice? 
Thanks!

---

### Post by agibby5 on 2009-11-15
> **kellerf said:**
> Hi,
moving to Karmic worked oposite with me. What worked in 9.04 does not work in 9.10 as far as picasa is concerned.
I can run picasa as root, but not as user. It sends this message:

/usr/bin/picasa: &#345;ádek 139: 11932 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: &#345;ádek 175: 12031 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

Any advice? 
Thanks!

Having the same issue under a fresh install of Karmic.

---

