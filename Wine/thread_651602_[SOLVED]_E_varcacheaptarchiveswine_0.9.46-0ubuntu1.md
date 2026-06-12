---
title: "[SOLVED] E: /var/cache/apt/archives/wine_0.9.46-0ubuntu1_i386.deb: failed in buffer_w"
date: 2007-12-27
forum: Wine
---

### Post by jose158 on 2007-12-27
Ok so I was trying to download wine and I got this message: ```
E: /var/cache/apt/archives/wine_0.9.46-0ubuntu1_i386.deb: failed in buffer_write(fd) (10, ret=-1)

```
Then I ran this code: ```
 sudo dpkg --force-overwrite -i  /var/cache/apt/archives/wine_0.9.46-0ubuntu1_i386.deb

```
And go this: ```
(Reading database ... 84616 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.46-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/wine_0.9.46-0ubuntu1_i386.deb (--install):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/wine/winhelp.exe.so': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine_0.9.46-0ubuntu1_i386.deb

``` any help?

---

### Post by hikaricore on 2007-12-27
> ** failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/wine/winhelp.exe.so': _No space left on device_**

Please post the output of:

```
df -h
```

It looks like you are trying to install WINE on a drive with no free disk space.

---

### Post by jose158 on 2007-12-27
> **hikaricore said:**
> Please post the output of:

```
df -h
```It looks like you are trying to install WINE on a drive with no free disk space.
I got this ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb11            1.9G  1.8G  1.9M 100% /
varrun                887M  212K  886M   1% /var/run
varlock               887M     0  887M   0% /var/lock
udev                  887M   84K  887M   1% /dev
devshm                887M     0  887M   0% /dev/shm
/dev/hdb6             957M   54M  903M   6% /boot
/dev/hdb7             950M   72M  830M   8% /home
/dev/hdb5              24G  8.3G   16G  36% /media/hdb5
/dev/hdb8             942M   24M  871M   3% /tmp
/dev/hdb10            942M  838M   57M  94% /var
fusesmb               1.9G  1.8G  1.9M 100% /home/jose/Network
/dev/hda              424M  424M     0 100% /media/cdrom0
/dev/sda1             974M  452M  522M  47% /media/disk
tmpfs                 887M   34M  853M   4% /lib/modules/2.6.22-14-generic/volatile

```

---

### Post by hikaricore on 2007-12-27
```

Filesystem            Size  Used **Avail **Use% Mounted on
/dev/hdb11            1.9G  1.8G  **1.9M** 100% 

```

Yea, it looks like your root partition, which is 1.9Gb in size is nearly full with only about 2 megs of free space. >.<

---

### Post by jose158 on 2007-12-27
Oh:(. It's ok though. I can fix it.

---

