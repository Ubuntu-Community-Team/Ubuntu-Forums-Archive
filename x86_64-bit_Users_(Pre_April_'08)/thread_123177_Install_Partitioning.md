---
title: "Install Partitioning"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by macaodha on 2006-01-29
Hi, 
Im trying to install ubuntu on my laptop to be dual booted with xp. i get as far as the partitioning screen then when i try and resize my xp partition it doesnt seen to do anything.
i have a 60GB hard disk with 20 free, but it only list me as having 8mb free. 
Any ideas?

---

### Post by Sutekh on 2006-01-29
[QUOTE=macaodha]Hi, 
Im trying to install ubuntu on my laptop to be dual booted with xp. i get as far as the partitioning screen then when i try and resize my xp partition it doesnt seen to do anything.
i have a 60GB hard disk with 20 free, but it only list me as having 8mb free. 
Any ideas?[/QUOTE]

It sounds like you have 20GB free space ON the windows partition.  

You need to create a separate partition for Ubuntu, it can't just be installed on the free space.

You will need to resize your Windows XP partition to a smaller one, and then Ubuntu can be installed on the remaining space.

This link has a good tutorial to install Ubuntu.  It has screenshots of the installation process and will walk you through resizing your Windows partition and creating one for Ubuntu.  Have a read, make sure you understand all the steps before you give it a shot.

[Installing Ubuntu and Windows (NTFS) - (hermanzone's awesome tutorials)]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by macaodha on 2006-01-30
i was trying to resize it, but it wouldnt let me. every time i tried to rezie it it would just go back to the main screen showing the partitions, but it was the same. 
greats minds think alike, i was actually following that tutorial.

---

### Post by BlakcTigers91 on 2006-01-30
I Dont think you can resize a Used Partition.  I always had to reformat, and do my partitioning from there.  Ubuntu needs it's own, it cant share.  You have a 60GB Partition, and 20GB Free.  Thats why its showin up that you have only 8mb for the other partition.

---

### Post by macaodha on 2006-01-30
the impression i got from the ubuntu installer was that you could resize it.

---

### Post by BlakcTigers91 on 2006-01-30
Nope.  If you have FREE (unpartitioned) space, it can be partitioned.  Try Partition Magic, to repartition you Drive.

---

### Post by macaodha on 2006-01-30
ill give it a go. thanks for your help.

---

