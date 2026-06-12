---
title: "Gigabytes of lost memory after a few hours"
date: 2008-10-11
forum: x86 64-bit Users
---

### Post by pathorn on 2008-10-11
I've started to get in a habit of leaving my computer running overnight.

I have a BOINC client running in the background that allocates and deallocates memory a fair amount. That should be normal and the memory should be usable again.

However I have twice woken up to the sound of my computer swapping.  I figure it is a serious memory leak and kill all the running processes (as well as BOINC).  All the while I am thinking to myself that it's not possible that BOINC has managed eat through the entire 4GB of memory-- it didn't look anywhere near that amount in top.

Anyway so I ran into this issue again today--I have had my computer on for only 10 hours.  So I decided to try and get to the root of the problem.  I killed every process aside from udevd, getty, login and a bash shell to make sure there was nothing weird going on.

free -m:```
             total       used       free     shared    buffers     cached
Mem:          3959       3468        490          0         20        291
-/+ buffers/cache:       3156        802
Swap:         2047         64       1983
```

output of a simple python script that interprets data in /proc/*/smaps:
```
 Private  +   Shared  =  RAM used       Program 

284.0 KiB + 500.0 KiB = 784.0 KiB       getty (3)
180.0 KiB + 612.0 KiB = 792.0 KiB       sleep
376.0 KiB + 544.0 KiB = 920.0 KiB       init
736.0 KiB + 392.0 KiB =   1.1 MiB       sshd
412.0 KiB + 816.0 KiB =   1.2 MiB       top
940.0 KiB + 352.0 KiB =   1.3 MiB       udevd
928.0 KiB + 988.0 KiB =   1.9 MiB       login (3)
  8.8 MiB +   1.4 MiB =  10.3 MiB       bash (3)

 Private  +   Shared  =  RAM used       Program 

 32.6 MiB +   5.5 MiB =  38.2 MiB       TOTALS

```

Yes, 3.1 GB are marked as used (not counting cache) while only 38 MB is actually used.  That's a hundredfold difference!!! 


/proc/meminfo:```
MemTotal:      4054436 kB
MemFree:        509544 kB
Buffers:         20604 kB
Cached:         295856 kB
SwapCached:        120 kB
Active:         168940 kB
Inactive:       160148 kB
SwapTotal:     2097144 kB
SwapFree:      2096872 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:       12544 kB
Mapped:           2504 kB
Slab:          3164496 kB
SReclaimable:  3151048 kB
SUnreclaim:      13448 kB
PageTables:        836 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   4124360 kB
Committed_AS:    16464 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     19192 kB
VmallocChunk: 34359710395 kB
```

The only thing that strikes me as odd is the 3.16GB in "Slab" and the 3.15GB in "SReclaimable".

Even if it is marked as reclaimable, it doesn't seem to be getting reused and instead the system favors swapping out to disk.

Anyone have any idea what is going on?  Is this a problem in the 2.6.24 kernel?  I am intending to test out the Intrepid alpha release anyway so I may try upgrading (or I will test with just the 2.6.27 kernel on Hardy)

---

### Post by pathorn on 2008-10-11
Just occurred to me to check the slabinfo file in /proc.

/proc/slabinfo:
```
# name            <active_objs> <num_objs> <objsize> <objperslab> <pagesperslab> : tunables <limit> <batchcount> <sharedfactor> : slabdata <active_slabs> <num_slabs> <sharedavail>
(cut out entries with less than 1000 active objs, except for one or two that looked relavent.  I have a copy saved on my computer if anyone is interested.)
ext3_inode_cache   11743  11745    768    5    1 : tunables    0    0    0 : slabdata   2349   2349      0
shmem_inode_cache   3238   3290    792    5    1 : tunables    0    0    0 : slabdata    658    658      0
radix_tree_node     5858   5859    560    7    1 : tunables    0    0    0 : slabdata    837    837      0
sysfs_dir_cache    15107  15198     80   51    1 : tunables    0    0    0 : slabdata    298    298      0
inode_cache          357    364    568    7    1 : tunables    0    0    0 : slabdata     52     52      0
dentry            14929475 14929497    208   19    1 : tunables    0    0    0 : slabdata 785763 785763      0
buffer_head        17408  17472    104   39    1 : tunables    0    0    0 : slabdata    448    448      0
vm_area_struct      8234   8234    176   23    1 : tunables    0    0    0 : slabdata    358    358      0
anon_vma            2048   2048     32  128    1 : tunables    0    0    0 : slabdata     16     16      0
numa_policy          680    680     24  170    1 : tunables    0    0    0 : slabdata      4      4      0
kmalloc-2048         762    772   2048    4    2 : tunables    0    0    0 : slabdata    193    193      0
kmalloc-1024        1029   1036   1024    4    1 : tunables    0    0    0 : slabdata    259    259      0
kmalloc-512          677    680    512    8    1 : tunables    0    0    0 : slabdata     85     85      0
kmalloc-256          673    720    256   16    1 : tunables    0    0    0 : slabdata     45     45      0
kmalloc-128          836   1056    128   32    1 : tunables    0    0    0 : slabdata     33     33      0
kmalloc-64          9150  10752     64   64    1 : tunables    0    0    0 : slabdata    168    168      0
kmalloc-32          2551   2816     32  128    1 : tunables    0    0    0 : slabdata     22     22      0
kmalloc-16          4588   5376     16  256    1 : tunables    0    0    0 : slabdata     21     21      0
kmalloc-8           7663   7680      8  512    1 : tunables    0    0    0 : slabdata     15     15      0
kmalloc-192         5944   5985    192   21    1 : tunables    0    0    0 : slabdata    285    285      0
kmalloc-96          1404   1512     96   42    1 : tunables    0    0    0 : slabdata     36     36      0
kmem_cache_node        0      0     56   73    1 : tunables    0    0    0 : slabdata      0      0      0

```

Hmm... wonder what that insanely large (14 Million) "dentry" field is doing...

Given that it says each one accounts for 1 page per slab, and there are 785763 "active slabs" for dentry, and the Linux page size is 4KB, that would account for about 4*785MB=3140MB of my missing memory.


So it looks like dentry's are the culprit.  Now onto understanding what a dentry is and why I have so many loaded into memory and how to solve this.

---

### Post by oldos2er on 2008-10-11
[http://www.cse.unsw.edu.au/~neilb/oss/linux-commentary/vfs-6.html](http://www.cse.unsw.edu.au/~neilb/oss/linux-commentary/vfs-6.html)

---

### Post by jpkotta on 2008-10-11
It's the disk cache.  If free memory was just sitting there, it really would be "lost".  Memory that isn't used is wasted.  So Linux caches blocks from the disk.

---

### Post by pathorn on 2008-10-12
Thanks for that link to the VFS page.  So it looks like these are literally directory entries that are being cached.
I just did a sudo find / | wc -l, and it turns out I have 2368838 files and directories on my entire disk.

@jpkotta, I believe the dentry cache is not the same as cached blocks from disk.  That is what the "Cached" column should correspond to.  Indeed I would prefer if my extra memory was mostly used as a cache for blocks rather than a cache of ghost directory entries.

I can understand if slocate runs and all 2 million of those are cached.  If if you look closely at my original output it says that 14 million dentry's are in the cache.  That's 7 times the total number of files/directories on all partitions of my disk. (Yes, the one I pasted below shows 3.5 million--that is still 2 million too many)

Even if it did make sense to cache 14 million entries, there is a point where it impacts performance.  Swapping out 2GB of legitimate data (if I run other memory-intensive applications as you see below) as well as caching no legitimate data does not make sense to me.  There's clearly something going wrong here.

For example, I have had this machine running for a day now and I now have 2GB swapped out after leaving a few memory-intensive programs open (as well as BOINC).  By memory intensive I mean that they are in total using half my available RAM:
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960       3928         31          0        500         89
-/+ buffers/cache:       3338        621
Swap:         2047       2034         13

$ cat /proc/slabinfo | grep dentry
45:dentry            3587409 3587409    208   19    1 : tunables    0    0    0 : slabdata 188811 188811      0

$ sudo python bin/ps_mem.py  | grep TOTAL
  2.4 GiB +  35.9 MiB =   2.4 GiB    TOTALS

```
So at the moment I pasted this, I  have 3.1 GB of memory in use without including the "buffers"/"cached" sections as well as 2 GB of swap in use, for a grand total of 5 GB of used memory.

However, the amount of memory used by programs is apparently 2.4 GB which is half that, and should leave a generous 1.6 GB of disk cache without swapping at all.

I have rebooted since my original post, and if you notice, in my case, some of the dentry's have indeed been freed.  But a large number are left over and the number continues to go up.

Also, another question I have is why dentry structures not show up in the "Cached" section of /proc/meminfo ?

Here's my meminfo (it's a bit harder to see what is going on here since I now have 2.4GB of legitimate data in use):
```
$ cat /proc/meminfo 
MemTotal:      4055040 kB
MemFree:         21604 kB
Buffers:        581940 kB
Cached:          92192 kB
SwapCached:      38404 kB
Active:        2279420 kB
Inactive:       516160 kB
SwapTotal:     2097144 kB
SwapFree:        11584 kB
Dirty:             868 kB
Writeback:           0 kB
AnonPages:     2092180 kB
Mapped:         218860 kB
Slab:           977392 kB
SReclaimable:   918980 kB
SUnreclaim:      58412 kB
PageTables:      27088 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   4124664 kB
Committed_AS:  4104676 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    314580 kB
VmallocChunk: 34359422971 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:   3968512 kB
DirectMap2M:    225280 kB

```
While it is a good sign that all of those are marked as "SReclaimable", it still is not making a good decision at all about which dentry's to cache and the disk cache to throw away.

I am assuming that BOINC is creating and deleting files hundreds of times per second, and each of those deleted files are being cached.

Anyway, for now I'm just not going to run BOINC, which is a pity since I have a quad core and I wanted to donate cycles.  I just can't afford to do it at the expense of hammering my disk all the time.


Any ideas if there are parameters I can set to tune the disk cache or set a maximum number of dentry's in the cache to a sane number like 100000?

---

### Post by jpkotta on 2008-10-13
Interesting, I learned something new.

I found Documentation/vm/slabinfo.c, and it has a shrink option, but appears to do nothing on my dentry cache.  Also, my dentry is much smaller than yours, probably because the number of files I have is much less (although, not *that* much less).

```
find / -name media -prune -o -name "*" | wc -l # skip nonlocal filesystems
```
```
736093
```

```
./slabinfo -S

```
```
Name                   Objects Objsize    Space Slabs/Part/Cpu  O/S O %Fr %Ef Flg
ext3_inode_cache         80456     760    66.0M     16120/94/2    5 0   0  92 a
proc_inode_cache         73017     592    49.8M      12171/3/2    6 0   0  86 a
dentry                  223064     208    48.0M      11742/9/2   19 0   0  96 a
cifs_inode_cache         69384     624    47.3M      11564/0/2    6 0   0  91 a
radix_tree_node          42950     552    25.5M     6228/502/2    7 0   8  92 
buffer_head             196164     104    21.1M     5175/989/2   39 0  19  96 a
shmem_inode_cache         3631     784     2.9M        728/7/2    5 0   0  95 

```

---

### Post by pathorn on 2008-10-13
I'm now back up to 2.9G in slab allocation.
./slabinfo -S```

Name                   Objects Objsize    Space Slabs/Part/Cpu  O/S O %Fr %Ef Flg
dentry                13849670     208     2.9G     728926/0/4   19 0   0  96 a
:0000040                237240      40    19.3M    4720/4284/4  102 0  90  49 *
ext3_inode_cache          7835     760    13.6M      832/678/4   21 2  81  43 a
radix_tree_node           5776     552    10.4M      632/613/4   29 2  96  30 a
shmem_inode_cache         5990     784     4.9M        296/9/4   20 2   3  95 
vm_area_struct           14386     176     2.6M      653/102/4   23 0  15  94 
task_struct                267    5736     1.9M        56/19/4    5 3  31  77 
(snip)

```

./slabinfo dentry```

Slabcache: dentry                Aliases:  0 Order :  0 Objects: 13758527
** Reclaim accounting active

Sizes (bytes)     Slabs              Debug                Memory
------------------------------------------------------------------------
Object :     208  Total  :  724134   Sanity Checks : Off  Total: 2966052864
SlabObj:     208  Full   :  724130   Redzoning     : Off  Used : 2861773616
SlabSiz:    4096  Partial:       0   Poisoning     : Off  Loss : 104279248
Loss   :       0  CpuSlab:       4   Tracking      : Off  Lalig:       0
Align  :       8  Objects:      19   Tracing       : Off  Lpadd: 104275296

dentry has no kmem_cache operations

dentry: Kernel object allocation
-----------------------------------------------------------------------
No Data

dentry: Kernel object freeing
------------------------------------------------------------------------
No Data

dentry: No NUMA information available.

```

I'm thinking this should maybe be reported as a kernel bug?  Likely BOINC is doing something weird to cause this, but the fact that the cache entries remain there makes me think something is also wrong at the kernel level.

---

### Post by Philk on 2008-10-13
I won't pretend to be an expert here, but I too run BOINC and and have a Core Duo Quad.

You may be using the BOINC 5.* that is available through the standard amd64 resources.  If so, try using the 6.2* you can get (look at the BOINC web page).

While using the 5.* last night (and after the updates yesterday, I noticed my system seemed to be getting much slower in response as the day wore on. This morning I upgraded to the 6.2* version and my system is running much better.  After at least 9 hours of running, my memory is much freer than what you are showing.

Just a possibility.:)

---

### Post by pathorn on 2008-10-21
The problem is with the "aisystem" module for boinc.  It is literally calling access() on seemingly-random filenames (that don't exist) in /var/tmp.] (*,)

Sure enough, I was able to get up to 6 million dentry's by writing a simple for loop generating random strings and calling access on it.


The first solution was to mount /var/tmp as a "tmpfs" partition which it should be by default.  Why isn't this done by default in most distros?
When it's a tmpfs partition the kernel doesn't seem to create dentry cache for it which is good.

Secondly, there is actually a flag in proc to flush the dentry cache.
from [http://www.linuxquestions.org/questions/linux-kernel-70/how-to-disable-filesystem-cache-627012](http://www.linuxquestions.org/questions/linux-kernel-70/how-to-disable-filesystem-cache-627012)
```

sync
echo 2 | sudo tee /proc/sys/vm/drop_caches
... this may take about a minute ...
echo 0 | sudo tee /proc/sys/vm/drop_caches

```

Anyway, I should report this to the aisystem people when I have more time.

---

