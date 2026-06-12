---
title: "Hello here, and my first problem: instalation on iMac G3"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by herb-i on 2005-11-14
Hello Community,
I am new here, with a not good (perhaps bad) english, because i am german.
Excuse Me!!!
Here my problem: I am new in Ubuntu and try to install it on my iMac G3 SE.
On my Mac i have 4 patitions and I want to install Ubuntu on one of them and have the possibility to choose between OSX and Ubuntu at startup. Or is it possible to install Ubuntu on an external harddisk, witch is connected to my iMac over firewire and decide on startup weather to use OSX or Ubuntu?
My main problem is how to partition this one partition for "root" "User" and "swap".

The more detailed your answer the better for me newcomer.

Thanks a lot

herb-i

---

### Post by ssam on 2005-11-14
guten tag

tut mir leid, ich sprecke nur ein bischen deutch.

I think it is possible but difficult to get linux to boot from a firewire disk. I would not recommend it untill you know more about linux.

you do not need to have a seperate partition for usr or home. You just need a root (also called / ) and swap. The swap in not absolutly necessary, but unless you have lots of ram it is very recomended. The swap partition ought to be between 512mb and 1gb.

how big is your hard disk? I think those imacs came with 10 or 20gb. it is fairly easy and cheap to upgrade them to 40, or even 80gb. You might want to user 512mb for swap and split the rest evenly between ubuntu and mac os x.

If you already have mac os x installed, and dont want to reinstall it then you could use the ubuntu installer to delete the other partitions from the disk and make the ones you need.

---

### Post by herb-i on 2005-11-14
hello,

thanks a lot for your quick answer ssam!
Well, for the first I will forget installation on a external firewire-hd. My harddisk has 80 GB, separated in 4 partitions. One partition for my MacOSX, the second and 3. partition for important things witch I don´t want to erase and one free partition with about 10 GB. On this 10GB-partition, in the moment formated in HFS+, I would like to install Ubuntu! I can start with the install-DVD and come to the point for partion. Now Ichoose "manual install" and see my harddisk and the partitions named ....hda7...hda10...etc or something else.  WHAT TO DO NOW?????

Thanks herb-i

---

### Post by ssam on 2005-11-14
hi

if you can make a back up before do this i recomend it.

on a mac there are a bunch of little hidden partitions that are needed hda1 to about hda8, then you'r main partitions.

it is best to identify the partitions by size, your 10 gig one should the highest numbered one, maybe hda11? if you are not sure then it would be best for you to get the live cd, then you can mount the partitions and check whats on what. if you just have one 10gb partition it should be easy to spot.

the partitioner is a little be confusing with its various icons. if you go to the help bit each icon is explained.

partitions can be ignored, mounted at a mount point, or reformated and mounted.

you are probably best ignoring all the mac partitions to start with. you can mount them after you have installed. select each one and set it to do not use (i cant remeber the exact wording).

now you need to delete the 10 gb partition. make sure you get the correct one.

then select the free space and make a new partition. set the size to 512mb, and set the type to swap.

then select the remaining free space, and set it to max size (about 9.5gb). choose ext3 and set the mount point to /

now you should be ready to ok your choices. you will be asked to review the changes it will make to the disk. check that they are right.

the rest of the install is easy compared to that. good luck.

if you are still unsure ask more questions

---

### Post by herb-i on 2005-11-14
Hi SSAM, hi Ubuntu Community,

THANKS!!!!!!!!!!!! for help. This answer is written in UBUNTU-Firefox. Installation was sucsessfull!!! No problems at all!!!

Now I will start to explore Ubuntu/Gnome/.....I´m happy!!!

Best wishes

herb-i

---

### Post by ssam on 2005-11-14
thats excelent news.

have fun

hopefully one day you'll be able to help people move to linux.

---

