---
title: "Lost my GUI Screen Blank W Cursor"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by skrap on 2008-10-18
Help! I inadvertently deleted via synaptics my guile file and when I rebooted the screen was black with a cursor that I could move around.  I have GeForce 6100 nividia graphics on a amd 64 processor and I am running the 64 bit version of 7.10 gutsy.

I have checked that the drivers are loaded and I can get the gnome desktop manager started but I still end up at the same place.

I have reloaded the OS onto another partition and enabled the restricted drivers for that install and it works fine but I do not want to have to reload all of my programs and profiles if I do not have to.

How can I restore the original OS to its previous state?  I think this is a problem with the Nvidia drivers but not sure.

---

### Post by cariboo on 2008-10-18
You could run diff in /etc on the two partitions to see what the difference in configuration files are. Run something like:

```
sudo diff -y /mountpoint1/etc /mountpoint2/etc
```

the -y option outputs two columns. Mountpoint 1 and 2 are where the partitions are mounted.

Jim

---

