---
title: "Disk space utilization problem"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by kvasanthkumar on 2009-03-22
Hi,

I have ubuntu resized from 51.1 GB to 96 GB. Since I got the partition resized, the disk space utilization 

1. Disk Usage Analyzer shows 
total capacity : 96 GB
used: 32 GB
free: 64 GB

2. File browser shows
59.1 GB free

3. Running "du -h /" shows, 3.9G /
   Running "sudo du -h /" shows 32G /

How can I find which files are occupying that space and get rid of them ?

/proc folder occupies about 5GB, What's the purpose of the /proc folder ?

Would appreciate if someone could help me fix this.

Thanks,
Vasanth

---

### Post by 3Miro on 2009-03-22
> **kvasanthkumar said:**
> Hi,

I have ubuntu resized from 51.1 GB to 96 GB. Since I got the partition resized, the disk space utilization 

1. Disk Usage Analyzer shows 
total capacity : 96 GB
used: 32 GB
free: 64 GB

2. File browser shows
59.1 GB free

3. Running "du -h /" shows, 3.9G /
   Running "sudo du -h /" shows 32G /

How can I find which files are occupying that space and get rid of them ?

/proc folder occupies about 5GB, What's the purpose of the /proc folder ?

Would appreciate if someone could help me fix this.

Thanks,
Vasanth


DO NOT TOUCH /proc or any folder that that is directly in /. You can easily damage your system beyond repair.

On my system sudo du -sh / gives 17G, while df gives used :26302748. I don't know where the discrepancy comes from.

---

### Post by kvasanthkumar on 2009-03-22
Hi,

I ran this command "sudo du -a / | sort -n -r | head -n 20"
and it was my backup file which occupied about 29 GB and i have removed it.

Funniest thing is my /proc folder still shows "37,473 items, totalling 5.0 GB". I really have no idea how this is possible.

---

### Post by prshah on 2009-03-22
> **kvasanthkumar said:**
> 
1. Disk Usage Analyzer shows 
used: 32 GB
free: 64 GB

2. File browser shows
59.1 GB free

3. Running "du -h /" shows, 3.9G /
   Running "sudo du -h /" shows 32G /

/proc folder occupies about 5GB, What's the purpose of the /proc folder ?



About 5% of diskspace is reserved for root's operations: in case the filesystem gets full, it makes sure that critical processes do not stop working, and also ensures that the system admin has working space available to address a diskfull situation.

That is probably the discrepancy that you are seeing.

the "/proc" file system is a dynamic filesystem, and it will not affect diskspace in any way. For example, you will find a file "kcore" in "/proc" that will be huge; The size of kcore will be more or less equal to your RAM size. This is a system representation of your RAM, and does not actually constitute a file on your disk, but is a "device" or virtual file.

In short, you cannot make any changes in "/proc".

running du as a ordinary user will not check a whole bunch of directories, which will be checked when you use "sudo"; and hence the discrepancy there.

As far as I can see, everything is normal. For a clearer picture, try this command```
echo && df -h | head -1 && df -h | grep sda && echo
```

df = diskfree.

---

### Post by Slim Odds on 2009-03-22
> **prshah said:**
> About 5% of diskspace is reserved for root's operations: in case the filesystem gets full, it makes sure that critical processes do not stop working, and also ensures that the system admin has working space available to address a diskfull situation.

And, in my opinion, with the size of most modern disk drives, 5% is way too much.

I usually size mine down to 1% using tune2fs.

---

### Post by kvasanthkumar on 2009-03-22
Hi prshah,

That's informative. Thank you.

---

### Post by 3Miro on 2009-03-22
Good to learn something new. Thanks all!

---

### Post by ahbart on 2009-03-22
Just for your information:
if sda1 is your root (/) partition do:
sudo tune2fs -m 3 /dev/sda1
to bring this reerved space down to 3%

---

### Post by Slim Odds on 2009-03-22
> **ahbart said:**
> Just for your information:
if sda1 is your root (/) partition do:
sudo tune2fs -m 3 /dev/sda1
to bring this reerved space down to 3%

For his 96GB partition that's still almost 3GB reserved (i.e., wasted).

If you keep a Live CD handy, you really don't need any reserved space.

I see people with 5% reserved on a separate huge /home partition. No point in that at all (make it 0%).

---

### Post by kvasanthkumar on 2009-03-23
Slim Odds,

I ran "sudo tune2fs -m 1 /dev/sda5" and did not notice any difference in disk space utilized.

Hope i can install my development tools and proceed further.

---

### Post by Slim Odds on 2009-03-23
> **kvasanthkumar said:**
> Slim Odds,

I ran "sudo tune2fs -m 1 /dev/sda5" and did not notice any difference in disk space utilized.

Hope i can install my development tools and proceed further.

How did you determine this?

What does **sudo tune2fs -l /dev/sda5** show?

---

### Post by kvasanthkumar on 2009-03-23
Sorry, the drive was /dev/sdb5 which was a typing error in previous post.
Below was the output received 

vasanth@vasanth-desktop:~$ sudo tune2fs -l /dev/sdb5
tune2fs 1.41.3 (12-Oct-2008)
Filesystem volume name:   /
Last mounted on:          <not available>
Filesystem UUID:          6312b59d-70b8-4af5-9228-5cf93e48294c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              10502144
Block count:              41985869
Reserved block count:     419858
Free blocks:              40407912
Free inodes:              10348125
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1013
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Tue Mar 10 23:58:03 2009
Last mount time:          Tue Mar 24 07:07:27 2009
Last write time:          Tue Mar 24 07:07:27 2009
Mount count:              3
Maximum mount count:      28
Last checked:             Mon Mar 23 09:47:19 2009
Check interval:           15552000 (6 months)
Next check after:         Sat Sep 19 09:47:19 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1785954
Default directory hash:   half_md4
Directory Hash Seed:      6c174651-c97d-4fbd-bf48-02a26a50e8b8
Journal backup:           inode blocks

---

### Post by Slim Odds on 2009-03-24
Now I understand. Changing the reserved space wouldn't change the **space utilized**, it will change the **space available**.

---

### Post by kvasanthkumar on 2009-03-24
So you mean O.S. will alert me when i have 1% free space only ?

---

### Post by Slim Odds on 2009-03-24
> **kvasanthkumar said:**
> So you mean O.S. will alert me when i have 1% free space only ?

No, it is simply space reserved for the root account. Nobody else can use it.

---

### Post by kvasanthkumar on 2009-03-25
Slim Odds,

Thanks for the info.

---

