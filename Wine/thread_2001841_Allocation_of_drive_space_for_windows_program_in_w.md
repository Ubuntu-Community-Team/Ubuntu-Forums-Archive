---
title: "Allocation of drive space for windows program in wine ?"
date: 2012-06-11
forum: Wine
---

### Post by userqq on 2012-06-11
Hi, I am running steam on wine and TFC plays just fine but when I start TF2 all is well until it starts to load the map and then computer hangs. It begins to load map but wont complete it, my HD is clicking normally (not stuck) and I can move the mouse but it just wont load.
So heres the question: TFC only requires 532 mb of disc space but TF2 requires 10616 mb of disc space and** im wondering if my standard install of wine on ubuntu 12.04 has not allocated enough drive space for this large windows program**. ??
I just ran **df -h** and heres what I got. I am not so good at this so I dont know what this means.

user1@user1-ThinkPad-R52:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        37G   19G   16G  54% /
udev            494M  4.0K  494M   1% /dev
tmpfs           201M  860K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M   80K  501M   1% /run/shm
user1@user1-ThinkPad-R52:~$ 

Help appreciated. BTW this is ubuntu only computer (no windows)
also: **home, 'C' drive, windows, program files and steam  folders all show free space is 17.1 gb** (if that even matters)

---

### Post by idoitprone on 2012-06-11
> **userqq said:**
> Hi, I am running steam on wine and TFC plays just fine but when I start TF2 all is well until it starts to load the map and then computer hangs. It begins to load map but wont complete it, my HD is clicking normally (not stuck) and I can move the mouse but it just wont load.
So heres the question: TFC only requires 532 mb of disc space but TF2 requires 10616 mb of disc space and** im wondering if my standard install of wine on ubuntu 12.04 has not allocated enough drive space for this large windows program**. ??
I just ran **df -h** and heres what I got. I am not so good at this so I dont know what this means.

user1@user1-ThinkPad-R52:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        37G   19G   16G  54% /
udev            494M  4.0K  494M   1% /dev
tmpfs           201M  860K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M   80K  501M   1% /run/shm
user1@user1-ThinkPad-R52:~$ 

Help appreciated. BTW this is ubuntu only computer (no windows)

If you have enough space in /home
then it shound not be a problem
wine installs in a hidden director in your home

---

### Post by oldos2er on 2012-06-12
Moved to Wine.

---

