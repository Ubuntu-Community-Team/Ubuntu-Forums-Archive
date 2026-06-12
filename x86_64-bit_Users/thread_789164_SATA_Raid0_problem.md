---
title: "SATA Raid0 problem"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by SyrusTV on 2008-05-10
Bit of a Ubuntu noob so apologies in advance, especially if this is glaringly obvious.

Have everything working, (inc my ATI card, xfi with OSS, network etc) except my raid0 on two drives which I dont want to format - one ntfs partion. 
(yes I know Raid0 is shite; but i was playing around & testing, ended up with files on it, got lazy & left it and ended up chewing up the whole 500GB so losing it, going back to two individual drives is a problem)

I'm NOT looking to boot from this drive, it's purely a file store.

I'm Using Ubunbtu 8.04 (fresh install of amd64, had gutsy and fiesty but never needed my raid0 till now..)

sudo ls /dev/mapper/
($result  ==) control  nvidia_hbedaicd  nvidia_hbedaicd1

sudo dmraid -r
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: nvidia, "nvidia_hbedaicd", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_hbedaicd", stripe, ok, 488397166 sectors, data@ 0

sudo mount -a
-- Gives no result; nothing happens and doesnt mount the drives so I'm presuming I've missed a vital step.

I can find loads of guides on setting up a raid to install ubuntu on and boot from it after formatting, but as to getting a software raid from a ntfs partion after install I'm drawing a blank.

If anyone can point me to a guide (an advanced one is fine) then it would be greatly appreciated.

Thanks,
S.

[edit]Mobo : Asus A8N-Deluxe - and i'm using its controller (nforce)

---

### Post by fjgaude on 2008-05-10
This might work:

```
sudo mount -t ntfs /dev/mapper/nvidia_hbedaicd <mountpoint>
```

May do it. You create your mountpoint first. Come the think of it I don't I know of anyone mounting an ntfs filesystem using dmraid, but who knows.

Let us know how you are doing.

---

### Post by cariboo on 2008-05-10
This what I have in my /etc/fstab

```
/dev/mapper/nvidia_acbgaiad	/home/storage	ext3	defaults	0	2
```

You would have to replace ext3 with ntfs.

Jim

---

### Post by SyrusTV on 2008-05-10
Hi guys;

fjgaude in particular , thank you -- the problem was with me not correctly mounting the drive/s.

But its working now so all is good :D

sudo mount -t ntfs /dev/mapper/nvidia_hbedaicd1 /home/syrus/aaaa

for example correctly mounts the drive/s, now i just need to write a script to do this on boot. But I have access to my data so don't really care atm lol :p

cariboo907 - thanks for your help, it was actually ur input that made me re-visit the problem :)

---

### Post by fjgaude on 2008-05-10
Thanks, now I know it is possible to mount an dmraid that uses ntfs filesystem.

We learn something new daily.

---

