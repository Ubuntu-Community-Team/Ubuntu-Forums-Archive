---
title: "Free dynamic RAM Drive with every ubuntu 64bit"
date: 2009-06-08
forum: x86 64-bit Users
---

### Post by DanglingPointer on 2009-06-08
Hi All,

I'm fairly new to ubuntu, and so far I must say I am VERY IMPRESSED!  Ok, so there are obstacles, but it's all got to do with just getting used to the linux way.  I suppose if the tables were turned and we were to learn the M$ Windows way, we would also need to cross a few obstacles to learn the M$ way. :mrgreen:

But now it is time for **[COLOR=DarkOrange]ubuntu[/COLOR]**, and I just realised that **[COLOR=Blue]/dev/shm[/COLOR]** is a partition in RAM!  which grows and shrinks dynamically or gets swapped to disk if an app starts needing all the RAM.  Fantastic!  Hence why this journal is in the 64bit forum.  You need lots of RAM. 

So for all you out there that want to do things in a hurry!  
- Compile thousands of java classes 
- want to use an app which has a LOTof I/O.  
- location for a running log file that you don't want to keep, but matters enough while the computer is still ON.
- perhaps even transcode videos, or any multimedia (however this is more CPU bound than I/O, but it would still negate the effects of disk waits on read and write).
Well, if you have loads of RAM (and RAM is cheap now a days), you can use [COLOR=Blue]**/dev/shm**[/COLOR]  :-\"

From what I have discovered so far.  It will use up to half your RAM, however, if your apps start needing the RAM and their use grows to a value greater than 50% well, whatever is in /dev/shm seems to gets swapped and then you're back to disc speed.

Catch?  =;

Well it is RAM, so it is volitile memory.  Therefore if you loose power or reboot, well whatever is in there is gone!  

So all those with the newest consumer grade mobos with up to 24GB of RAM capability, well stock up with RAM and when you need the speed temporarily, well throw whatever will be I/O'ed into [COLOR=Blue]**/dev/shm.  **[COLOR=Black]You'll see and feel the difference!  Just remember, before turning off your computer to move whatever needs saving back to disc or it is gone.[/COLOR][/COLOR]

---

### Post by reeseslover531 on 2009-06-08
How much of the ram is used by shm?

---

### Post by Eeqmcsq on 2009-06-08
The size of /dev/shm by default is 1/2 your available RAM. Note that available RAM is NOT the same as installed RAM. For example, on my machine at work running Ubuntu-32, I have 1 GiB x 4 sticks installed, Ubuntu sees 3.2 GiB available, so my /dev/shm has a max of 1.6 GiB.

---

### Post by DanglingPointer on 2009-06-08
> **reeseslover531 said:**
> How much of the ram is used by shm?

1/2 by default.  However, if for example you have upgraded in the recent past, let's say the new core i7's with their mobos that can go from 12GB to 24GB; you can use the commands in the following link to change the default size.

Let's say you reckon that your apps will never go more than 4GB and you have 12GB total, well you can set your /dev/shm to 8GB.  
[**http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html**]("http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html")

Case Study 1:
Playing an RPG which has lots of I/O per level/scene/map/whatever.  If it can fit in /dev/shm.  Throw it in there and never worry about load times again.

Case Study 2:
Playing a First Person Shoorter with notoriously long load times per level.  Same thing, thing if it fits ok in /dev/shem, throw it in there and watch it fly!

Case Study 3:
Java project/module with THOUSANDS of .java classes.  If it fits in /dev/shm, well throw it in there.  Just make sure to backup to disc before turning the computer off.  UPS for workstation or desktop would probably be recommended for this scenario.

Case Study 4:
Think outside of the box and use the /dev/shm partition for any kind of app or process you can think of which has some sort of I/O penalty if it were using standard hard drive or even RAID.  Remember, this is MILLIONS of times faster than the best RAID.

Essentially your imagination is the limit with what you can do _*faster*_ in a RAM Drive that comes free off-the-shelf.8-)

---

### Post by reeseslover531 on 2009-06-09
Excellent thank you very much! I will def. take a look at this

---

