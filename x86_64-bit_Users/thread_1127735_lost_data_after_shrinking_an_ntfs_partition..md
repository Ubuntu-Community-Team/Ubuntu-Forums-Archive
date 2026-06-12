---
title: "lost data after shrinking an ntfs partition."
date: 2009-04-16
forum: x86 64-bit Users
---

### Post by ramen. on 2009-04-16
hi, 
i tried to move and shrink an ntfs partition using gparted (on ubuntu 8.04 liveCd) and i (apparently) lost all my data.
that's what happened in this stormy evening

**--- before (few hours ago) ---**
my laptop hd had 4 partitions. 
```
/dev/sda1  10M               (dell useless stuff)
/dev/sda2  10G    HPFS/NTFS  (9G of data)
/dev/sda3  118G   HPFS/NTFS  (MS Vista)
/dev/sda4  ...               (extended partition w/ ubuntu)
```


**--- what i did ---**
i wanted to:
- delete sda1 and sda3.
- move sda2 close to sda4.
- resize sda2 from 10G to 80G.
- format the first part (50G) with NTFS.

i launched ubuntu 8.04 x86_64 liveCd. ran gparted. set up those 4 steps (in the order i wrote). press apply.
gparted worked for less than an hour and finished without errors. 
'everything is all right' - gparted said.
'cool!' - i thought


**--- now ---**
i restart ubuntu (i'm running ubuntu8.10 x86_64 2.6.27-14).
ran fdisk -l.

```
$ sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6431    51656976    7  HPFS/NTFS    
/dev/sda2            6432       16660    82164442+   7  HPFS/NTFS    (data)
...                                                                  (linux stuff)
```

i mount sda2.
BUT.
but instead of my 9G of data i found just 4G of some useless folders like User, Windows, Program Files..  - i guess from my previous MS vista installation on sda3



any idea of what happened? 
i would like to (1) understand what i did wrong and (2) if i could recover my data..

thanks.

ramen

---

### Post by ramen. on 2009-04-18
any help? did i choose the proper place for posting this question?

---

### Post by Yellow Pasque on 2009-04-18
> **ramen. said:**
> any help? did i choose the proper place for posting this question?
There's nothing wrong with posting it in this subfourm, but you probably would have gotten more people to read it in 'General Help'

> (1) understand what i did wrong
The version of gparted you used was probably old. In the future, I'd look at a Linux CD meant explicitly for this purpose (e.g. Parted Magic). Also, you apparently didn't backup data before making major changes to your partition table. The data must not have been that important to you..

---

### Post by drs305 on 2009-04-18
> **ramen. said:**
> i mount sda2.
BUT.
but instead of my 9G of data i found just 4G of some useless folders like User, Windows, Program Files..  - i guess from my previous MS vista installation on sda3



any idea of what happened? 
i would like to (1) understand what i did wrong and (2) if i could recover my data..


Take a look in sda1. As partitions were deleted, sda2 probably ended up as sda1, even though it might not be the first partition on the left.

Before you do any writing to the disk, if you don't find your data you may be able to recover your data with *testdisk*. There are numerous posts on the forum on how to use this app.

---

### Post by lisati on 2009-04-18
Mental note for future: It's always a good idea to (a) make backups, and (b) defrag Windows partitions before tinkering with their size. Things can (and do) sometimes go wrong.

---

### Post by ramen. on 2009-04-19
thanks for your replies.


> The version of gparted you used was probably old.
gpart version was 0.3.5, a bit old..

>  Also, you apparently didn't backup data before making major changes to your partition table. The data must not have been that important to you..

well no, i didn't backup.. my fault.
but anyway i'd like to understand why it happened.. and to recover those if possible. 


> Take a look in sda1. As partitions were deleted, sda2 probably ended up as sda1, even though it might not be the first partition on the left.
i tried to mount sda1, but it seems to be empty..


> Before you do any writing to the disk, if you don't find your data you may be able to recover your data with testdisk...
i've already tried with testdisk, but it has found only some .dll .txt and .mpg fake file..

on which partition you think my data should be right now (if they are still somewhere..), sda1 or sda2?



i'm also trying with gpart, the output doesnt seem to be good.

> $ sudo gpart /dev/sda1 -Efl logGpatr

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


mmmh. any bright idea?

thanks again

ramen

---

### Post by drs305 on 2009-04-19
> **ramen. said:**
> on which partition you think my data should be right now (if they are still somewhere..), sda1 or sda2?


ramen,

I tried duplicating what you did. If you and I both did it in the order you reported it in the original post, running it all in one operation: 

sda2 eventually became sda1, and remained the second partition on the device.

It's a bit confusing, but here is how I think it worked with each of the 4 partitions (3 plus the extended). Zeros used instead of "**-**" to indicate deleted partition for formatting reasons:

1 2 3 [e]  Start
0 2 3 [e]  Delete 1
0 1 2 [e]  Renumber
0 1 0 [e]  Delete 3
0 0 1 [e]  Move old 2 against extended partition.
0 1 1 [e]  Expand old 2 to the left to increase size.
2 1 0 [e]  Create new partition, #1 with empty space on left.

At least that's how it worked on my machine. Probably the same on yours if your sda2 is to the left of sda1.

---

### Post by ramen. on 2009-04-20
thanks drs305 
in that case i would expect that sda1 would have been 80G, but actually sda2 is 80G (as i wanted), and sda1 50 G. am i wrong?

anyway, what do you think i should do?

---

### Post by drs305 on 2009-04-20
> **ramen. said:**
> thanks drs305 
in that case i would expect that sda1 would have been 80G, but actually sda2 is 80G (as i wanted), and sda1 50 G. am i wrong?


You are probably not wrong. The best thing to do at this point is run *testdisk* on the partition without the .dll files and see if your data files are there. I am not enough of an expert on testdisk to know what all its capabilities are but at this point something like testdisk is probably the way to find any files that remain on any of the partitions.

---

### Post by ramen. on 2009-04-21
thanks again, i'll try testdisk again..

---

### Post by ramen. on 2009-04-22
mhm, i run testdisk (v. 6.9 ) and it seems i lost my data.. since i cannot see my data folder anywhere..

that's the deep search output
[*full step sequence is: testdisk > select sda hhd >  Intel > proceed > analyze > quick search > Y (for vista partition) > deeper search *]


> 
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  6430 254 63  103313952
D FAT32 LBA               12   0  1  4189 254 63   67119570 [NO NAME]
D HPFS - NTFS             12  28 17  1317  28  8   20964817 [RECOVERY]
D HPFS - NTFS             12  28 17  1317 134 33   20971520 [RECOVERY]
D HPFS - NTFS           1317 134 34 16659  59 17  246464489 [OS]
D HPFS - NTFS           6431   0  1 16659 254 51  164328873 [RECOVERY]
D HPFS - NTFS          15355   0  1 16659 254 55   20964817 [RECOVERY]
D FAT32 LBA            16660   0  1 30400 254 62  220749164
D FAT32 LBA            16660   1  1 26384 254 63  156232062 [BRIDGE]
D Linux                26385   1  1 29885 254 57   56243496
D Linux                26390  82 61 29891  81 54   56243496
D Linux                26390 180 31 29891 179 24   56243496
D Linux                26392 158  7 29893 156 63   56243496


logfile says (few more details)
> 
..
Results
   D HPFS - NTFS              0   1  1  6430 254 63  103313952
     NTFS, 52 GB / 49 GiB
   D FAT32 LBA               12   0  1  4189 254 63   67119570 [NO NAME]
     FAT32, 34 GB / 32 GiB
   D HPFS - NTFS             12  28 17  1317  28  8   20964817 [RECOVERY]
     NTFS, 10733 MB / 10236 MiB
   D HPFS - NTFS             12  28 17  1317 134 33   20971520 [RECOVERY]
     NTFS found using backup sector!, 10 GB / 10 GiB
   D HPFS - NTFS           1317 134 34 16659  59 17  246464489 [OS]
     NTFS, 126 GB / 117 GiB
   D HPFS - NTFS           6431   0  1 16659 254 51  164328873 [RECOVERY]
     NTFS, 84 GB / 78 GiB
   D HPFS - NTFS          15355   0  1 16659 254 55   20964817 [RECOVERY]
     NTFS, 10733 MB / 10236 MiB
   D FAT32 LBA            16660   0  1 30400 254 62  220749164
     FAT found using backup sector!, 113 GB / 105 GiB
   D FAT32 LBA            16660   1  1 26384 254 63  156232062 [BRIDGE]
     FAT32, 79 GB / 74 GiB
   D Linux                26385   1  1 29885 254 57   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux                26390  82 61 29891  81 54   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux                26390 180 31 29891 179 24   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux                26392 158  7 29893 156 63   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux                26392 223  8 29893 222  1   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux                26394  38 13 29895  37  6   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux                26402  46 13 29903  45  6   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
   D Linux Swap           29886   1  1 30400 254 43    8273392
     SWAP2 version 1, 4235 MB / 4039 MiB
ntfs_device_testdisk_io_ioctl() unimplemented
 


then i've listed every partitions' files - using option P
those are the outputs (from log file)


> 
dir_partition inode=0
FAT32 cluster=2(0x2), pos=209208
   D FAT32 LBA               12   0  1  4189 254 63   67119570 [NO NAME]
     FAT32, 34 GB / 32 GiB
Directory /
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS Volume is dirty.


dir_partition inode=5
   D HPFS - NTFS             12  28 17  1317  28  8   20964817 [RECOVERY]
     NTFS, 10733 MB / 10236 MiB
Directory /
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 .
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 ..
  10910 dr-xr-xr-x     0      0         0 28-Mar-2008 09:16 dell
     35 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Program Files
     88 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 ProgramData
   2648 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 sources
  11021 dr-xr-xr-x     0      0         0 28-Mar-2008 01:20 System Volume Information
  10806 dr-xr-xr-x     0      0         0 28-Mar-2008 08:57 Tools
    108 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Users
    145 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Windows
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS Volume is dirty.


dir_partition inode=5
   D HPFS - NTFS             12  28 17  1317 134 33   20971520 [RECOVERY]
     NTFS found using backup sector!, 10 GB / 10 GiB
Directory /
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 .
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 ..
  10910 dr-xr-xr-x     0      0         0 28-Mar-2008 09:16 dell
     35 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Program Files
     88 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 ProgramData
   2648 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 sources
  11021 dr-xr-xr-x     0      0         0 28-Mar-2008 01:20 System Volume Information
  10806 dr-xr-xr-x     0      0         0 28-Mar-2008 08:57 Tools
    108 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Users
    145 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Windows
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.


dir_partition inode=5
   D HPFS - NTFS           1317 134 34 16659  59 17  246464489 [OS]
     NTFS, 126 GB / 117 GiB
Directory /
      5 dr-xr-xr-x     0      0         0 15-Mar-2009 14:29 .
      5 dr-xr-xr-x     0      0         0 15-Mar-2009 14:29 ..
  36349 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 DELL
   7073 -r--r--r--     0      0        24 28-Mar-2008 08:46 autoexec.bat
     39 dr-xr-xr-x     0      0         0 28-Mar-2008 08:46 Boot
   7076 -r--r--r--     0      0    438840 28-Mar-2008 08:46 bootmgr
   7077 -r--r--r--     0      0        10 18-Sep-2006 23:43 config.sys
  47181 -r--r--r--     0      0      4475 28-Mar-2008 09:16 dell.sdr
  45437 dr-xr-xr-x     0      0         0 25-Apr-2008 13:30 Development
  36790 dr-xr-xr-x     0      0         0 28-Mar-2008 08:58 doctemp
     17 dr-xr-xr-x     0      0         0  6-Jan-2009 18:27 found.000
   9080 dr-xr-xr-x     0      0         0  7-Jan-2009 10:26 found.001
  13969 -r--r--r--     0      0   3747655680 28-Mar-2008 01:25 hiberfil.sys
 157961 -r--r--r--     0      0         0 27-Sep-2008 12:40 IO.SYS
 156642 -r--r--r--     0      0         0 27-Sep-2008 12:40 MSDOS.SYS
  39390 -r--r--r--     0      0   4061384704 17-Dec-2008 17:34 pagefile.sys
     64 dr-xr-xr-x     0      0         0 14-Jul-2008 17:29 Program Files
    280 dr-xr-xr-x     0      0         0 28-Mar-2008 08:46 ProgramData
  40076 dr-xr-xr-x     0      0         0  3-Apr-2008 01:30 Programmi
  51403 dr-xr-xr-x     0      0         0 28-Mar-2008 01:20 System Volume Information
    408 dr-xr-xr-x     0      0         0 28-Mar-2008 08:46 Users
    502 dr-xr-xr-x     0      0         0 22-Jun-2008 12:34 Windows
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS Volume is dirty.


dir_partition inode=5
   D HPFS - NTFS           6431   0  1 16659 254 51  164328873 [RECOVERY]
     NTFS, 84 GB / 78 GiB
Directory /
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 .
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 ..
  10910 dr-xr-xr-x     0      0         0 28-Mar-2008 09:16 dell
     35 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Program Files
     88 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 ProgramData
   2648 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 sources
  11021 dr-xr-xr-x     0      0         0 28-Mar-2008 01:20 System Volume Information
  10806 dr-xr-xr-x     0      0         0 28-Mar-2008 08:57 Tools
    108 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Users
    145 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Windows
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS Volume is dirty.


dir_partition inode=5
   D HPFS - NTFS          15355   0  1 16659 254 55   20964817 [RECOVERY]
     NTFS, 10733 MB / 10236 MiB
Directory /
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 .
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 ..
  10910 dr-xr-xr-x     0      0         0 28-Mar-2008 09:16 dell
     35 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Program Files
     88 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 ProgramData
   2648 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 sources
  11021 dr-xr-xr-x     0      0         0 28-Mar-2008 01:20 System Volume Information
  10806 dr-xr-xr-x     0      0         0 28-Mar-2008 08:57 Tools
    108 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Users
    145 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Windows


dir_partition inode=0
FAT32 cluster=2(0x2), pos=267750668
   D FAT32 LBA            16660   0  1 30400 254 62  220749164
     FAT found using backup sector!, 113 GB / 105 GiB
Directory /
20437076 drwxr-xr-x     0      0   909150861  9-Aug-1959 16:38 ¢ô2’›šw..n
161717141 drwxr-xr-x     0      0   434987121 27-Jan-1988 12:50 Èh*cæë“.ƒŸË
1212328801 -rwxr-xr-x     0      0   2308307784 31-Jan-1981 03:00 >P{Ö.*YT.pŠŽ
504607822 -r-xr-xr-x     0      0   2212370085 12-May-1934 16:39 V$aT==±.ïLY
1113410575 drwxr-xr-x     0      0   2782059505 28-Nov-1908 05:21 ¿=èÄCÛVM.-Lë
18446744072997780422 drwxr-xr-x     0      0   3116129368  9-Nov-2022 23:01 6$N6¬Òî.oœ
559465614 dr-xr-xr-x     0      0   1572720625 15-Dec-1927 16:50 P0H!Ø‚G~.qŸó
18446744071650278428 drwxr-xr-x     0      0   2954399949 29-Dec-1916 12:12 XGÊµX.ši
1666695496 drwxr-xr-x     0      0   3812194536  3-Mar-2023 17:07 ÷¥HP²6].‡ð
790689281 -r-xr-xr-x     0      0   3297900852 25-Mar-2004 00:04 Ú•ÎN³².b•I
18446744072675232222 dr-xr-xr-x     0      0   328480244 15-May-1902 05:37 ×?Ðÿ
18446744073036636315 -r-xr-xr-x     0      0   916636353 12-Nov-1935 17:09 Šª€s:ÁP».”F
18446744072965424346 -rwxr-xr-x     0      0   1870376021 14-Jan-2006 03:15 iZ1Ñ)
636103074 -rwxr-xr-x     0      0   4162706177 14-Jul-1996 22:51 ‡M«dÛ•.'i,
18446744071940037750 dr-xr-xr-x     0      0   776306170 31-Oct-2007 11:04 ÷ýM|¶"¥M.}€®
18446744071924513121 dr-xr-xr-x     0      0   3360594655 24-Jan-2035 10:02 Â–O8–lq.&Š
18446744071821162352 -rwxr-xr-x     0      0   825959239 14-Apr-1991 04:49 ²eÒV`I.…K
1004789586 dr-xr-xr-x     0      0   1012552787 29-Jan-1940 09:21 >€ŸÏµ|Ô.a(%
18446744072532289058 -r-xr-xr-x     0      0   1379436843 14-Mar-1938 05:44 yPoÚê†'f.|åý
18446744073028899981 -rwxr-xr-x     0      0   3877930336  1-May-1983 05:51 e±zO*(ð™.-Ô¬
902374693 dr-xr-xr-x     0      0   721961586 25-Dec-1999 19:31 d:3¬;
….K–
18446744071575523307 drwxr-xr-x     0      0   1643546354  1-Dec-1948 17:28 Jœt:"§J.š„Ù
18446744072137345230 drwxr-xr-x     0      0   2570786855  2-May-2002 00:37 •°Ì8`¿.œsF
1229904461 -rwxr-xr-x     0      0   142968261  9-Jul-2023 07:09 ·YÍu0á.”ðâ
18446744073121258471 -r-xr-xr-x     0      0   1099912926 27-Jun-1998 02:47 HÀQœ/—žI.©ˆ^
18446744073348007409 dr-xr-xr-x     0      0   951816241 12-Feb-1929 07:57 Q~ÂñÞã™.Ë|
1240700248 dr-xr-xr-x     0      0   1794573193 27-Nov-1909 07:02 )Èbª1õ'®.zqZ
782638622 -rwxr-xr-x     0      0   1490840732 12-Dec-1902 05:49 vœé¥d.Á%
1098999730 drwxr-xr-x     0      0   276767913  4-Jul-2028 03:54 âiMJœžã.)Q›
18446744072884044351 -rwxr-xr-x     0      0   3792183738 10-Dec-1926 06:48 .×š{
1745039533 drwxr-xr-x     0      0   717450276 29-Sep-2015 17:55 .Š„É
897468146 dr-xr-xr-x     0      0   641229173  3-Aug-1905 19:36 QŽ2
}.Tw,
16722501 dr-xr-xr-x     0      0   2049292169 18-Nov-1999 21:26 “+Éeee.÷‚


dir_partition inode=0
FAT32 cluster=2(0x2), pos=267662067
   D FAT32 LBA            16660   1  1 26384 254 63  156232062 [BRIDGE]
     FAT32, 79 GB / 74 GiB
Directory /
      7 drwxr-xr-x     0      0         0  6-Aug-2008 02:43 .Trash-1000
 918563 drwxr-xr-x     0      0         0 12-Apr-2009 19:27 mUsiC -
     11 drwxr-xr-x     0      0         0  3-Apr-2009 14:04 photo
1140263 drwxr-xr-x     0      0         0 21-Apr-2009 14:31 not
     10 drwxr-xr-x     0      0         0 15-Mar-2009 22:08 corto
1138165 -rwxr-xr-x     0      0   91970579 13-Apr-2009 13:23 Rumah_Sakit_-_Obscured_By_Clowns.rar
1204109 drwxr-xr-x     0      0         0 12-Apr-2009 19:27 movie
  48155 drwxr-xr-x     0      0         0 29-Mar-2009 23:39 music
1040793 -rwxr-xr-x     0      0   36350597 19-Mar-2009 08:45 Krobak_-_Vorkoma.rar
1071082 drwxr-xr-x     0      0         0  7-Apr-2009 11:16 movie paolo
1041348 -rwxr-xr-x     0      0   33693411 24-Mar-2009 22:43 New_Century_Classic_-_New_Century_Classic.rar
1139728 -rwxr-xr-x     0      0   35023578 18-Apr-2009 12:44 65daysofstatic_-_The_Distant_And_Mechanised_Glow_Of_Eastern_European_Dance_Parties__2008_.rar
      4 drwxr-xr-x     0      0         0 25-Jun-2008 01:52 $RECYCLE.BIN
  67636 drwxr-xr-x     0      0         0  1-Oct-2008 15:09 MYNET
1179654 drwxr-xr-x     0      0         0 19-Mar-2009 19:57 AG&L


dir_partition inode=2
   D Linux                26385   1  1 29885 254 57   56243496
     EXT3 Large file Sparse superblock Recover, 28 GB / 26 GiB
Directory /
      2 drwxr-xr-x     0      0      4096 18-Mar-2009 09:43 .
      2 drwxr-xr-x     0      0      4096 18-Mar-2009 09:43 ..
     11 drwx------     0      0     16384 24-Jun-2008 23:49 lost+found
 450561 drwxr-xr-x     0      0      4096 22-Apr-2008 20:26 var
 229377 drwxr-xr-x     0      0     12288 22-Apr-2009 10:21 etc
 614401 drwxr-xr-x     0      0      4096 22-Apr-2009 10:21 media
  24577 lrwxrwxrwx     0      0        11 24-Jun-2008 23:50 cdrom
 811009 drwxr-xr-x     0      0      4096 16-Apr-2009 23:04 bin
1032193 drwxr-xr-x     0      0      4096 16-Apr-2009 13:45 boot
1646593 drwxr-xr-x     0      0      4096 20-Nov-2008 15:40 dev
1220609 drwxr-xr-x     0      0      4096  9-Apr-2009 10:39 home
  49153 drwxr-xr-x     0      0      4096 22-Apr-2008 20:02 initrd
 745473 drwxr-xr-x     0      0     12288 16-Apr-2009 13:44 lib
  24578 lrwxrwxrwx     0      0         4 24-Jun-2008 23:50 lib64
 434177 drwxr-xr-x     0      0      4096 15-Apr-2008 07:53 mnt
1581057 drwxr-xr-x     0      0      4096 15-Apr-2008 07:53 proc
  16385 drwxr-xr-x     0      0      4096 18-Mar-2009 10:00 root
1327105 drwxr-xr-x     0      0      4096 17-Apr-2009 00:30 sbin
  32769 drwxr-xr-x     0      0      4096 22-Apr-2008 20:02 srv
1458177 drwxr-xr-x     0      0      4096 18-Apr-2008 18:02 sys
1548289 drwxrwxrwt     0      0      4096 22-Apr-2009 11:20 tmp
 622593 drwxr-xr-x     0      0      4096 15-Mar-2009 11:44 usr
   8834 lrwxrwxrwx     0      0        33 18-Mar-2009 09:43 initrd.img
   8838 lrwxrwxrwx     0      0        30 18-Mar-2009 09:43 vmlinuz
  24612 lrwxrwxrwx     0      0        33  5-Mar-2009 11:07 initrd.img.old
  24579 lrwxrwxrwx     0      0        30  5-Mar-2009 11:07 vmlinuz.old
1720321 drwxr-xr-x     0      0      4096 30-Jan-2009 10:14 lib32

...




if i mount sda2, inside i can see 
> 
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 .
      5 dr-xr-xr-x     0      0         0 22-Dec-2008 13:21 ..
  10910 dr-xr-xr-x     0      0         0 28-Mar-2008 09:16 dell
     35 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Program Files
     88 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 ProgramData
   2648 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 sources
  11021 dr-xr-xr-x     0      0         0 28-Mar-2008 01:20 System Volume Information
  10806 dr-xr-xr-x     0      0         0 28-Mar-2008 08:57 Tools
    108 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Users
    145 dr-xr-xr-x     0      0         0 28-Mar-2008 08:56 Windows

that are folders from my previous ms vista partition (original sda3), while i would have like to find data from my original sda2 partition..

---

