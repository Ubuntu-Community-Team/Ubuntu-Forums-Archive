---
title: "[SOLVED] Making A Persistent Pendrive Live Distro"
date: 2007-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mark76 on 2007-12-20
Can anyone point me to a how to specifically for Xubuntu and not for any other *buntu?

---

### Post by Mark76 on 2007-12-20
And here's why the instruction set at pendrivelinux.com doesn't work for Xubuntu

> mark@Panopticon:~$ syslinux -sf /dev/sdf1
mark@Panopticon:~$ cd /cdrom
mark@Panopticon:/cdrom$ cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/xubuntu710/
cp: cannot stat `disctree': No such file or directory
cp: cannot create symbolic link `/media/xubuntu710/dists/stable': Operation not permitted
cp: cannot create symbolic link `/media/xubuntu710/dists/unstable': Operation not permitted
cp: cannot stat `ubuntu.ico': No such file or directory
mark@Panopticon:/cdrom$ cd /home/xubuntu
bash: cd: /home/xubuntu: No such file or directory
mark@Panopticon:/cdrom$ wget pendrivelinux.com/downloads/U710fix.zip
--20:17:31--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
           => `U710fix.zip'
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 939 [application/zip]
U710fix.zip: Read-only file system

Cannot write to `U710fix.zip' (Read-only file system).
mark@Panopticon:/cdrom$ unzip -o -d /media/ubuntu710/ U710fix.zip
unzip:  cannot find or open U710fix.zip, U710fix.zip.zip or U710fix.zip.ZIP.
mark@Panopticon:/cdrom$ 


---

### Post by dabl on 2007-12-20
Even though it is Kubuntu, this guy seems to know what he's doing:

[http://kubuntuforums.net/forums/index.php?topic=3089474.0](http://kubuntuforums.net/forums/index.php?topic=3089474.0)

:)

---

### Post by Mark76 on 2007-12-20
I don't get it, I don't get it, I don't get it :(

> grub> root (hd2,0)
root (hd2,0)

Error 21: Selected disk does not exist
grub> 

Why is it NOT hd2,0?  Do I have to go through every possible combination of 2 characters to find the right one?

---

### Post by Mark76 on 2007-12-20
And to top it all I've just found out I'm following instructions for 32 bit machines.

GAH

I'm on a 64.

---

### Post by Mark76 on 2007-12-21
So. Are there any how tos for doing this on 64 bit machines?

---

### Post by Mark76 on 2007-12-23
I did it.

In the end I bit the bullet, installed Ubuntu and then changed it to Xubuntu by removing lots of Gnome packages and following the Psychocats guide to installing XFCE4 and getting back to a pure XFCE.

It's working well so far :)

---

