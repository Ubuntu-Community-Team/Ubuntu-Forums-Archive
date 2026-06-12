---
title: "Which partition for Ubuntu?"
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by outofnicks on 2006-03-03
Just got my Ubuntu CDs in the mail, only took 3 weeks \\:D/ 

I want to give it a try on my &W G3, which currently has 5 major partitions on a WD 120 gb IDE HD:
1. OS X (Jaguar) -- 7 gb
2. OS 9.1 -- 7 gb
3. Apps -- 7 gb
4. Untitled -- 7 gb
5. Documents -- 83 gb

I want to keep Jaguar and OS 9, so can I put Ubuntu on any one of the other partitions? Which of course would be erased and reformatted after transferring the files off.
Ideally, I think I would like to shrink #5 (Documents) and create a 6th partition on that for Ubuntu using parted.

Any possible problems with that plan?

---

### Post by jdp on 2006-03-03
I see no porblems with shrinking 5 and using the new #6 for Ubuntu.  Of course the actual partition number will be much higher, so keep it all straight, but it should work fine.

---

### Post by andrewsawyer on 2006-03-03
I can't see any problems with that no.  Ubuntu gives you the option when installing to shrink a partition to make room for another with Ubuntu in it.  I would make sure that you are fully backed up first though.

---

### Post by 3rdalbum on 2006-03-03
I didn't know you could shrink partitions on Ubuntu PPC, but hey. I don't see a problem with that at all, as long as you make your Ubuntu partition more than 2 gigs. Trust me on this :-)

---

### Post by outofnicks on 2006-03-03
Thanks for the encouraging replies.
To be safe, I'll probably choose one of the small partitions, since I don't have a CD burner or other method to back up the big partition.

3rdalbum, instructions for shrinking a partition to make new space for Ubuntu are here:
[http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960)

---

### Post by outofnicks on 2006-03-03
Well, now I'm not sure how to proceed. If anyone's still with me, couple questions--

I will try installing Ubuntu on partition #4 (untitled 4) and at this point I have it empty, still as HFS+, haven't inserted the install CD yet--still in Jaguar. Do I need to reformat this partition using OS X's Disk Tools first? Or can I go directly to the Ubuntu install?

So, once I've started the install and get to the partitioning, I guess I'll have to choose "Manually edit partition table".

From the Installation/PowerPC wiki page:
> Select a partition to modify or delete it. Remember to assign at least one partition for swap space, to mount a partition on /, and on modern Power Mac systems to create a NewWorld boot partition.

Here is where I'm really not sure what I'll have to do. I want Ubuntu to install on the #4 partition as if it were a complete hard drive. Will that happen? Will the swap space and boot partitions be created either within my chosen partition, somewhere else on the drive, or will I have to set it up manually?

Thanks in advance.

---

### Post by andrewsawyer on 2006-03-03
Ok, partition 4, blank space.

Is this hda4?  not sure if OS X would show it as such.  As there is nothing else on it, it should be pretty easy to pick out in the Ubuntu partition section as the correct one.  You shouldn't have to do anything with it through OS X - Ubuntu should do it all.

You need to allocate double the amount of your ram as a swap partition (so if you have 512Mb ram, have a 1Gb swap partition).  The reast you can allocate as say ext3 and set it to mount as /.

Without going through a reinstall myself I can't give you the exact details of which options to choose - maybe someone else can tell you?

Basically, you should be able to go into the advanced partition/manual partition setup, choose the blank partition.  Delete it, so it is just sitting there as free, unallocated space.  Then make your swap partition (double your ram size), and put it at the end of the blank space - should be given option of end or beginning.

Then make the rest ext3, and set it as /.  Sorry I can't give you line by line code, however it's not something you can just bring up on the screen.  Oh, when you set the swap space, you set it as a normal partition, only when choosing the filesystem type, there will be the option of 'swap'.

I hope this helps!

---

### Post by outofnicks on 2006-03-03
I think you've given me enough to go on, Andrew--thanks!

df in Jaguar's terminal shows my intended partition as /dev/disk0s9 , is that what I should be looking for in the Ubuntu install? I suppose it will be obvious, whatever it's named...

I wouldn't have known to delete the partition during the install, that's very helpful info. Thanks again.

---

### Post by andrewsawyer on 2006-03-03
I'm not sure about the Apple partition details unfortunately.  I am pretty sure though that it shows how much of the space has been used.  As that will be the only one with nothing on it, it should be easy enough to find.

Just make sure you have a decent backup!

---

