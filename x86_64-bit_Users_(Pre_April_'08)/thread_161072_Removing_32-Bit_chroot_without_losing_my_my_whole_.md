---
title: "Removing 32-Bit chroot without losing my my whole hdd"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by danrom on 2006-04-16
A while back I installed a 32-bit chroot, I thought I could just delete the chroot folder and all would be well. Erased everything :(.

I would now like to remove chroot again but cannot figure out how. Could some one please assist me?

---

### Post by hollywoodb on 2006-04-16
what command did you use to delete the chroot folder before?

```
sudo rm -rf <path_to_chroot>
```
should work, as long as you aren't in your chroot
also remember to comment or remove the chroot lines from /etc/fstab

---

### Post by danrom on 2006-04-16
I did that last time and that did not go so well.

I just removed a small file from my desktop in the /chroot directory and its no longer on my main Desktop as well. Thanks for your help but thats not going to work.

---

### Post by Yagisan on 2006-04-16
It seems you have done a bind mount of some directories (eg home) inside your chroot, sh when you delete the chroot you deleted the bind mounted directories.

type mount in a terminal, and you will see some entries like this
```
jamie@doomguy:~$ mount
/dev/md1 on / type jfs (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-20-amd64-generic/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext3 (rw)
/dev/md3 on /home type jfs (rw,noatime)
/dev/md0 on /opt type jfs (rw,noatime)
/dev/md2 on /usr type jfs (rw)
/dev/md4 on /var type jfs (rw)
/dev/hda2 on /mnt/windows type ntfs (rw)
tmpfs on /tmp type tmpfs (rw,noatime,size=12g)
/home on /opt/esel_amd64/home type none (rw,bind)
/home on /opt/esel_i386/home type none (rw,bind)
/home on /opt/u606_amd64/home type none (rw,bind)
/home on /opt/u606_i386/home type none (rw,bind)
/home on /opt/base_i386/home type none (rw,bind)
proc on /opt/esel_amd64/proc type proc (rw)
proc on /opt/esel_i386/proc type proc (rw)
proc on /opt/u606_amd64/proc type proc (rw)
proc on /opt/u606_i386/proc type proc (rw)
proc on /opt/base_i386/proc type proc (rw)
/tmp on /opt/esel_amd64/tmp type none (rw,bind)
/tmp on /opt/esel_i386/tmp type none (rw,bind)
/tmp on /opt/u606_amd64/tmp type none (rw,bind)
/tmp on /opt/u606_i386/tmp type none (rw,bind)
/tmp on /opt/base_i386/tmp type none (rw,bind)
/opt on /opt/esel_amd64/opt type none (rw,bind)
/opt on /opt/esel_i386/opt type none (rw,bind)
/opt on /opt/u606_amd64/opt type none (rw,bind)
/opt on /opt/u606_i386/opt type none (rw,bind)
/opt on /opt/base_i386/opt type none (rw,bind)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=jamie)
```
See all the ones with "bind" in them. unmount them like this
```
sudo umount /opt/esel_amd64/tmp
```. When they are all unmounted, you should be able to delete your chroot.

---

### Post by danrom on 2006-04-16
Thanks that seem to work but now theres another problem. My harddrive 'used' harddrive space is still double.

---

### Post by fabertawe on 2006-07-11
> **danrom said:**
> Thanks that seem to work but now theres another problem. My harddrive 'used' harddrive space is still double.

Any chance of an update danrom please? Did you sort this out?

I want to remove chroot also but I haven't found a single thread (other than this) which gives definitive instructions for doing this safely... anyone?!

Cheers ... Paul

---

### Post by dayd on 2006-10-22
**REMOVING CHROOT:**
Im running Debian etch with AMD64 and I installed my chroot per [http://http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292174]("http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292174") AND I just removed that chroot by umounting as Yagisan recommends and then simply deleting the chroot folder and all of its contents. I did not have the problem that danrom had-I can see that I have more space on my hdd as a result of deleting the chroot folder. 

Hope this helps fabertawe.

---

### Post by fabertawe on 2006-10-22
Hi dayd, thanks for posting, it's good that there is feedback on problems when people search :)

I actually re-installed... I was new and impatient and had messed a few things up!

Cheers ... Paul

---

### Post by chrisccoulson on 2006-10-22
The first time I removed a chroot, I ballsed my system up. The second time, after I had learnt my lesson, was fairly easy. I just removed all of the associated bind entries from fstab, then did a sudo mount -a, and checked to make sure that things like /home were not still mounted in /chroot/home, before removing the chroot.

---

### Post by dayd on 2006-10-22
[SIZE="2"]Oh, yes, I almost forgot to mention something: I also deleted the ("chroot") bind entries from fstab,  similar to chrisccoulson's post. Well, at least you know for next time, Paul. Good luck![/SIZE]

[SIZE="1"][i]REMOVING CHROOT:
Im running Debian etch with AMD64 and I installed my chroot per [http://http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292174](http://http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292174) AND I just removed that chroot by umounting as Yagisan recommends and then simply deleting the chroot folder and all of its contents. I did not have the problem that danrom had-I can see that I have more space on my hdd as a result of deleting the chroot folder.

Hope this helps fabertawe.[/I][/SIZE]

---

