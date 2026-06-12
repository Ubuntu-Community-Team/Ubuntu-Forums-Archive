---
title: "NTFS Support for 64bit CPU"
date: 2006-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by don_pucci on 2006-08-31
I have just upgraded my pc to a 64bit AMD cpu.  With that, I upgraded to the 64bit version of 6.06 and much to my surprise, I am unable to get ntfs-3g working.

I have read almost every forum thread regarding this topic and it seems that there is no current solution for this problem.

Is that correct?

---

### Post by Kilz on 2006-08-31
> **don_pucci said:**
> I have just upgraded my pc to a 64bit AMD cpu.  With that, I upgraded to the 64bit version of 6.06 and much to my surprise, I am unable to get ntfs-3g working.

I have read almost every forum thread regarding this topic and it seems that there is no current solution for this problem.

Is that correct?

I believe so, but even ntfs-3g is experemental. I dont recommend anyone to use it unless they can afford to lose thge data. There is a warning not to use it on production machines on its website. 
While you cant write to ntfs, you can mount the partition read only.

---

### Post by don_pucci on 2006-08-31
Actually, I do not think you can do either with a 64-bit cpu.

Or at least I have not found a way to read or write.

> **Kilz said:**
> I believe so, but even ntfs-3g is experemental. I dont recommend anyone to use it unless they can afford to lose thge data. There is a warning not to use it on production machines on its website. 
While you cant write to ntfs, you can mount the partition read only.

---

### Post by Kilz on 2006-08-31
> **don_pucci said:**
> Actually, I do not think you can do either with a 64-bit cpu.

Or at least I have not found a way to read or write.

Here is the line from my /etc/fstab file that auto mounts the ntfs partition read only. It can be done.

```
/dev/hda2  /media/hda2  ntfs    defaults,nls=utf8,umask=007,gid=46 0   1
```
You might have to change the /dev/had2 to what it is for your system. Go to System > Adminastration > Disks highlight the disk and look on the partition tab for the info

---

### Post by don_pucci on 2006-08-31
thank you for your help.  that worked.

i will get all the data off that drive then format it accordingly.

regards.

---

### Post by Dirtycash on 2006-09-01
Just for some extra verification I am running 64 bit and I recognize NTFS no problem.

---

### Post by don_pucci on 2006-09-02
yes...that has been established...but READ only....

which is better than nothing i guess.

> **Dirtycash said:**
> Just for some extra verification I am running 64 bit and I recognize NTFS no problem.

---

### Post by prince_niceguy on 2006-09-06
I am using 64 bit and i compiled ntfs-3g from source code with 64 bit. It is working great. I copied around 18GB of files in one shot... took around 43 minutes or so... not bad... my crappy windows 32 bit takes 2 hours to do the same....

---

### Post by Kilz on 2006-09-06
> **prince_niceguy said:**
> I am using 64 bit and i compiled ntfs-3g from source code with 64 bit. It is working great. I copied around 18GB of files in one shot... took around 43 minutes or so... not bad... my crappy windows 32 bit takes 2 hours to do the same....

Thats nice, but as long as its still in beta and the creators recommend not using it on production machines I dont recommend it. It may work fine for you. But if it doesnt, it will take out everything on the drive. I strongly suggest you back up everything.

---

### Post by kuja on 2006-09-06
Another workable solution you might not have thought of is to instead of sharing the ntfs partition, why not share an ext2/3 partition instead? If I remember right you can get that working in windows with drivers from.... I forget where. I'll take a look around.
Perhaps this? [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by cord on 2006-09-06
Let me quote a post I had in another thread. For me ntfs-3g is working.

> 
If you mean ntfs-3g then the answer is yes. Let me see if I can find my the posts.

here:

[http://www.ubuntuforums.org/showpost...&postcount=385](http://www.ubuntuforums.org/showpost...&postcount=385)
[http://www.ubuntuforums.org/showpost...&postcount=381](http://www.ubuntuforums.org/showpost...&postcount=381)

It is working fine on my ubuntu installation.


---

### Post by jbernardo on 2006-09-06
For me, ntfs-fuse works, (but refuses to do a lot of stuff) ntfs-3g seems to stall copying large files. YMMV.

---

