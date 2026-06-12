---
title: "Mounting drive automatically"
date: 2008-06-06
forum: openSUSE and SUSE Linux Enterprise
---

### Post by sayakb on 2008-06-06
Hello
I dual boot Suse + Hardy
I have a /dev/sda3 mounted as /home in Hardy
Suse does not have a separate home folder. The Suse home is inside / which is /dev/sda4
```
glade@Mean-Machine:~> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             9.5G  3.3G  5.7G  37% /
udev                  499M   84K  499M   1% /dev
/dev/sda3             136G  3.1G  132G   2% /media/Docs
glade@Mean-Machine:~>

```I mounted /dev/sda3 by:
```
sudo mount /dev/sda3 /media/Docs
```I don't seem to be able to add this drive to the /etc/fstab
What should be the fstab line for the /dev/sda3 (ext3 fs)

---

### Post by peitschie on 2008-06-06
Hiya!

The line would be the following in theory:
```

/dev/sda3 /media/Docs ext3 defaults 0 0

```

What do you mean you can't add it to fstab...?

---

### Post by wdaniels on 2008-06-06
Ideally you 'should' use the UUID:

```
sudo vol_id -u /dev/sda3
```

...so in place of /dev/sda3 at the start of the line write UUID=whatever

But it should still work fine with /dev/sda3. What exactly is the problem?

---

### Post by sayakb on 2008-06-06
> **wdaniels said:**
> Ideally you 'should' use the UUID:

```
sudo vol_id -u /dev/sda3
```...so in place of /dev/sda3 at the start of the line write UUID=whatever

But it should still work fine with /dev/sda3. What exactly is the problem?

```

glade@Mean-Machine:~> sudo vol_id -u /dev/sda3
root's password:
sudo: vol_id: command not found
glade@Mean-Machine:~>

```

There's no problem as such. But I just want to mount it automatically without having to mount it manually each time I log in :)
I'm just trying reply #2

---

### Post by sayakb on 2008-06-06
> **peitschie said:**
> What do you mean you can't add it to fstab...?

I meant that whatever I was adding (Was a mixture of malformed UUIDs :)) isn't working for me.
Though this worked (never though this will w/o an UUID! :o)

---

### Post by wdaniels on 2008-06-06
> **LinuxIsInnovation said:**
> sudo: vol_id: command not found

Funny, vol_id is in udev nowadays so it should be there as standard. Try /sbin/vol_id explicitly or alternatively:

```
sudo blkid /dev/sda3
```

...or even...

```
ls -l /dev/disk/by-uuid
```

---

### Post by sayakb on 2008-06-06
```
glade@Mean-Machine:~> ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-06-06 12:55 7b12ac17-ed4d-4025-8a8c-5dbf8509f8eb -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-06 12:55 a3fa2485-80ac-463e-9abf-99c7bb0ce653 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-06 12:55 c9501d24-ae1d-4cae-ad6a-c586c72449c2 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-06-06 12:55 ee2a01d0-31d2-4c8e-b227-07ce28ef6bff -> ../../sda1
glade@Mean-Machine:~> sudo blkid /dev/sda3
sudo: blkid: command not found
glade@Mean-Machine:~>

```

Though the drive seems to be mounting w/o UUID I guess (kinda surprising for Suse)

---

