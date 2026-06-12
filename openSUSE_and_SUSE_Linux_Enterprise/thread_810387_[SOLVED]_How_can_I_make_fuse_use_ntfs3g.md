---
title: "[SOLVED] How can I make fuse use ntfs3g?"
date: 2008-05-28
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Growbag on 2008-05-28
openSUSE 10.3

Whenever I plug in my external USB hard disk, I can read it, but not write to it.

I have tried uninstalling/reinstalling all the fuse and ntfs3g packages to no avail.

Also the ntfsconfig programme refuses to run.

I can mount the drive manually with:

```
mount.ntfs-3g /dev/sdb1 /media/sdb1
```

...but I would really like it to automount with R/W support.

Oh, here is the output of ***mount -l*** if it helps:

```
/dev/sda3 on / type reiserfs (rw,acl,user_xattr) []
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
debugfs on /sys/kernel/debug type debugfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,mode=0620,gid=5)
/dev/mapper/cr_sda5 on /home type reiserfs (rw,acl,user_xattr) []
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/200 type ntfs (rw,nosuid,nodev,uid=1000,utf8) [200]
```

I can't seem to find any config file for fuse or ntfs3g in /etc/ either.

Thanks in advance :)

---

### Post by quickshade on 2008-05-30
whats the error NTFS-config outputs.

---

### Post by Growbag on 2008-05-31
```
laptop:~> ntfs-config
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 41, in <module>
    from NtfsConfig.NtfsConfig import *
  File "/usr/lib64/python2.5/site-packages/NtfsConfig/NtfsConfig.py", line 23, in <module>
    from xml.sax.saxutils import escape as escape_mkup
ImportError: No module named xml.sax.saxutils
```

Odd eh?

---

### Post by RedDwarf on 2008-05-31
You need to install the python-xml package. It should have been a dependency of ntfs-config, report the problem at [https://bugzilla.novell.com/](https://bugzilla.novell.com/)

---

### Post by Growbag on 2008-06-01
Thanks for the reply reddwarf, I tried to install python-xml, and got an error message (see attached screenshot).

I don't understand what it means though!

---

### Post by RedDwarf on 2008-06-01
Means you use the crappy openSUSE 10.3 libzypp instead of Smart ;-) (Smart also requires python-xml, that's why we already had it when installing ntfs-config).

You don't understand the message because... the message doesn't makes any sense. Probably libzypp thinks that to install python-xml it needs to uninstall python... what is plain stupid. And trying to remove python he finds that python-tk requires it.

So... install the package manually:
> rpm -i "http://download.opensuse.org/update/10.3/rpm/x86_64/python-xml-2.5.1-39.2.x86_64.rpm"

---

### Post by Growbag on 2008-06-01
This is what I get from that command:

```
laptop:/home/rtz # rpm -i "http://download.opensuse.org/update/10.3/rpm/x86_64/python-xml-2.5.1-39.2.x86_64.rpm"
error: Failed dependencies:
        python = 2.5.1 is needed by python-xml-2.5.1-39.2.x86_64
laptop:/home/rtz #
```

Should I use the --force option?

Thanks for your help :)

---

### Post by Growbag on 2008-06-01
Aha, I just searched for "python", and noticed that it is listed in red text.

I'm guessing that means something bad :D.

It says my installed version of python is 2.5.2-2, and the available version is 2.5.1-39.2.

I think I caused this problem (unwittingly) myself because I installed something many months ago from a 3rd party repo, and subsequently removed the repo from my list!

I just set python to be removed and amongst all the (unwanted) gnome stuff, Ultrasol and PysolFC came up as dependants.

I really love my PysolFC version, and don't want to get rid of it :(.

Is it possible to update python do you think?

Thanks for your help :).

---

### Post by Growbag on 2008-06-01
YAY, all fixed and working 100% :D

I removed all the gnome-desktop related stuff, and then PysolFC.

Then set python to "update" (which actually downgraded the version to the official one).

This allowed ntfs-config to function properly.

Then I re-installed PySolFC from Packman and it works perfectly :).

I have no idea why I got that unofficial updated version of python installed!

Anyway, all is good now, many thanks for your help :).

---

### Post by RedDwarf on 2008-06-05
Now makes sense. Still libzypp should have offered to downgrade python and python-tk like a solution (better downgrade than delete python-tk), and it didn't.

Since I have not seen any ntfs-config bug report I have reported it like bug #397577.

---

