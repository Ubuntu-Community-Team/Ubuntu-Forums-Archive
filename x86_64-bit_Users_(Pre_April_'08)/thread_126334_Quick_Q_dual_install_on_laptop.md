---
title: "Quick Q: dual install on laptop"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by meenfreem on 2006-02-06
Right... so we have a new HP pavilion dv5000 (never mind the condolences, heard them:P). And it comes with windoze installed on it. Partition is c: alone.

Now I need to install Ubuntu on it too. We'll need both OS's, but now my question is: If I install Ubuntu on this machine, will it 'split' up the c: partition during the Ubuntu setup? Or do I need to do it before hand? As you all probably know all too well, re-installing windoze with a HP rescue disk is no easy task and will most likely take the better half of a day... so I really don't want to 'accidentally' have to delete the c partition in order to create two (three) partitions.

If ubuntu won't 'split' the partition, reckon that partition magic will do the trick?

---

### Post by joft on 2006-02-06
Hi,

AFAIK ubuntu will not split such partitions.
(Furthermore it had to resize the Windows partition and would need "real" NTFS support for that (even more than just reading and writing), assuming your Windows uses NTFS on that partition.)

So, use a partition management application to do that. PM would be one ...

---

### Post by newuser111 on 2006-02-06
use the gparted livecd, i have resized ntfs partitions with it without any data loss

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

after that let ubuntu cd create partions out of the free space

---

### Post by meenfreem on 2006-02-07
thanks, I'll give the gparted a go... looks good :D

---

### Post by meenfreem on 2006-02-08
update:
PartitionMAgic gives me the 117 error (can't find the partition letter) and won't start in windoze. How typical. A way around this would be to run it in Dos mode. 

Gparted wants me to rename the c: drive, it doesn't seem to recognise it. Doing this will erase the drive :S Exactly what I was trying to avoid. 

Any ideas? I'm kind of lost and I'd still rather not reinstall windoze.

---

### Post by plors on 2006-02-08
What do you mean exactly by 'split'?

And what do you mean by 'Gparted wants me to rename the c: drive, it doesn't seem to recognise it. Doing this will erase the drive' ?

---

### Post by muzcuk on 2006-02-08
I have a compaq presiaro v2000z computer and I had the same single partition issue. I just acted brave and started installing ubuntu (64 bit) and it asked me how much space I'd like to subtract from windows partition, I sain 10GB, then it resized ntfs partition, made 2 ext3 and 1 swap partitions and mounted them all by itself. no problems at all. It should work for you too, why not?

for your problems with partition magic, try doing a scandisc, there might be something wrong with the partition tables (windows is good at messing itself up, you know) and scandisc will probably fix it..

---

### Post by sylvester_0 on 2006-02-08
He's right..but in today's world it's called check disk....chdsk

---

### Post by meenfreem on 2006-02-10
well... decided to repartition the disk the hard way :D 

now I'm just having problems installing ubuntu on my hp dv5000 (turion 64, with ATI 200m graphics card). Been reading through the forums and it seems I'm not alone on this one. There are several threads on the subject but haven't found a solution yet. If anyone reading this has a good link for me... would be greatly appreciated.

---

