---
title: "Slow file copy"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by soxs on 2009-01-17
After reinstalling ubuntu hardy a couple of times (serious hardwre issues) I got it running almost smooth.
Almost.
File copy is darn slow. I get 2 MiB/s copy speed. This is awfull and doesn't even allow me to watch movies..
I allready removed tracker and evolution to stop fileindexing and generic hd usage, but even then its still as slow as it was before.

Side note: I only see 3.6 GiB of ram out of 4, this wasn't the case in a prior install. There I always saw 3.8/3.9 GiB, but this may be caused having switched to integrated gpu 3200/3300 RadeonHD (using fglrx)

---

### Post by DeMus on 2009-01-17
> **soxs said:**
> After reinstalling ubuntu hardy a couple of times (serious hardwre issues) I got it running almost smooth.
Almost.
File copy is darn slow. I get 2 MiB/s copy speed. This is awfull and doesn't even allow me to watch movies..
I allready removed tracker and evolution to stop fileindexing and generic hd usage, but even then its still as slow as it was before.

Side note: I only see 3.6 GiB of ram out of 4, this wasn't the case in a prior install. There I always saw 3.8/3.9 GiB, but this may be caused having switched to integrated gpu 3200/3300 RadeonHD (using fglrx)

Is this when copying from one Linux partition to another, or from or to an NTFS partiton?

---

### Post by albinootje on 2009-01-17
> **soxs said:**
>  File copy is darn slow. I get 2 MiB/s copy speed. This is awfull and doesn't even allow me to watch movies..

Copying from where to where ?
NFS ? Samba ? FTP ? external disk or stick ? cdrom ? dvd ? local disk ?

---

### Post by soxs on 2009-01-17
from ext3 to ext3[external via USB2.0], from ext3 to ntfs[external via USB2.0], didn't test internal.. will do that soon

---

### Post by albinootje on 2009-01-17
> **soxs said:**
> from ext3 to ext3[external via USB2.0], from ext3 to ntfs[external via USB2.0], didn't test internal.. will do that soon

A few days ago a friend of mine visited me, downloading from usb disk to usb disk was very slow, even though she has a fairly recent laptop.
We didn't have much time, and copied things with a different solution (via the network), but you might want to check your BIOS settings for usb.

And in general for hard disk, check hdparm (and be careful with certain options!) :
[http://www.linuxdevcenter.com/lpt/a/272](http://www.linuxdevcenter.com/lpt/a/272)
[http://en.wikipedia.org/wiki/Hdparm](http://en.wikipedia.org/wiki/Hdparm)

---

### Post by soxs on 2009-01-17
It's a SATAII Drive and a recent motherborad with AMD 780GX chipset

source
```

sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0

```target
```

sudo hdparm /dev/sdb

/dev/sdb:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0

```

Restting and reconfiguring BIOS didn't help at all...

---

### Post by soxs on 2009-01-17
Update: That very same external got 20 MB/s when copying files from my laptop (not my f*** Tower PC) ext3 home to ext3 (usb2.0)

any ideas..


UPDATE: The first 200 to 250 MB get copied with about 20MB/s , then speed drops to under 1MB/s.. this is really odd... and I don't understand it at all..

---

### Post by bikodog on 2009-08-13
I too am having this problem with large file transfers. The speed starts out at approx 20.0 Mbs and trails off to approx 4.0.

1.5 TB ntfs transferring to 1.0 TB ntfs usb 2.0 external. The whole purpose in doing this is because when I originally setup the hard drive partioning scheme I was new to linux and didn't fully understand the benefits of ext3 and was still using windo$ dual boot. I am now making a back up so that I can repartition the internal in ext3 and use ubuntu exclusively. The slow speed is a pain, but I can survive ;)

Any thoughts would be appreciated. Apparently many folks are having this problem.

---

### Post by Djowij on 2009-08-14
I have the exact same problem, Strange thing is that when i copy via mc or command line the speeds are fast. 

I currently copy from ntfs to ntfs for backup purposes. I will retest and post an update after I format to ext3.

---

### Post by Djowij on 2009-08-22
Copying from ext3 to ext3 goes several hundred percent faster then ntfs to ntfs. ntfs from and to ext3 also has good performance. Seems to me the problem only occurs if you copy from ntfs to ntfs.

---

### Post by ecntrk on 2009-09-02
Things are even worse for me.
From qhatever device I copy files, be it from ext4 drive to ext4 drive or dvd/cd/usb flash  to ext4 drive; the best transfer rate i got is 1.03MB/s in my recently bought Dell Inspiron 1545 with Core2Duo and 3GiB Ram.:confused:

I'm giving the hdparm output here :
```

ecntrk@mithai:~$ sudo hdparm /dev/sdb

/dev/sdb:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 1024/0/62, sectors = 0, start = 0
ecntrk@mithai:~$ sudo hdparm /dev/sdc
/dev/sdc: No such file or directory
ecntrk@mithai:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0
ecntrk@mithai:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
ecntrk@mithai:~$ sudo hdparm -t /dev/sda

/dev/sda:

 Timing buffered disk reads:  180 MB in  3.01 seconds =  59.87 MB/sec
ecntrk@mithai:~$ 
ecntrk@mithai:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  190 MB in  3.02 seconds =  62.86 MB/sec
ecntrk@mithai:~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   2004 MB in  2.00 seconds = 1002.18 MB/sec
ecntrk@mithai:~$ 

```

Anything to improve speeds? :(

---

