---
title: "&quot;Delete&quot; a partition"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by Combs on 2009-02-02
Hello Ubuntu friends, i'm very happy to talk to yall again :D
How are you today ? I'm pretty well :)
So during my "Linux testing days" I would like to "remove" Windows Wonstart(a.K.a vista ^^) by deleting a partition! Under Vista, we can do it via the right click on the "computer"icon and blablabla...
Please help me :D
Thank you so much again and have a nice day :KS

---

### Post by drs305 on 2009-02-02
In ubuntu most partition work is done with gparted (Partition Editor). It is accessible via System, Administration, Partition Editor. 

If you can't find it, you can install it with: 
```
sudo apt-get install gparted
```

It would work on removing windows if you really want to do that. It also resizes partitions, allows you to label a variety of file systems and more.

To do work on the ubuntu system partitions, shoud you need to do so, you will need to run it from the LiveCD or a third-party CD such as the SystemRescueCD or gparted CD. Gparted won't allow operations on *mounted* partitions.

One note if you are deleting partitions. Most of ubuntu's system files have changed from designating devices (and partitions) from "sdXX" to UUIDs. If you delete a partition and your system files still refer to "/dev/sdXX" (such as /dev/sda1) you may have problems. It would be best to change these to use UUIDs. You can check your menu.lst and fstab settings to see if they are using "/dev/sdXX" or UUIDs with the following commands:
```

cat /etc/fstab
cat /boot/grub/menu.lst

```

---

### Post by Combs on 2009-02-02
> **drs305 said:**
> In ubuntu most partition work is done with gparted (Partition Editor). It is accessible via System, Administration, Partition Editor. 

If you can't find it, you can install it with: 
```
sudo apt-get install gparted
```

It would work on removing windows if you really want to do that. It also resizes partitions, allows you to label a variety of file systems and more.

To do work on the ubuntu system partitions, shoud you need to do so, you will need to run it from the LiveCD or a third-party CD such as the SystemRescueCD or gparted CD. Gparted won't allow operations on *mounted* partitions.

One note if you are deleting partitions. Most of ubuntu's system files have changed from designating devices (and partitions) from "sdXX" to UUIDs. If you delete a partition and your system files still refer to "/dev/sdXX" (such as /dev/sda1) you may have problems. It would be best to change these to use UUIDs. You can check your menu.lst and fstab settings to see if they are using "/dev/sdXX" or UUIDs with the following commands:
```

cat /etc/fstab
cat /boot/grub/menu.lst

```

Thank you mayne..But what I just needed to do is deleting the partition and re-creating one on the HDD. I think that I won't have problem(s) isn't it xD
by the way, thank you so much :d

---

### Post by Combs on 2009-02-03
> **valve2009 said:**
> A **[ball valve](http://www.google.ch)** is a valve that opens by turning a handle attached to a ball inside the valve. The ball has a hole, or port, through the middle so that when the port is in line with both ends of the [ball valve]("http://www.nothing.com") flow will occur.

A spammer is someone who get mad because people are nice :)

---

