---
title: "Disk space error when attempting to install Wavelab on Wine."
date: 2018-11-07
forum: Wine
---

### Post by shag00 on 2018-11-07
[FONT=arial]I had installed a number of programs in Wine and they all worked well until I tried to install wavelab 6. I receive 2 error pop-up messages:
[/FONT][FONT=arial]1/ Insufficient free disk space.
2/ Cannot prepare main package. Probably incorrect TMP/TEMP variables or there is no execute permission for temporary folder.

There is significant available space, $ df returns:
Filesystem      1K-blocks          Used        Available         Use%    Mounted on
/dev/sdc2         3844123664  17652788  3631129872   1%          /

I have checked that the installer .exe is flagged executable.
[/FONT]
After running into this problem the first thing I did was to purge Wine and then re-instal which gave the same results. I then submitted a wine bug report (regression) as I had previously had it installed and running prior to upgrading my system. They responded that they were able to install with no issues. A post on the wine forums yielded no results either. A google search did have some answers but many were almost 10 years old and appeared to relate to a then existing problem.

This is a now a virgin standard Wine install with only mfc42 added which is necessary for the program.

System info:
Dual boot Windows 10 with Kubuntu 18.04
CPU Intel I5 2500K
Nvidia 1080 using Nvidia drivers
Kubuntu is installed on a separate 4TB HDD by itself.
Wine version was initially 3.18 but is now 3.19
The install program can be downloaded from the distributor: [ftp://ftp.steinberg.net/Download/WaveLab_6/6.1.1.353/WaveLab_6.1.1_Update.zip](ftp://ftp.steinberg.net/Download/WaveLab_6/6.1.1.353/WaveLab_6.1.1_Update.zip) 

Can anyone help me with this error please.

---

### Post by TheFu on 2018-11-07
**df -i**   Check the inodes.

Also, **df -Th |egrep -v loop** would be helpful, so we see the entire picture.

---

### Post by shag00 on 2018-11-07
As requested:
```
scott@scottubuntu:~$ df -i 
Filesystem         Inodes  IUsed      IFree IUse% Mounted on
udev              2037180    684    2036496    1% /dev
tmpfs             2045801   1088    2044713    1% /run
/dev/sdc2       244162560 293639  243868921    1% /
tmpfs             2045801     53    2045748    1% /dev/shm
tmpfs             2045801      5    2045796    1% /run/lock
tmpfs             2045801     18    2045783    1% /sys/fs/cgroup
/dev/sdd1      1700630444    617 1700629827    1% /media/data1
/dev/sdb1      1523053412  15587 1523037825    1% /media/data3
/dev/sda2               0      0          0     - /boot/efi
/dev/sde1      3111130176 146273 3110983903    1% /media/data4
tmpfs             2045801     31    2045770    1% /run/user/1000

```
```
scott@scottubuntu:~$ df -Th |egrep -v loop 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  3.0M  1.6G   1% /run
/dev/sdc2      ext4      3.6T   78G  3.4T   3% /
tmpfs          tmpfs     7.9G   59M  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sdd1      fuseblk   1.9T  242G  1.6T  13% /media/data1
/dev/sdb1      fuseblk   1.9T  411G  1.5T  23% /media/data3
/dev/sda2      vfat       96M   31M   66M  32% /boot/efi
/dev/sde1      fuseblk   3.7T  760G  2.9T  21% /media/data4
tmpfs          tmpfs     1.6G   16K  1.6G   1% /run/user/1000

```

---

### Post by TheFu on 2018-11-07
Well, I'm convinced it isn't an out of storage issue.
Have you tried using a new winprefix yet?

---

### Post by shag00 on 2018-11-08
Not only new prefix but new Wine as well.

---

### Post by kg4muc on 2019-02-15
Have you found a solution to installing Wavelab as of yet?  I would like to install my copy as well after I upgrade my HDD to a Solid state drive.

Thanks!

---

