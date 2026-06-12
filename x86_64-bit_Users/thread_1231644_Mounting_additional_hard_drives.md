---
title: "Mounting additional hard drives?"
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-08-04
I've got a small problem.

I've added some new hard drives.
Created some partitions and formatted them with ext4.
I've then modified my fstab files with the following lines:

/dev/sda1 /data1                auto    defaults        0       0
/dev/sda2 /data2                auto    defaults        0       0
/dev/sde /data7                 auto    defaults        0       0

The drives gets mounted fine, but I am unable to write to them. Presumably it's a permissions issue because I can write to them if I mount them as:

/dev/sda1 /home/niw/data1                auto    defaults        0       0
/dev/sda2 /home/niw/data2                auto    defaults        0       0
/dev/sde /home/niw/data7                 auto    defaults        0       0

I want the drives and partitions to be available to all users.

Help please!

TIA.

---

### Post by JohnLau on 2009-08-04
):P
Try 
```
sudo chmod a +rw /data1 -R
sudo chmod a +rw /data2 -R
sudo chmod a +rw /data7 -R
```
This adds read and write permission to all users.

John

---

### Post by niw_uk1964 on 2009-08-05
Thanks very much John. I will try that today :)

I'm learning all the time and although I have played with Linux on/off for a few years I have finally decided to jump to it full time now...hence the questions as I start digging deeper.

---

### Post by niw_uk1964 on 2009-08-05
Sorted.

Thanks very much.

One more question if I may? How do I remap specific folders in my home directory to directory on these drives?

---

