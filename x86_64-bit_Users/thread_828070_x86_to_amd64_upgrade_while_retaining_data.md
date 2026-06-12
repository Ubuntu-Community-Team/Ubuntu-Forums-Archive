---
title: "x86 to amd64 upgrade while retaining data"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by sonicseaweed on 2008-06-13
I know that this question has been asked before, but I wanted to know if anyone had some "easy" steps for upgrading from x86 to amd64 while retaining as much data as possible. I upgraded my hardware but kept my hard drive, so I would like to upgrade my ubuntu installation to take a little more advantage of the new hardware.

---

### Post by Kilz on 2008-06-13
> **sonicseaweed said:**
> I know that this question has been asked before, but I wanted to know if anyone had some "easy" steps for upgrading from x86 to amd64 while retaining as much data as possible. I upgraded my hardware but kept my hard drive, so I would like to upgrade my ubuntu installation to take a little more advantage of the new hardware.

Since you know the question has been asked before, you could have just read the posts and gotten this info.
There is no way of upgrading a 32bit to a 64bit. If you have a separate home partition you can save it and mount it in a 64bit install. If you dont, do a dual boot install, then mount the old 32bit install in a folder, then you can copy over any files you want to save. Then setup the 64bit install and finaly delete the 32bit partition to reclaim hard drive space.

---

### Post by sonicseaweed on 2008-06-13
Thank you I guess.

The point with asking again is that none of the threads I found had a straightforward way of doing this. I don't see a reason for not being able to have a repository way of doing this sort of upgrade. All that is needed is no more complicated than a kernel upgrade (yes, there are more files to upgrade) because the repository uses precompiled packages. 

I guess to summarize for others like me:

1. create a temporary partition and copy all data that you wish to retain to that partition.
2. Download and install the 64-bit version of ubuntu using the partition that your installation was on. (taking care to not let the installation use the partition keeping your precious data)
3. mount the temporary partition and copy your data to your new installation.
4. remove the temporary partition and resize your main partition to reclaim the space.
5. done.

Of course, this process is void if you have more data than free space on your system.

---

### Post by Sef on 2008-06-14
> 1. create a temporary partition and copy all data that you wish to retain to that partition.
2. Download and install the 64-bit version of ubuntu using the partition that your installation was on. (taking care to not let the installation use the partition keeping your precious data)
3. mount the temporary partition and copy your data to your new installation.
4. remove the temporary partition and resize your main partition to reclaim the space.
5. done.

1,3: If you have a home paritition, you need not worry about these two steps.  But still you should **back up** your data.

4) If you resized the main partition where the OS is, then you have to reinstall the OS because by making it bigger, you would have to reformat the partition, thus writing over the OS.

---

### Post by sonicseaweed on 2008-06-14
Those are some very good points.

---

