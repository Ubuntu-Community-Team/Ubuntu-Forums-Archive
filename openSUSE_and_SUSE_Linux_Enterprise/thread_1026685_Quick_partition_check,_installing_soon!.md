---
title: "Quick partition check, installing soon!"
date: 2008-12-31
forum: openSUSE and SUSE Linux Enterprise
---

### Post by addylad on 2008-12-31
Hi,

Just a quick check to see whether these partitions are OK before I install in a few minutes!  :)

[[img=http://img156.imageshack.us/img156/8622/newpartitionsmt9.th.png]](http://img156.imageshack.us/my.php?image=newpartitionsmt9.png)

So that's:
40GB for Windows XP Home
36GB for openSuSe and its applications
13GB for the /home directory, which can also be read by Windows (formatted to FAT32)
4GB swap

1.  Does that sound OK?
2.  Can I specify that the /home directory will be installed to the 13GB partition later on in the install process?
3.  Does this allow me to upgrade in the future without losing my files?

Thanks a lot!

---

### Post by damis648 on 2008-12-31
FAT for a /home is a BAD idea, sorry. It cannot correctly handle Unix file permissions. Stick with Ext3 and just download a [Windows driver]("http://www.fs-driver.org/").

---

### Post by addylad on 2008-12-31
[[img=http://img181.imageshack.us/img181/6891/screenshotopensuse111gi1.th.png]](http://img181.imageshack.us/my.php?image=screenshotopensuse111gi1.png)

How does that look?

And I will check out that link, thanks a lot.

---

### Post by damis648 on 2008-12-31
That looks good, but make sure to set the mountpoints before you install! :popcorn:

PS. Also, make sure your swap is at lease the size of your RAM.

---

### Post by addylad on 2008-12-31
Is a mountpoint like where everything is going to go?  :confused:

Please explain, as this is my first installation of anything other than Windows.  At the moment, only the Swap partition has a mountpoint, all others have 'Mountpoint:'.

Thanks.

---

### Post by addylad on 2008-12-31
[[img=http://img81.imageshack.us/img81/6048/finalrp4.th.png]](http://img81.imageshack.us/my.php?image=finalrp4.png)

I assume / means 'everything'?  And if I mount one partition as /, and another as /home, does that mean that /home will be created on both, or only one of the partitions?

Thanks a lot, almost there :P

Edit: ignore the 'sdb's in the image, they are a 4GB USB drive (for the screenshots).  :)

---

### Post by damis648 on 2008-12-31
That partition scheme is correct for what you want to do. :popcorn:
> And if I mount one partition as /, and another as /home, does that mean that /home will be created on both, or only one of the partitions?

In linux, / is like C:\. It is the toppedy-top of the directory tree. But unlike Windows, any other volumes are mounted under that, so your /home partition is mounted at, well, /home, instead of D:\ or E:\, etc. If you don't absolutely require a /home partition, you can do away with that and have just simply /home directly on /. (I hope you know what I mean :-P)

---

### Post by addylad on 2008-12-31
> **damis648 said:**
> That partition scheme is correct for what you want to do. :popcorn:


In linux, / is like C:\. It is the toppedy-top of the directory tree. But unlike Windows, any other volumes are mounted under that, so your /home partition is mounted at, well, /home, instead of D:\ or E:\, etc. If you don't absolutely require a /home partition, you can do away with that and have just simply /home directly on /. (I hope you know what I mean :-P)

I think I do.  :P

I'll go for that, thanks a lot!

Edit: if something is not mounted, does that mean nothing will be installed?  I.e. the Windows partition is not mounted, so it cannot be overwritten?

---

