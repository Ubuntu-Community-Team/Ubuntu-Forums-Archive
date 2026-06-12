---
title: "Unable to get firewire drive to mount read-write"
date: 2007-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by WMCoolmon on 2007-03-09
I've got a firewire drive that I wanted to do some video conversion with. I need to get the files on the drive, and I've got the files that I'm converting from on the drive as well.

So the fasted way to do this would be to mount the drive as read-write and do the conversion there. Unfortunately the drive refuses to mount as anything but read-only. I've tried manually remounting it with umask set to 000 and iocharset set to utf8. I've also tried sticking that in the fstab and using mount -a (after umounting again, of course).

However every time I try to mount the drive, I keep on getting the error:
mount: block device /dev/sdb1 is write-protected, mounting read-only

The drive is formatted with fat32 and has only ever been used with OS X.

[Here is the drive's page on the CompUSA website](http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200112+404721&Ne=400000&product_code=341179&Pn=E5_320GB_Hard_Drive)

Is there some way to get the drive to mount as read-write?

---

### Post by WMCoolmon on 2007-03-12
Got it working. The solution turned out to be:

```
sudo mount -o remount,rw MOUNTFOLDER
```

---

### Post by dfreer on 2007-03-12
glad you got it working. in the future, you might try pmount as it's default is to mount the drive with rwx permissions for the user who mounted it.

---

### Post by WMCoolmon on 2007-03-13
I'll keep that in mind. Thanks. :)

---

