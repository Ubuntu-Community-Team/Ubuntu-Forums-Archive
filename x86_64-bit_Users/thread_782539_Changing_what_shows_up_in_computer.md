---
title: "Changing what shows up in computer:///"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-05-05
I recently created a software RAID-1 on my system which was already running Hardy 64-This was quite a challenge by itself, but it created a small bug which I think I'll file a bug report for, but wondering if anyone on the forums can help.

I've attached a screenshot of computer:///

My "filesystem" is now a RAID-1 comprised of sdb1 and sdc1```
ryan@ryan-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      112414720 blocks [2/2] [UU]
      
unused devices: <none>
``` And the drive called "115.1 GB Media" is now part of the RAID, yet it still shows up in computer:///

This drive if I try to mount it, quite expectedly it says that it's already mounted somewhere else. I would like to remove this drive from showing up in computer:/// as it's not really useful/can't be mounted.

Thanks in advance

---

### Post by ASULutzy on 2008-05-05
bump

---

### Post by fjgaude on 2008-05-05
I believe this is a bug that has been reported for 8.04. If you use Nautilus' Places menu, go to Media and then see all the locked drives showing which you can't access from there. The Places versions of them can.

Likely we'll have to wait until the developers fix this little mess. Can't say what it hirts though.

How you doing on your HOW-TO for raid0?

---

### Post by ASULutzy on 2008-05-05
I'm at work now, I'm going to dig up the post today and use it to make a HOWTO.

I just really have to stress how tricky it was to do, and it's not something I'd recommend for someone to try cause they're bored. :P

---

